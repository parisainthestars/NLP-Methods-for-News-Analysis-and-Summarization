---
language: en
tags:
  - summarization
model-index:
  - name: google/pegasus-xsum
    results:
      - task:
          type: summarization
          name: Summarization
        dataset:
          name: xsum
          type: xsum
          config: default
          split: test
        metrics:
          - name: ROUGE-1
            type: rouge
            value: 46.8623
            verified: true
          - name: ROUGE-2
            type: rouge
            value: 24.4533
            verified: true
          - name: ROUGE-L
            type: rouge
            value: 39.0548
            verified: true
          - name: ROUGE-LSUM
            type: rouge
            value: 39.0994
            verified: true
---

# PEGASUS-XSum

This folder uses the `google/pegasus-xsum` model for abstractive text summarization.

PEGASUS is an encoder-decoder Transformer pretrained with **gap-sentence generation**. During pretraining, important sentences are removed from a document and the model learns to reconstruct them from the remaining text. This objective is closely related to summarization and helps the model generate short representations of longer documents.

The XSum checkpoint is intended for short, direct summaries and is suitable for news articles. In this project, the model is used for inference only; no additional training or fine-tuning is performed.

## Model Results

The Hugging Face model card reports the following verified results on the XSum test set:

| Metric | Score |
|---|---:|
| ROUGE-1 | 46.86 |
| ROUGE-2 | 24.45 |
| ROUGE-L | 39.05 |
| ROUGE-LSUM | 39.10 |

These are the reported results of the pretrained model and were not produced by this project.

## Model Notes

The PEGASUS model family was trained on large text collections such as C4 and HugeNews. Updated checkpoints use mixed training data, varying gap-sentence ratios, and stochastic selection of important sentences.

The model and tokenizer are downloaded automatically through Hugging Face Transformers when they are first used.

## References

- [PEGASUS documentation](https://huggingface.co/docs/transformers/model_doc/pegasus)
- [Original PEGASUS implementation](https://github.com/google-research/pegasus)

```bibtex
@misc{zhang2019pegasus,
    title={PEGASUS: Pre-training with Extracted Gap-sentences for Abstractive Summarization},
    author={Jingqing Zhang and Yao Zhao and Mohammad Saleh and Peter J. Liu},
    year={2019},
    eprint={1912.08777},
    archivePrefix={arXiv},
    primaryClass={cs.CL}
}
