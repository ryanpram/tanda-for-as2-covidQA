# TandA for answer sentence selection on covidQA

The pre-trained Ansq-RoBERTa Large model (transfer model)  provided by [wqa_tanda repo](https://github.com/alexa/wqa_tanda).  The transformers directory and run_glue.py are adaptation and modification from [wqa_tanda repo](https://github.com/alexa/wqa_tanda), the rest is author's code.

## Description
This work is for advanced machine learnine course's final assignment. You can read all detail work's description (in bahasa) at [technical-report](https://github.com/ryanpram/tanda-for-as2-covidQA/tree/main/technical-report)



### Requirement
* Python 3.7
* datasets 1.8.0
* boto3 1.17.97
* sacremoses 0.0.45
* sentencepiece-0.1.95 
* nltk 3.2.5

### Reproduce Step

* Clone This Repo
* Download ASNQ Transfer's Model From [RoBERTa-Large ASNQ](https://wqa-public.s3.amazonaws.com/tanda-aaai-2020/models/tanda_roberta_large_asnq.tar)
* Training Adapt 
```
!python3 run_glue.py \
    --model_type roberta \
    --model_name_or_path  [model-name-or-path] \
    --task_name ASNQ \
    --do_train \
    --do_eval \
    --evaluate_during_training \
    --do_lower_case \
    --data_dir [dataset_dir] \
    --per_gpu_train_batch_size 15 \
    --learning_rate 2e-5 \
    --num_train_epochs 3.0 \
    --output_dir [ouput_dir] \
    --tensorboard_log_dir_loc=[tensor_dir] \
```
* Eval Model's Performance
```
!python3 run_glue.py \
    --model_type roberta \
    --model_name_or_path  [model-name-or-path] \
    --task_name ASNQ \
    --do_test \
    --do_eval \
    --evaluate_during_training \
    --do_lower_case \
    --data_dir [dataset_dir] \
    --per_gpu_train_batch_size 15 \
    --learning_rate 2e-5 \
    --num_train_epochs 3.0 \
    --output_dir [ouput_dir] \
    --tensorboard_log_dir_loc=[tensor_dir] \
```

Note: --do_test is argument for using test data in evaluation process.

### Alternatif reproduce way

In this repo also provided sample notebook ([Example Notebook](https://github.com/ryanpram/tanda-for-as2-covidQA/blob/main/example-notebook/TandA_CovidQA_Repro_Example.ipynb)) to run the program. You can change the parameters as you wish


## Help

You can submit a GitHub issue for asking a question or help. Or you can contact me directly at ryan.pramana@ui.ac.id as well

