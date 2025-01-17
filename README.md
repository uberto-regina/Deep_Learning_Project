# README
This is the README for the code of the project "Advancing Continual Learning through Modular Architectures: Leveraging Convolutional Backbones for Adaptability and Flexibility" by Uberto Regina, Federico Deotto and Lucas Tavier for the Deep Learning 2024-2025 ETHZ Course.

In this README, we explain the folder that was submitted and how to run the notebooks.

## Folder Structure

In the folder submitted, there is this README and another folder called `Models` where all our experiments are stored. 

We have divided the experiments into two categories: those concerning CIFAR10 and those concerning CIFAR100. Inside `Models`, there are two dataset folders:

- `CIFAR10`
- `CIFAR100`

Within each dataset folder, we have the same models, which are as follows:

1. **MTSimpleCNN**: This is the base model `MTSimpleCNN()` from Avalanche.
2. **ResNetCNN**: This model consists of ResNet as a backbone and then a variant of the `MTSimpleCNN()` which we called `MTCustomCNN()`.
3. **EfficientNetCNN**: Similar to `ResNetCNN`, but using EfficientNetB0 as a backbone.
4. **PCNN**: This is our variant of the Progressive Convolutional Neural Network cited in our paper (we have removed lateral connections and included fewer layers than in the original).
5. **ResNetPCNN**: This model consists of ResNet as a backbone and then another variant of the PCNN (not exactly the one above; the channels were modified to accommodate the output of ResNet).
6. **EfficientNetPCNN**: Similar to `ResNetPCNN`, but using EfficientNetB0 as a backbone.

Each model is a Jupyter notebook with the same structure. The only packages required are `Avalanche`, `Torch`, and `Torchvision`.

## Running the Notebooks

### For CIFAR10

You can run each notebook in the following way:

1. **First Cell**: Import the required libraries.
2. **Second Cell (Optional)**: Activated only when `SAVE == True`. Used for saving outputs (probably not needed).
3. **Third Cell**: Define hyperparameters and the device.
4. **Fourth Cell**: Define the model (not needed for `MTSimpleCNN` as it is already in the Avalanche library).
5. **Fifth Cell**: Define the benchmark (dataset and its split using Avalanche API) and evaluation metrics (corresponding to "evaluation plugin").
6. **Sixth Cell**: Define the strategy (model, loss function, optimizer, and other hyperparameters).
7. **Seventh Cell**: Train and evaluate the model.
8. **Eighth Cell (Optional)**: For saving outputs, similar to the second cell.

### For CIFAR100

The steps are similar to CIFAR10, with the following differences:

1. **First Cell**: Import the required libraries.
2. **Second Cell (Optional)**: Activated only when `SAVE == True`. Used for saving outputs (probably not needed).
3. **Third Cell**: Define hyperparameters.  
   - Two experiments are performed on CIFAR100:
     - Using `SETTING = '0'`: Reproduces the setting with 50 experiences (2 classes per experience) and 10 tasks.
     - Using `SETTING = '1'`: Reproduces the setting with 10 experiences (10 classes per experience) and 5 tasks.
4. **Fourth Cell**: Define the model (not needed for `MTSimpleCNN` as it is already in the Avalanche library).
5. **Fifth Cell**: Class order for the training task (as we are not evaluating on the entire dataset).
6. **Sixth Cell**: Define the benchmark (dataset and its split using Avalanche API) and evaluation metrics (corresponding to "evaluation plugin").
7. **Seventh Cell**: Define the strategy (model, loss function, optimizer, and other hyperparameters).
8. **Eighth Cell**: Train and evaluate the model.
9. **Ninth Cell (Optional)**: For saving outputs, similar to the second cell.


At the end of the process, after the data was already collected, all files were rerun to verify everything was correct. The execution was manually stopped a few seconds later, which is why a `KeyboardInterrupt` appears for all the training cells
