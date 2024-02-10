# Set things up

<strong>Python v3.10 is required </strong>
 
- <h4>Folder Structure</h4>
    <pre>
    ROOT
    |-fns2020_dataset/
    |  |-training/
    |  | |-annual_reports/
    |  | |-gold_summaries/
    |  |-validation/
    |  | |-annual_reports/
    |  | |-gold_summaries/
    |-generated_summary/
    |-eval/
    | |-projects/
    | | |-test-summarization/
    | | | |-reference/
    | | | |-system/
    | |-resources/
    | |-rouge.properties
    | |-rouge2-1.2.2.jar
    | |-work.ipynb
    |-requirements.txt
    |-final.ipynb
    |-README.md
    |-.env
    |-environment.yml
    </pre>

    We don't provide the dataset.

- Set up `.env` file
<br>
    ```
    TRAINING_DIR="./fns2020_dataset/training/"
    VALIDATION_DIR="./fns2020_dataset/validation/"
    TR_AR="./fns2020_dataset/training/annual_reports/"
    TR_GS="./fns2020_dataset/training/gold_summaries/"
    VAL_AR="./fns2020_dataset/validation/annual_reports/"
    VAL_GS="./fns2020_dataset/validation/gold_summaries/"
    TARGET_DIR="./generated_summary/"
    ```



# Running the code

As most of work has been done in the notebook file, it is advisable to run the notebook either in `VSCode` or `Jupyter notebook`. It is assumed Jupyter Notebook is installed and configured and same is the case with VSCode. We also provide our virtual environment config as `environmnent.yml`. To use this virtual environment, run the comand below

`conda env create -f environment.yml`

To activate this environment,

`conda activate mypython310`

After activating the environment, install the required libraries.

# Installing Required Library

Install the necessary libraries required for this code to run.

`pip install -r requirements.txt`

## Extractive Summary

There are two ways to run the code :-
1) For 1 file (used to test if the code is working, takes less time)
2) For all files in a directory (takes a lot of time)

# For 1 File
> Open 'FileDemo.ipynb'
> Put your text that you want to summarize in input valiable and its gold summary
> Run all the cells, the input will automatically get preprocessed and summarised
> You can view its Rouge Score at the bottom
> Generating Summary takes a lot of time so be patient

# For all files 
> Put all the text files for which you want to create summary in 'annual_reports' directory
> This code will create dataframe and will save it in 'output.csv'
> Run all the cells and this will generate summaries for all the files in a dataframe



## Abstravtive Summary
Launch the notebook from terminal in VSCode. 

While running the ipynb file, choose the python environment `mypython310`

Once the file is run, it will generate the summary files in `TARGET_DIR`.

## Evaluating our summaries.

Make sure to download the ROUGE-2 from [this repo](https://github.com/kavgan/ROUGE-2.0).  Also from the same repo, download the `resources` folder and replace it with the `./eval/resources/` folder.

Move or copy our generated summaries from `./generated_summary/` to `./eval/projects/test-summarization/system/`

Move or copy our gold summaries from `VAL_GS` directory to `./eval/projects/test-summarization/reference/`

Now open the `./eval` directory in terminal and run

`java -jar rouge2-1.2.2.jar`

This will generate the `results.csv` in the same directory.

Run the `work.ipynb` file, it will compute an display average Rouge Score.


