# AIDI-1002_Final_Project
Final Project for Machine Learning Programming Course (AIDI 1002).

Here is the link to the original github link for this paper: https://github.com/iikka-v/ML-NDT

This project implements some upgrades and improvements over the original code. Here are the detailed report of upgrades and improvements that were added:
- Enhanced Model Architecture:
  - The addition of BatchNormalization layers after each Conv2D layer. This helps in reducing internal covariate shift, potentially leading to faster training and better generalization.
  - Increasing the number of filters in Conv2D layers (e.g., 128, 96, 64, 48 instead of 96, 64, 48, 32) allows the model to learn more complex features.
  - Changing activation functions from 'relu' to 'elu' (Exponential Linear Unit) can help mitigate the "dying ReLU" problem and potentially improve learning dynamics.
  - The addition of a Dropout layer before the final Dense layer is a form of regularization that can help prevent overfitting.
 
- Improved Training Efficiency:
  - The implementation of mixed precision training. This allows for faster computation and reduced memory usage on compatible GPUs, potentially enabling training on larger datasets or more complex models.
  - The refactored data generator that yields batches directly is more memory-efficient, allowing for training on larger datasets that might not fit entirely in memory.

- Better GPU Utilization:
  - The addition of GPU detection and utilization code makes the model more adaptable to different hardware setups, potentially speeding up training on GPU-enabled systems.

- Enhanced Visualization and Debugging:
  - The modified DebugCallback now saves plots as image files after each epoch, providing a visual history of the model's performance throughout training. This allows for better analysis of the model's learning progress.

- Improved Hyperparameter Tuning:
  - The increase in learning rate from 0.0001 to 0.0005 is an example of hyperparameter tuning, which can lead to faster convergence if appropriately chosen.

These improvements collectively contribute to the methodology by:
  - Potentially improving the model's performance through architectural enhancements and regularization techniques.
  - Enabling training on larger datasets or more complex models through improved memory efficiency and GPU utilization.
  - Providing better tools for model analysis and debugging through enhanced visualization capabilities.
  - Demonstrating the effects of hyperparameter tuning on the model's training process.

Items of exitsing directories:
  - /src : contains source codes
  - /data : contains dataset
  - /data/debug_plots : contains graphs ran on dataset for each epochs
  - /data/modelcpnt5ba5d242-aaac-43cc-8593-e6f1d462faa8.keras : model_checkpoint file that was generated by us
  - /data/train.py : original training python file from the author
  - /data/AIDI_1002_Final_Project.ipynb : contains upgraded and improved trian.py code
    
To run this code:
  - Clone the github repository.
  - Install the following dependencies by doing "pip install -r requirements.txt"
    - Please note you will need the exact same version of dependencies for hassle free code run.
  - Once the dependecies are done,
    - If you want to run the existing created model checkpoint file:
      - simply run "python inference.py modelcpnt5ba5d242-aaac-43cc-8593-e6f1d462faa8.keras ../data/validation/FA4DC2D8-C0D9-4ECB-A319-70F156E3AF31.bins"
      - please ensure you have provided the path accurately (this depends on where you are running the code from, but as long as you are running it from inside src directory, you should be fine)
    - If you want to create your own checkpoint file,
      - you can delete the existing 
        - modelcpnt5ba5d242-aaac-43cc-8593-e6f1d462faa8.keras file
        - results.txt
        - final_results.png
        - /debug_plot directory  
      - then open jupyter notebook and run the "AIDI_1002_Final_Project.ipynb" file
      - after it has completed all 100 epochs, you will have your own model checkpoint file, plots and results.txt file where you can see the results.
      - you can then use this file with command "python inference.py <path_to_checkpoint_file> ../data/validation/FA4DC2D8-C0D9-4ECB-A319-70F156E3AF31.bins" on python console to test it out. 

