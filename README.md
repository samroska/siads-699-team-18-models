# siads-699-team-18-models
The models used for the Skin Lesion application https://github.com/samroska/siads-699-team-18-frontend

1. Introduction

Skin cancer is a growing global health concern, with rising incidence rates and limited access to early diagnostic services in many regions- for example melanoma accounts for around 75% of skin cancer-related deaths (Didier et al., 2024). Timely detection is essential as early-stage skin cancers are highly treatable, and prompt diagnosis not only improves patient outcomes but also reduces healthcare costs. However, traditional diagnostic methods depend on specialist expertise, which is often scarce in low-resource or remote settings. The public health impact is further compounded by behavioral barriers—elderly individuals may avoid seeking medical attention for suspicious skin lesions due to fear, mobility issues, or lack of awareness.

Advances in deep learning offer a promising solution to automate the classification of skin lesions from images, potentially expanding access to early assessment. Motivated by these challenges, this project develops and rigorously evaluates machine learning models capable of distinguishing cancerous from benign skin lesions leveraging publicly available datasets. The project developed two complementary models—one designed for healthcare providers using dermatoscopic images, and another for the general public using smartphone images through a mobile-friendly web application. This data-driven accessible approach aims to support clinical triage, reduce unnecessary biopsies and provide an initial self-assessment tool, encouraging earlier medical consultation.

The core questions guiding our research are:

How accurately can deep learning models classify skin lesions, and which architectures perform best in this context?
How can we effectively integrate these models into lightweight applications tailored to health care providers and beneficiaries to support accurate and timely classification?

To address these questions, the project trained multiple Convolutional Neural Networks (CNNs) architectures on PAD-UFES-20 smartphone dataset, Monkeypox Skin Lesion Dataset and the BCN20000 dermatoscopic dataset. It applied class-balancing strategies and finetuned training pipelines to enhance model performance. The best smartphone image model achieved an F1 score of 0.75, while the dermatoscopic model reached a F1 of 0.84, the latter substantially outperforming published baselines. 

In order to reproduce the results, follow the steps below.

2. Directories Structure
The following folders structure is necessary for the software:

.
./Images/
./Images/BCN20000-all-images-original/
./Images/BCN20000-all-images-original/bcn_20k_train
./Images/PAD-UFES-20-all-images/
./Images/PAD-UFES-20-all-images-RGB/
./Images/Images_for_tests
./Images_Arrays/
./Metadata/
./Models/
./Notebooks/
./Training_Results/

3. Steps to Run the Notebooks
3.1. Download Images

Download PAD-UFES-20 from:
https://www.kaggle.com/datasets/mahdavi1202/skin-cancer 

Download Dermatoscopic Images from:
BCN20000: Dermoscopic Lesions in the Wild - figshare 

Download Monkeypox Skin Lesion Dataset (MSLD) from:
https://www.kaggle.com/datasets/nafin59/monkeypox-skin-lesion-dataset 

3. 2. Unzip Images and place them into the directories

./Images/PAD-UFES-20-all-images/
./Images/BCN20000-all-images-original/bcn_20k_train

PAD-UFES-20 images will need to be converted from PNG to RGB. 
The following notebook can be used for that: SIADS699 Smartphone - Images to RGB. 

It will place the RGB images at ./Images/PAD-UFES-20-all-images-RGB/

Notes:
When unzipping MSLD, Monkeypox images will be on ./Original Images/Original Images/Monkey Pox.
Place them at  ./Images/PAD-UFES-20-all-images-RGB/

3. 3. Metadata
The following metadata is available on the folder:

./Metadata/PAD-UFES-20-Metadata.csv
./Metadata/Monkeypox_metadata.csv
./Metadata/BCN20000_metadata_original.csv


3. 4. Visualize Classes Distribution
Run the notebook: SIADS699 - Visualizations V1.ipynb

3. 5. Create Images and Labels Numpy Arrays
Run the notebooks:
SIADS699 Smartphone - Preparation V104.ipynb and 
SIADS699 Dermatoscopic - Preparation V104.ipynb

They will convert the images and Labels in Numpy Arrays:

./Images_Arrays/BCN20000_images_array (112_112).npy
./Images_Arrays/BCN20000_labels_array (112_112).npy
./Images_Arrays/PAD-UFES-20_images_array_112_112.npy
./Images_Arrays/PAD-UFES-20_labels_array_112_112.npy

They will also clean up the Metadata and create the following ones:

./Metadata/PAD-UFES-20-Metadata-One-Hot.csv
./Metadata/BCN20000-Metadata-One-Hot.csv

3. 6. Train the Models
Run the notebooks:

SIADS699 Dermatoscopic - ML Model V101 (Base).ipynb
SIADS699 Dermatoscopic - ML Model V102 (Weights).ipynb
SIADS699 Dermatoscopic - ML Model V103 (Aug).ipynb
SIADS699 Dermatoscopic - ML Model V104 (Weights + Aug).ipynb

SIADS699 Smartphone - ML Model  V101 (Base).ipynb
SIADS699 Smartphone - ML Model  V102 (Weights).ipynb
SIADS699 Smartphone - ML Model  V103 (Aug).ipynb
SIADS699 Smartphone - ML Model  V104 (Weights + Aug).ipynb

Models will be trained and stored on ./Models
Results will also be stored in datasets at ./Training_Results

3. 7. View Training Results
Run the notebook: SIADS699 - Results V1.ipynb

3. 8. Execute Inference
Run the notebooks:

SIADS699 Dermatoscopic - Inference V104.ipynb
SIADS699 Smartphone - Inference V104.ipynb

3. 9. Generate the GradCAM++
Execute the notebooks:

SIADS699 Dermatoscopic - GradCAM V104.ipynb
SIADS699 Smartphone - GradCAM V104.ipynb

