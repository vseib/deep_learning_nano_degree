# 2-7_introduction_to_pytorch

## Quick Start

### Datasets

The datasets will be downloaded automatically when running the scripts.

### Execute one of the provided scripts

This lecture was split into multiple small tasks that each introduced another feature of PyTorch. I summarized most of this steps in one script and included the detailed comments provided by Udacity. This script will train on the MNIST dataset for 1 epoch and display a classification result. To run this script do the following:

```
cd 2-7_intro
python introduction_training.py
```

The next folders contains a simple MLP with 3 layers and a more coplex MLP with 4 layers and dropout. The script will

* train for 10 / 20 epochs, plot the losses, save the model
* load the model, perform 1 inference, display results

Another difference between the two MLPs is that the more complex one is defined inside an own class.
Both MLPs are prepared for the MNIST and the Fashion MNIST datasets.
Additionally, there is a script to evaluate hyperparameters for each MLP and each dataset.

To use the simple version type:

```
cd 2-7_simple_mlp
```

And for the more complex one:

```
cd 2-7_new_mlp
```

Then choose one of the scripts:

```
python mnist_mlp.py
```

or

```
python fmnist_mlp.py
```

To test different hyperparameters either run

```
python mnist_mlp_optimizer_eval.py
```

or

```
python fmnist_mlp_optimizer_eval.py
```

## Description

The evaluation script compares the SGD and the Adam optimizer with different learning rates for a training of 20 epochs. In the following I summarize the resulst. The complete output is also provided in the corresponding folders.

### Simple MLP for MNIST

The following are the 3 best results with SGD:

---

Optimizer: SGD learning rate: 0.1
Epoch: 20/20	 Train Loss: 0.0145	 Test Loss: 0.0747	 Accuracy: **0.9803**

Optimizer: SGD learning rate: 0.05
Epoch: 20/20	 Train Loss: 0.0234	 Test Loss: 0.0796	 Accuracy: 0.9771

Optimizer: SGD learning rate: 0.01
Epoch: 20/20	 Train Loss: 0.0967	 Test Loss: 0.1084	 Accuracy: 0.9668

---

The other learning rates were too low to achieve good results after 20 epochs.

Now the 3 best results for the Adam optimizer:

---

Optimizer: Adam learning rate: 0.001
Epoch: 20/20	 Train Loss: 0.0280	 Test Loss: 0.0968	 Accuracy: **0.9776**

Optimizer: Adam learning rate: 0.0005
Epoch: 20/20	 Train Loss: 0.0254	 Test Loss: 0.0904	 Accuracy: 0.9744

Optimizer: Adam learning rate: 0.0001
Epoch: 20/20	 Train Loss: 0.0812	 Test Loss: 0.0985	 Accuracy: 0.9704

---

The results for Adam are more constant, however, slightly below the best result with SGD.


### Simple MLP for Fashion MNIST

The following are the 3 best results with SGD:

---

Optimizer: SGD learning rate: 0.1
Epoch: 20/20	 Train Loss: 0.1894	 Test Loss: 0.3603	 Accuracy: 0.8771

Optimizer: SGD learning rate: 0.05
Epoch: 20/20	 Train Loss: 0.2079	 Test Loss: 0.3187	 Accuracy: **0.8886**

Optimizer: SGD learning rate: 0.01
Epoch: 20/20	 Train Loss: 0.3051	 Test Loss: 0.3672	 Accuracy: 0.8678

---

Now the 3 best results for the Adam optimizer:

---

Optimizer: Adam learning rate: 0.001
Epoch: 20/20	 Train Loss: 0.1699	 Test Loss: 0.3757	 Accuracy: **0.8843**

Optimizer: Adam learning rate: 0.0005
Epoch: 20/20	 Train Loss: 0.1829	 Test Loss: 0.3528	 Accuracy: 0.8808

Optimizer: Adam learning rate: 0.0001
Epoch: 20/20	 Train Loss: 0.2832	 Test Loss: 0.3505	 Accuracy: 0.8739

---

We notice that Fashion MNIST is much more complex than MNIST as the results are about 10 percent points below the previous results. Once again SGD is by a tiny margin better than Adam, whereas Adam has more consitent results.

### New MLP for MNIST

Now the hope is to further improve the results by using 1 more layer and dropout to avoid overfitting.

The following are the 3 best results with SGD:

---

Optimizer: SGD learning rate: 0.1
Epoch: 20/20	 Train Loss: 0.0316	 Test Loss: 0.0629	 Accuracy: **0.9821**

Optimizer: SGD learning rate: 0.05
Epoch: 20/20	 Train Loss: 0.0306	 Test Loss: 0.0732	 Accuracy: 0.9788

Optimizer: SGD learning rate: 0.01
Epoch: 20/20	 Train Loss: 0.0809	 Test Loss: 0.0778	 Accuracy: 0.9755

---

Now the 3 best results for the Adam optimizer:

---

Optimizer: Adam learning rate: 0.0005
Epoch: 20/20	 Train Loss: 0.0480	 Test Loss: 0.0571	 Accuracy: **0.9835**

Optimizer: Adam learning rate: 0.0001
Epoch: 20/20	 Train Loss: 0.0297	 Test Loss: 0.0639	 Accuracy: 0.9821

Optimizer: Adam learning rate: 5e-05
Epoch: 20/20	 Train Loss: 0.0387	 Test Loss: 0.0614	 Accuracy: 0.9816

--- 

First notice that for SGD its the same learning rates that lead to best results, while for Adam there was a small change.
Second, there is a small improvement in all cases and now Adam is clearly better than SGD.

Here is the plot for the best result (Adam with lr=0.0005):

![alt text](2-7_new_mlp/mnist_plots_Adam_0.0005.png "MNIST plot")

### New MLP for Fashion MNIST

Now lets see if there is also an improvement for Fashion MNIST.

The following are the 3 best results with SGD:

---

Optimizer: SGD learning rate: 0.1
Epoch: 20/20	 Train Loss: 0.2108	 Test Loss: 0.3357	 Accuracy: **0.8868**

Optimizer: SGD learning rate: 0.05
Epoch: 20/20	 Train Loss: 0.2208	 Test Loss: 0.3418	 Accuracy: 0.8815

Optimizer: SGD learning rate: 0.01
Epoch: 20/20	 Train Loss: 0.3029	 Test Loss: 0.3410	 Accuracy: 0.8781

---

Now the 3 best results for the Adam optimizer:

---

Optimizer: Adam learning rate: 0.0005
Epoch: 20/20	 Train Loss: 0.2072	 Test Loss: 0.3180	 Accuracy: 0.8951

Optimizer: Adam learning rate: 0.0001
Epoch: 20/20	 Train Loss: 0.1942	 Test Loss: 0.3141	 Accuracy: **0.8953**

Optimizer: Adam learning rate: 5e-05
Epoch: 20/20	 Train Loss: 0.2254	 Test Loss: 0.3051	 Accuracy: 0.8949

---

Again, we notice that for SGD its the same learning rates that lead to best results, while for Adam there was a small change.
Second, there is a small improvement in most cases, especially for Adam, that is now clearly better than SGD.

Here is the plot for the best result (Adam with lr=0.0001):

![alt text](2-7_new_mlp/fmnist_plots_Adam_0.0001.png "Fashion MNIST plot")

The plot looks as if the network is not done training. With a longer training better results might be possible.

