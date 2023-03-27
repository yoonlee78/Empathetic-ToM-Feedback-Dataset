# Empathetic ToM Feedback Dataset (ETF)

- The **Empathetic ToM Feedback Dataset (ETF)** is a dataset designed to train and evaluate empathetic agents using reinforcement learning. It is based on feedback from people and focuses on the Theory of Mind (ToM), which is crucial for social interaction and empathetic understanding. 

- _Theory of Mind (ToM)_ refers to the cognitive ability to understand and attribute mental states, such as beliefs, desires, and intentions, to oneself and others. For example, when someone reaches for an umbrella on a cloudy day, you may infer that they believe it will rain soon. In this dataset, we focus on the expression of 'mentalizing' aspects in written sentences, as this enables people to predict and explain the behavior of others based on their mental states.

## Dataset Background

We used sentences and ToM tags from [covid19-tom-empathy-diary](https://github.com/yoonlee78/covid19-tom-empathy-diary) by Lee et al [1](https://escholarship.org/uc/item/950900w7),[2](https://arxiv.org/abs/2108.11810). 

The original dataset has diary entries (sentences) by crowdworkers in Korea during the early stages of the pandemic about their daily lives. Each sentence in the dataset has been annotated with a ToM level by human experts in psychology. 

The Theory of Mind (ToM) levels range from 0 to 3, where higher levels indicate a greater degree of mentalizing others' minds. These levels represent how a sentence reflects the authors' consideration of other people, from merely mentioning their presence to mentalizing and taking their perspective. 

The main purpose of the dataset is to train and test reinforcement learning agents to make empathetic responses by giving them rewards based on the levels of the Theory of Mind, with a focus on rewarding sentences with a ToM level of 3.

ToM Level Definitions: 

Level 0: Sentences that do not mention other people at all 
Level 1: Sentences that mention other people but do not involve mentalizing others' minds.
Level 2: Sentences that involve mentalizing others' minds but do not necessarily take their perspective (either positively or negatively) or may judge them negatively.
Level 3: Sentences that involve taking the perspective of others, curious about others' thoughts consideration of their thoughts and feelings. Depending on the context, some sentences may not connotate positive, empathetic assumption of others.  

_Note_

- The dataset was collected during the early stages of the pandemic, which influenced the nature of the diary entries.There are many level 2 sentences in the data set that show how people think about others but don't consider their points of view. 
- These usually take the form of criticizing, judging, or forcing one's belief on them (e.g., "he must be a crazy person not to wear a mask in the middle of a pandemic," "is it that hard just to be patient?"). 
- Although, from a psychological standpoint, recognizing the presence and mental states of others is a more complex cognitive process than merely mentioning their physical existence. However, it does not necessarily lead to empathetic understanding or positive outcomes. 
- For this reason, in building a helpful and kind AI agent, we have chosen to refrain from rewarding level 2 sentences, as they do not effectively contribute to the desired goal of fostering empathy and practicality in the agent.

## Usage

The dataset can be used to train and evaluate reinforcement learning agents that aim to generate empathetic responses. By using the dataset as a reward function, agents can learn to generate sentences that exhibit a higher degree of perspective-taking and empathetic thinking, as determined by the ToM levels.

## Dataset Overview

The dataset consists of 5K pairs of sentences collected from emotion diaries from Lee (2021a, 2021b), with each sentence tagged with ToM levels. The ToM levels range from 0 to 3, where higher levels indicate a greater degree of mentalizing others' minds. The objective is to reward agents for generating sentences with ToM level 3 (reward = 1), as these sentences are considered more empathetic and perspective-taking, and the rest are rewarded as 0. 

Each example in the dataset includes:

- `human_ref_A`: A sentence tagged with a ToM level.
- `human_ref_B`: Another sentence tagged with a different ToM level.
- `tom_level_A`: The ToM level tagged with `human_ref_A`.
- `tom_level_B`: The ToM level tagged with `human_ref_B`.
- `reward_A`: A binary reward for `human_ref_A`, where 1 indicates a ToM level 3 and 0 indicates otherwise.
- `reward_B`: A binary reward for `human_ref_B`, where 1 indicates a ToM level 3 and 0 indicates otherwise.
- `labels`: A binary label, where 1 indicates that `human_ref_A` has a ToM level 3, and 0 indicates that `human_ref_B` has a ToM level 3.


## Format

The dataset is provided in JSON format, with one JSON object per line. Each JSON object includes the fields listed above. The file is located at  ``` data ``` folder

Example:

```
{
"human_ref_A": "그나마 휴대폰 때문에 답답함을 잊는 것 같아 그냥 두고 보는데...",
"human_ref_B": "12시 05분, 가방엔 2.4 킬로그램의 노트북, 전원 어댑터, 구형의 전자책 단말...",
"tom_level_A": 3,
"tom_level_B": 0,
"reward_A": 1,
"reward_B": 0,
"labels": 1
}
```

## License

This dataset is released under the Creative Commons Attribution-Non-Commercial 4.0 International (CC BY-NC 4.0) license. However, access to the dataset is granted to researchers who explicitly state that they will use it solely for research purposes. To obtain access, interested researchers must fill out an application form.

Commercial use of the dataset is strictly prohibited. In addition, when using the dataset for publication, researchers may not modify the content of the diary sentences.

Please contact the author for more information on the terms and conditions of using this dataset.

## Citation

If you use the Empathetic ToM Feedback Dataset (ETF) in your research, please cite it using the following format:

Yoon Kyung Lee. (2023). Empathetic ToM Feedback Dataset. Version 1. https://github.com/yoonlee78/Empathetic-ToM-Feedback-Dataset.git

```
#APA style
Yoon Kyung Lee. (2023). Empathetic ToM Feedback Dataset (Version 1) [Dataset].https://github.com/yoonlee78/Empathetic-ToM-Feedback-Dataset.git.

#IEEE style
Yoon Kyung Lee, "Empathetic ToM Feedback Dataset," Version 1, Dataset, 2023. [Online]. Available: https://github.com/yoonlee78/Empathetic-ToM-Feedback-Dataset.git.

#BibTex
@dataset{lee2023empathetictomfeedback,
  title={Empathetic ToM Feedback Dataset},
  author={Yoon Kyung Lee},
  year={2023},
  version={1},
  howpublished={\url{https://github.com/yoonlee78/Empathetic-ToM-Feedback-Dataset.git}},
}
```

## References

There are two publications related to the dataset. Please cite BOTH papers along with the dataset for better interpretation and broader context. For your information, 2021a is the first appearance of the original emotion diary dataset and was mainly targeted at the cognitive science and social science community, while 2021b is specifically targeted at ToM level classification using deep learning models (e.g., BERT).

[1] Lee, Y., Jung, Y., Lee, I., Park, J., & Hahn, S. (2021a). Building a Psychological Ground Truth Dataset with Empathy and Theory-of-Mind During the COVID-19 Pandemic. Proceedings of the Annual Meeting of the Cognitive Science Society, 43. Retrieved from https://escholarship.org/uc/item/950900w7

[2] Lee, Y. K., Lee, I., Park, J. E., Jung, Y., Kim, J., & Hahn, S. (2021b). A Computational Approach to Measure Empathy and Theory-of-Mind from Written Texts. arXiv preprint arXiv:2108.11810. Retreived from :https://arxiv.org/abs/2108.11810,[Dataset](https://github.com/humanfactorspsych/covid19-tom-empathy-diary
)


## Ethics and Disclaimer

The Empathetic ToM Feedback Dataset (ETF) consists of sentences extracted from crowdsourced diaries. All the diary entries were created with the informed consent of the crowdworkers who were aware that their entries would be released to the public for research purposes. While the authors of the original dataset have ensured that the dataset does not contain any personally identifiable information, it is the responsibility of the researchers using this dataset to interpret and handle the data ethically and correctly. The authors shall not be held responsible for any consequences arising from the misuse or misinterpretation of the dataset by others.
