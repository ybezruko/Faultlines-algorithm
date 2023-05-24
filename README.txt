
SAS Faultline Calculation (Version 1.0, July 26, 2004) 

ReadMe File

**********************************************************************************************
* When using this algorithm to calculate faultline scores, please reference
*
* Thatcher, S.M.B., Jehn, K.A., and Zanutto, E. (2002) "Cracks in Diversity Research: The Effects 
* of Faultlines on Conflict and Performance," Group Decision and Negotiation, 12:217-241.
* 
* and
*
* Zanutto, E., Bezrukova, K., and Jehn, K. Measuring group faultlines: Analytical considerations and assumptions (work in progress)
* 
* Code Available at: www-stat.wharton.upenn.edu\~zanutto
*               and: Kate's webpage (http://crab.rutgers.edu/~bezrukov/faultlines.htm)
*
* Algorithm Author: Elaine Zanutto (zanutto@wharton.upenn.edu)
* Programmer: Gregory Giddings 
*
* copyright, all rights reserved, 2004
**********************************************************************************************

1. WHAT THIS CODE DOES

This SAS code will calculate faultline strength and distance for groups of size 3 to 16. 
(This code requires SAS IML). 

2. WHAT WE ASSUME ABOUT THE DATA

The data must be in a comma-separated text file. It is assumed that the first row of the file contains column headers and the data starts on row 2.

All categorical variables must be already recoded into dummy variables (if the variable has 3 categories you need 3 dummy variables, one for each category).

No missing values are allowed (it is assumed that the data has been cleaned).

There must be a variable in the dataset that identifies each group. The groups must be numbered sequentially from 1 to n (where n is the total number of groups).

3. WHAT WE ASSUME ABOUT THE RESCALING FACTORS

Rescaling factors must be specified for each variable to be used in the faultline calculations (note that you may you less variables in the faultline calculations than are contained in the raw data file). The rescaling factors are such that newdata=rawdata*rescaling_factor. So if you want newdata=rawdata/10, specify the rescaling factor for that column as .1.

The rescaling factors must be specified in a comma-separated text file. It is assumed that the first row of the file contains column headers and the data starts on row 2.

4. HOW TO RUN THE CODE

Download the SAS code and data files and copy them to your computer with the following directory structure. (If you decide to put this code in a different directory on your PC you must modify all the path names in C:\Faultline\FL_code\FL_Code_parameters.txt  and in the %include statement in C:\Faultline\FL_code\FL_Code_1_0.sas accordingly).

C:\Faultline
   files: README.txt
C:\Faultline\FL_Code
   files:  FL_Code_1_0.sas
           FL_Code_parameters.txt
           group3.sas7bdat
           group4.sas7bdat
           group5.sas7bdat
           group6.sas7bdat
           group7.sas7bdat
           group8.sas7bdat
           group9.sas7bdat
           group10.sas7bdat
           group11.sas7bdat
           group12.sas7bdat
           group13.sas7bdat
           group14.sas7bdat
           group15.sas7bdat
           group16.sas7bdat
C:\Faultline\FL_SASDataSets
   files: (empty directory until you run the code at least once)
C:\Faultline\FL_Data
   files: FL_testdata.csv
          FL_Rescalingtest.txt
C:\Faultline\FL_Output
   files: FL_test_answers.txt
C:\Faultline\FL_CodeBackup
   files: FL_Code_1.0.sas
          FL_Code_parameters.txt

The code is setup to calculate faultline stengths and distances on test data (FL_testdata.csv) using the gender, race, and age variables in the faultline calculations and using the rescaling factors in (FL_testrescaling.txt). 

To run the code, go to the C:\Faultline\FL_Code directory and double click on FL_Code_1_0.sas. (Alternatively, start SAS and select File-Open and navigate to FL_Code_1_0.sas.) Click on the SAS window with the SAS code. Right click the mouse and select Submit All.  This will create several output files: FL_testoutput.txt, FL_rawdataout.txt, FL_rescalingout.txt (you can choose the filenames, these are the default filenames).

The main output file FL_testoutput.txt  contains 5 columns: group number ("Group"), faultline strength (not allowing  subgroups of size 1) ("Fau1"), faultline distance (not allowing subgroups of size 1) ("FauDist1"), faultline strength (allowing subgroups of size 1) ("Fau2"), faultline distance (allowing subgroups of size 1) ("FauDist2"). The file contains one row of data for each group. To 
verify that everything is working for you, check that the faultline scores in FL_testoutput.txt are
the same as those in FL_testoutput_answers.txt


The two other output files FL_rawdata_out.txt and FL_rescaling_out.txt contain copies of the raw data and rescaling factors (so you can verify that SAS is reading them in correctly and using the right data).


5. HOW TO MODIFY THE INPUT PARAMETERS

All user inputs are specified in the file C:\Faultline\FL_Code\FL_Code_parameters.txt. 
Here you can specify which dataset to use, and what variables to use for the faultline calculations, what to name the output files, etc.

Do not change the name of this file. The master SAS code will look explicitly for the file C:\Faultline\FL_Code\FL_Code_parameters.txt. There is a backup version of this file in the C:\Faultline\FL_Backup directory so you will always have an example to use as a template.

There should be no need to ever modify the master code in C:\Faultline\FL_Code\FL_Code_1_0.sas (except maybe to modify the pathname in the %include statement if you put the parameter file in a different directory thatn C:\Faultline\FL_Code).

A back-up copy of FL_Code_parameters.txt and FL_Code_1_0.sas is contained in C:\Faultline\FL_CodeBackup.





