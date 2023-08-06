# Spoken StoryCloze Benchmark
This is the official repository of the Spoken StoryCloze benchmark as introduced by Hassid, Michael, et al. 2023 [Textually Pretrained Speech Language Models](https://arxiv.org/pdf/2305.13009.pdf).

## Textual StoryCloze 
The textual [StoryCloze benchmark](https://arxiv.org/pdf/1604.01696v1.pdf) contains 4k five-sentence commonsense stories (split to validation and test sets). For each story, there is an additional negative sample, composed of the first four sentences followed by a negative continuation (ending sentence). The goal is to distinguish the original fifth sentence from the negative one. 

## Spoken Benchmark
To generate the spoken benchmark, we synthesize the stories from the test set using a single-speaker TTS system as provided by Wang, Changhan, et al. [fairseq Sˆ2: A Scalable and Integrable Speech Synthesis Toolkit, EMNLP 2021](https://arxiv.org/pdf/2109.06912.pdf), comprised of a [FastSpeech2.0](https://arxiv.org/pdf/2006.04558.pdf) (Ren et al.,
2020) model and [HiFi-GAN](https://arxiv.org/pdf/2010.05646.pdf) vocoder (Kong et al., 2020).

We release two versions of the Spoken Story Cloze benchmark: 
* Topic Story Cloze (tStoryCloze). 
* Spoken Story Cloze (sStoryCloze). 

For sStoryCLoze, we follow the original StoryCloze negative samples. With this benchmark, researchers can evaluate the models’ capabilities to capture fine-grained causal and temporal commonsense relations.

For tStoryCloze, we randomly sample the negative ending sentence from the dataset. The premise behind tStoryCloze is to evaluate continuation coherence given a spoken prompt. This version is far easier for text-based language models, but quite challenging for speech-based language models. Similar to previous zero-shot speech metrics (e.g., sWUGGY), both speech segments are fed into the SpeechLM, and the probability of each spoken sentence is measured. The percentage of examples where the probability of the positive sample
is higher than the negative ones being reported.

### Download
You can download both benchmarks using the following links: [sStoryCloze](https://drive.google.com/file/d/19ZnkM4vjApCZipd7xQ1ESlOi5oBVrlFL/view?usp=sharing), [tStoryCloze](https://drive.google.com/file/d/17prYkldYb3w3Pyg3Pm77-VnE6nkD5jzG/view?usp=sharing). 

## Evaluation

### tStoryCloze
|     Model     | Reference           | Accuracy |
|:-------------:|---------------------|:--------:|
| LLaMA-7B-text | Hassid, et al. 2023 | 98.3     |
| TWIST-1.3B    | Hassid, et al. 2023 | 61.3     |
| TWIST-7B      | Hassid, et al. 2023 | 64.4     |

### sStoryCloze
TBD


## Citation
If you use this benchmark and find it useful for your research/work, please cite our work using the following bibtex: 
```
@article{hassid2023textually,
  title={Textually Pretrained Speech Language Models},
  author={Hassid, Michael and Remez, Tal and Nguyen, Tu Anh and Gat, Itai and Conneau, Alexis and Kreuk, Felix and Copet, Jade and Defossez, Alexandre and Synnaeve, Gabriel and Dupoux, Emmanuel and others},
  journal={arXiv preprint arXiv:2305.13009},
  year={2023}
}
```
