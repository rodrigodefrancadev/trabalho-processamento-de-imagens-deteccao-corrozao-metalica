# Detector de Corrosão Metálica - Treinamento do Modelo

## Requisitos:

1. Instalar e configurar a biblioteca ultralytics
   - [Anaconda Navigator](https://www.anaconda.com/products/navigator)
   - [Tutorial com Conda](https://docs.ultralytics.com/pt/guides/conda-quickstart/)
2. Criar uma pasta chamada datasets
3. Baixar os datasets e colocar na pasta recem criada. [Link Para Download](https://drive.google.com/file/d/1k790sySefZtWeZeY8Ybr1Vvz6Mklt-jN/view?usp=sharing)

## Sobre os Datasets

Existem 2 datasets no link de download:

- [Rust Detection.v1i.yolov11](https://universe.roboflow.com/rust-detection/rust-detection-38s6e) que contem 10 classes de diferentes tipos de corrosão metálica.
- Rust Detection.v1i.yolov11-monoclass: Este é feito do mesmo dataset acima, porém com todas as classes unificadas em uma só para questões de comparação de desempenho, uma vez que neste trabalho o objetivo é apenas detectar corrosão, mas não classificar.

## Modelos treinados

- runs\detect\train\weights\best.pt
  - Modelo base: yolo11n.pt
  - Dataset: Rust Detection.v1i.yolov11
  - Épocas: 91
  - Obs: o treinamento foi configurado para 100 épocas, mas apenas 91 foram concluídas.
- runs\detect\train2\weights\best.pt
  - Modelo base: yolo11n.pt
  - Dataset: Rust Detection.v1i.yolov11-monoclass
  - Épocas 90
  - Obs: o treinamento foi configurado para 100 épocas, mas apenas 90 foram concluídas.

## Scripts

O projeto contém os seguintes scripts e suas funcionalidades:

### main.py

Contém um menu de 3 opções: 0. Treinar modelo: treina um modelo baseado em yolo11, usando o dataset informado na linha 5.

1. Continuar treinamento: Continua o treinamento de um modelo já treinado anteriormente. Informar o modelo na linha 14.
2. Testar modelo: chama a função test_model do arquivo test_model.py. Esta função usa o modelo indicado em test_model.py:linha 6 para fazer a detecção nas imagens que estao em test_images/input.

### camera.py

abre a webcam para detecção com o modelo e confiança informados nas linhas 4 e 5.
