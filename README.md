# KorQuAD

...

## Create Bundel
```
cl run :KorQuAD_v1.0_dev.json :src "python src/run_squad.py --bert_config_file=src/bert_config.json --vocab_file=src/vocab.txt --init_checkpoint=src/model.ckpt-45000 --do_predict=True --output_dir=output --predict_file src/KorQuAD_v1.0_dev.json --output_file predictions.json" -n run-predictions --request-docker-image tensorflow/tensorflow:1.12.0-gpu-py3 --request-memory 11g --request-gpus 1
```

## Submit 
```
cl make run-predictions/output/predictions.json -n predictions-{MODELNAME}

cl macro korquad-utils/dev-evaluate-v1.0 predictions-{MODELNAME}
```
