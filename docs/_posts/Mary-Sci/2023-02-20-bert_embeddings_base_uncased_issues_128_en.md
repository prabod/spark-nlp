---
layout: model
title: English Bert Embeddings Cased model (from antoinev17)
author: John Snow Labs
name: bert_embeddings_base_uncased_issues_128
date: 2023-02-20
tags: [open_source, bert, bert_embeddings, bertformaskedlm, en, tensorflow]
task: Embeddings
language: en
edition: Spark NLP 4.3.0
spark_version: 3.0
supported: true
engine: tensorflow
annotator: BertEmbeddings
article_header:
type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BertEmbeddings model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `bert-base-uncased-issues-128` is a English model originally trained by `antoinev17
`.

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/bert_embeddings_base_uncased_issues_128_en_4.3.0_3.0_1676927301180.zip){:.button.button-orange}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/bert_embeddings_base_uncased_issues_128_en_4.3.0_3.0_1676927301180.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}

```python
documentAssembler = DocumentAssembler() \
    .setInputCols(["text"]) \
    .setOutputCols("document")

tokenizer = Tokenizer() \
    .setInputCols("document") \
    .setOutputCol("token")

embeddings = BertEmbeddings.pretrained("bert_embeddings_base_uncased_issues_128","ko") \
    .setInputCols(["document", "token"]) \
    .setOutputCol("embeddings") \
    .setCaseSensitive(True)
    
pipeline = Pipeline(stages=[documentAssembler, tokenizer, embeddings])

data = spark.createDataFrame([["I love Spark NLP"]]).toDF("text")

result = pipeline.fit(data).transform(data)
```
```scala
val documentAssembler = new DocumentAssembler() 
    .setInputCols(Array("text")) 
    .setOutputCols(Array("document"))
      
val tokenizer = new Tokenizer()
    .setInputCols("document")
    .setOutputCol("token")
 
val embeddings = BertEmbeddings.pretrained("bert_embeddings_base_uncased_issues_128","ko") 
    .setInputCols(Array("document", "token"))
    .setOutputCol("embeddings")
    .setCaseSensitive(True)    
   
val pipeline = new Pipeline().setStages(Array(documentAssembler, tokenizer, embeddings))

val data = Seq("I love Spark NLP").toDS.toDF("text")

val result = pipeline.fit(data).transform(data)
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|bert_embeddings_base_uncased_issues_128|
|Compatibility:|Spark NLP 4.3.0+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[sentence, token]|
|Output Labels:|[bert]|
|Language:|en|
|Size:|410.1 MB|
|Case sensitive:|true|

## References

https://huggingface.co/antoinev17/bert-base-uncased-issues-128
