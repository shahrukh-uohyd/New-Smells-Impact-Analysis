**Replication Package — Multi-Language Design Smells and Maintainability**

This replication package accompanies the study
“Smells Across Boundaries: Quantifying the Quality Impact of Multi-Language Design Smells.”

It contains all data, scripts, and results required to reproduce the analyses of smell prevalence, change-proneness, and fault-proneness across 15 open-source JNI systems.

**Directory Summary**
Folder/File	Description
Dataset details.csv :	Contains the details of the projects and the list of releases analyzed.
Smell Detection Implementation/	: Java implementation of the smell detector
Prevalence/	: CSV results of smell detection (per release and per smell type)
Change-proneness/	: Datasets, scripts, and results for RQ2 (change-proneness analysis)
Fault-proneness/	: Datasets, scripts, and results for RQ3 (fault-proneness analysis)

**How to Reproduce the Analyses**
Step 1: Clone all the releases of all the projects listed in Dataset details.csv file.

Step 2: Run Smell Detection

  Each smell must be run separately for clarity. To do this:
  1. Navigate to: Smell Detection Implementation/mlssdd/
  2. Open DetectCodeSmellsAndAntiPatterns.java.
  3. Uncomment the line corresponding to the smell you want to detect and assign dir=”smellName”.
  4. Recompile
  5. Run DetectCodeSmellsAndAntiPatterns.java
  Each run will produce a CSV file under:<SmellName>/<ProjectName>.csv
  Example (detecting ShotgunSurgery):
  • Uncomment codeSmellDetectors.add(new ShotgunSurgery1()).
  • Put dir=”ShotgunSurgery”
  • Run: java “mlssdd.DetectCodeSmellsAndAntiPatterns”
  • Output: ShotgunSurgery/<ProjectName>.csv
  Why One Smell at a Time?
  We intentionally run one smell per execution to:
  • Keep results for each smell separate and easier to validate.
  • Simplify comparison with manually curated ground truth.
  • Improve reproducibility and clarity for future researchers.

Step 3: Compute Prevalence
Use the CSV files in /Prevalence/ to calculate percentages of smelly files per release.

Step 4: Analyze Change-Proneness
Navigate to:
cd Change-proneness/Scripts
Run the script "change and fault proneness.ipynb"

Outputs:
project wise result change simplified.csv
global_logistic_change_results.csv

Step 5: Analyze Fault-Proneness

Navigate to:
cd Fault-proneness/Scripts
Run the script "change and fault proneness.ipynb"

Outputs:
project wise result fault simplified.csv
global_logistic_fault_results.csv

**Data Description**

Each project-level dataset (in Change-proneness and Fault-proneness) includes:

Filepath

Four smell frequency columns (LE, CRD, CLSS, EB)

Binary variable indicating change or fault status
