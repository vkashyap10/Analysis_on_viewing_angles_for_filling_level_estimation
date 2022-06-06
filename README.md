# Analysis on viewing angles for filling level estimation


Notes: 

1) All code has been tested on GPU capable servers via JupyterHub on https://jhub.eecs.qmul.ac.uk. The   general purpose instance option there intended for ML (tensor) workloads was chosen. Conda environment spec list has also been provided in the sw folder ("spec-file.txt) to create identical condo environments.

2) In all the python files in sw folder, changes have been made to train(), predict(), experiment() and run_kfold() methods of "https://github.com/v-iashin/CORSMAL/blob/main/filling_type/r21d_rgb/main.py"

3) F1 scores from all tests (single view, two view and three view) are saved in "/report/F1_scores_ICV_sub2.xlsx"

Steps to run software:

1. Clone the repository from paper: 
	command: "git clone https://github.com/v-iashin/CORSMAL"

2. Copy all files from sw folder to the following path in the cloned repository
	"CORSMAL/filling_level/r21d_rgb/"

3. If needed install condo environment from sw/spec-file.txt
	command: "conda install --name myenv --file spec-file.txt"
	or command: "conda create --name myenv --file spec-file.txt"

4. Open and run all cells of "main_ViewTests.ipynb" to observe the results. Predictions will be stored in the "CORSMAL/filling_level/r21d_rgb/predictions/" folder.


* Some epochs throw the following warning: 

"UndefinedMetricWarning: Precision is ill-defined and being set to 0.0 in labels with no predicted samples."

This is because some labels in y_test don't appear in y_pred. This warning does not interfere with the training process (we do not minimise the F1 score) or results in any way (F1 score in case of such warnings will always be lower). These warnings have been suppressed in the jupyter notebooks.
