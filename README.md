# Co-authorship Prediction

```
$ pip install -r requirements.txt
``` 

### Train Embedding

```

Note:
  'embedding.pth' and 'log.txt' are saved under ./backup/.../ directory.
  The argument parser of this script is automatically generated by
  docopt package using this help message itself.
  
Usage:
  train_embedding.py symmetric [options]
  train_embedding.py skipgram  [options]
  train_embedding.py (-h | --help)
  
Options:
  -d --dim <int>            Embedding dimension [default: 256]
  --max-context <int>       Maximum context length                 [default: 3]
  --neg-sample-factor <int>   Number of negative samples per context [default: 20]
  -b --batch <int>          Batch size          [default: 100]
  --lr <float>              Learning rate       [default: 1e-2]
  -e --epochs <int>         Epochs              [default: 1000]
  -s --seed <int>           Random seed [default: 0]
  --device <int>            Cuda device [default: 0]
  --num-workers <int>       Number of processors [default: 4]
  --file <str>              Path to input file [default: data/paper_author.txt]
  --backup-interval <int>   Interval of model backup [default: 100]
  --dirname <str>           Directory name to save trained files
  -h --help                 Show this screen.

```

### Train Classifier
  ```
Note:
  'classifier.pth' and 'log.txt' are saved under ./backup/.../ directory.
  The argument parser of this script is automatically generated by
  docopt package using this help message itself.
  
Usage:
  train_classifier.py (--embedding <str>) (--lstm | --deepset) [options]
  train_classifier.py (-h | --help)
  
Options:
  --embedding <str>     Path for embedding.pth (required)
  --no-train-embedding  When set, re-train embedding
  --handle-foreign      When set, make all foreign authors to have the same idx. If there are more than one foreign authors, only one idx remains.
  --lstm                When set, use bidirectional LSTM aggregator
  --deepset             When set, use DeepSet aggregator
  --hidden <int>        Hidden size         [default: 256]
  --dropout <float>     Dropout rate        [default: 0.5]
  --enable-all-pools    (DeepSet only option) enable all poolings
  -b --batch <int>      Batch size          [default: 100]
  --emb-lr <float>      Learning rate for embedding network [default: 1e-3]
  --lr <float>          Learning rate       [default: 1e-3]
  --weight-decay <float>    Weight Decay    [default: 1e-4]
  -e --epochs <int>     Epochs              [default: 10]
  --ratio <float>       Train validation split ratio    [default: 0.8]
  --use-paper-author    Use paper_author.txt in addition to query_public.txt
  --oversample-false-collabs    Oversample false collabs. Only effective when used with --use-paper-author.
  --threshold <float>   threshold           [default: 0.5]
  -s --seed <int>       Random seed         [default: 0]
  --dirname <str>       Directory name to save trained files [default: None]
  --device <int>        Cuda device         [default: 0]
  -h --help             Show this screen

  ```
  
