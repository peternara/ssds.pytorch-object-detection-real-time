# ssds.pytorch
Repository for Single Shot MultiBox Detector and its variants, implemented with pytorch, python3.

Currently, it contains these features:
- **Multiple SSD Variants**: SSD, RFBNet, RFBNet-lite
- **Multiple Base Network**: VGG, Mobilenet V1/V2
- **Free Image Size**
- **Visualization** with [tensorboard-pytorch](https://github.com/lanpa/tensorboard-pytorch): training loss, eval loss/mAP, example archor boxs.

This repo is depended on the work of [ssd.pytorch](https://github.com/amdegroot/ssd.pytorch), [faster-rcnn.pytorch](https://github.com/jwyang/faster-rcnn.pytorch), [RFBNet](https://github.com/ruinmessi/RFBNet), [Detectron](https://github.com/facebookresearch/Detectron) and [Tensorflow Object Detection API](https://github.com/tensorflow/models/tree/master/research/object_detection). Thanks for there works.

### Table of Contents
- <a href='#installation'>Installation</a>
- <a href='#usage'>Usage</a>
- <a href='#performance'>Performance and Model Zoo</a>
- <a href='#visualization'>Visualization</a>
- <a href='#todo'>Future Work</a>
- <a href='#reference'>Reference</a>

## Installation
1. install [pytorch](http://pytorch.org/)
2. install requirements by `pip install -r ./requirements.txt`

## Usage
To train, test and demo some specific model. Please run the relative file in folder with the model configure file, like:

`python train.py --cfg=./experiments/cfgs/rfb_lite_mobilenetv2_train_voc.yml`

Change the configure file based on the note in [config_parse.py](./lib/utils/config_parse.py)

## Performance
| VOC2007     | SSD                                                                         | RFB                                                                         | FSSD                                                                        |
|-------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| VGG16       | [76.0%](https://drive.google.com/open?id=1TS50uVN-9_WJdyO1ImRAW0HFK11RkVlK) | [80.5%](https://drive.google.com/open?id=1bR79OsJY2cidjcI9L1DbXx2zde5sM2nf) | [77.8%](https://drive.google.com/open?id=1HPotrN0oM0oUQu_o-i_VYRYFlT3PKDrr) |
| MobilenetV1 | N                                                                           | [73.7%](https://drive.google.com/open?id=1DWleN7Rcf92QYVAoeSxUeK7COXD4cuPN) |                                                                             |
| MobilenetV2 |                                                                             | T                                                                           |                                                                             |

| COCO2017    | SSD | RFB                                                                         | FSSD                                                                        |
|-------------|-----|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| VGG16       | T   |                                                                             | [24.5%](https://drive.google.com/open?id=1mxmv2Al5bzdBvNgY3disrZlxd6CSK2yh) |
| MobilenetV1 | T   | [19.1%](https://drive.google.com/open?id=1SexO9XZFpMK2JGmr0mTGqosud-tb2wNe) |                                                                             |
| MobilenetV2 |     | [18.5%](https://drive.google.com/open?id=1uRfoi6iJo8Vd5yYMhzFJ97_l3NLtQhf-) | T                                                                           |


## Visualization

- visualize the network graph (terminal) -tensorboard has bugs.
![graph](./doc/imgs/graph.jpg)

- visualize the loss during the training progress and meanAP during the eval progress (terminal & tensorboard)
![train process](./doc/imgs/train_process.jpg)

- visualize archor box for each feature extractor (tensorboard)
![archor box](./doc/imgs/archor_box.jpg)

- visualize the preprocess steps for training (tensorboard)
![preprocess](./doc/imgs/preprocess.jpg)

- visualize weight (coming soon & any suggestion?)

## TODO
- add DSSDs: DSSD FPN TDM
- test the multi-resolution traning
- add rotation for prerprocess
- test focal loss
- add resnet, xception, inception
- figure out the problem of visualize image in training, visualize graph, and visualize pr curve
- speed up preprocess part (any suggestion?)
- add half precision based on [csarofeen/examples](https://github.com/csarofeen/examples/tree/dist_fp16)
- add network visualization based on [pytorch-cnn-visualizations](https://github.com/utkuozbulak/pytorch-cnn-visualizations)
- [object detection](https://github.com/handong1587/handong1587.github.io/blob/master/_posts/deep_learning/2015-10-09-object-detection.md)

## Reference
