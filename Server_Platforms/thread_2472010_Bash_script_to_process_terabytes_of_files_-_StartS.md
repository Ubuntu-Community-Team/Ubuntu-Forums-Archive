---
title: "Bash script to process terabytes of files - Start/Stop/Resume/Log"
date: 2022-02-15
forum: Server Platforms
---

### Post by LHammonds on 2022-02-15
**EDIT:** *Wow, I cannot stress enough how excited my boss is about what I created.  Bash+SQLite for the win!  The initial code worked as intended but was slower than I wanted so I ended up porting the code into Perl and use an SQLite API and it it did indeed reduce the amount of system calls to speed it up considerably (no external calls to grep/sed/sleep/etc.)*

I need to find or design a bash script that processes files and has the capability of logging results and resuming where it left off if the process gets interrupted.

It would function similar to rsync how it handles the copying of files from one location to another but I need it to handle a few situations due to the expected long-running time to process (days or weeks):

1. Loop through a list of files/folders to process a command on each one.
2. Has the ability to log success/failure for each file.
3. Has the ability to start again and not process the files it already handled.
4. Extra ability to re-process all files that have failed.

My initial thought is to scan the file names/paths into a database table.  Then loop through the database rows and update the status record for each file after processing.

Any thoughts or suggestions?  I have tried searching for existing solutions like this but found nothing (my google-fu may not be strong)

**EDIT:** For those curious, this is to import DICOM files into an Orthanc server.

Thanks,
LHammonds

---

### Post by #&amp;thj^% on 2022-02-15
> **LHammonds said:**
> I need to find or design a bash script that processes files and has the capability of logging results and resuming where it left off if the process gets interrupted.

It would function similar to rsync how it handles the copying of files from one location to another but I need it to handle a few situations due to the expected long-running time to process (days or weeks):

1. Loop through a list of files/folders to process a command on each one.
2. Has the ability to log success/failure for each file.
3. Has the ability to start again and not process the files it already handled.
4. Extra ability to re-process all files that have failed.

My initial thought is to scan the file names/paths into a database table.  Then loop through the database rows and update the status record for each file after processing.

Any thoughts or suggestions?  I have tried searching for existing solutions like this but found nothing (my google-fu may not be strong)

**EDIT:** For those curious, this is to import DICOM files into an Orthanc server.

Thanks,
LHammonds
This may take some thought to get your desired output: [https://stackoverflow.com/questions/56913648/upload-folder-dicom-with-orthanc-library](https://stackoverflow.com/questions/56913648/upload-folder-dicom-with-orthanc-library)
Peaked Interest here on how this turns out. :D
Good Luck

---

### Post by LHammonds on 2022-02-15
I know about the batch uploads provided by orthanc's Python examples.  The problem is if you set it to run against a hundred terrabytes of of files and it fails 3/4 the way through, there is no recourse other than submitting it again...which might allow duplicates or it might reject the duplicates but either way it will re-process all the same files over again.

I have at least 3 different ways I can send to Orthanc....via the REST API like the Python examples or via the DICOM port with tools such as **storescu** or **dcmsend** (from **dcmtk** package).

I'm looking at how to leverage sqlite3 for the database since I won't need a full-featured SQL server but need something better than text files.

I am really surprised I have not found something that handles huge files like this yet but then again, most of the planet does not deal with such large data sets...but such a thing would be useful for small data sets too.

**EDIT:** Initial research into utilizing an sqlite database in a bash script is VERY promising.

LHammonds

---

### Post by kevdog on 2022-02-16
I'm curious what you find.  I can't imagining handling terabytes of data with the solution.  I'm not sure how big each individual file you need to back up would be, however say you're processing 5Tb of data and the system dies 3Tb in.  Your next run would have to scan and compare all current files to those in the dataset??

Are you planning on using rsync as the actually transfer program and using error codes from this run?
Do you need to first scan all the files at the source (on every run) and make sure each file has an entry in the database?
Each file would then be assigned a flag designating it's been backed up or not -- once all files receive the flag the "entire" dataset could be designated as being "backed up" with certain timestamp and each file's backup status flag reset.  
Were you planning on using python or other language for such script?

---

### Post by MAFoElffen on 2022-02-16
Before getting through the first third of your Post #1, I was already thinking of a database file list, so you can keep a list of files and update when each is completed. 

On transferring large files, with a resume, my first choice is, if the target file does not exist...
```

rsync -aP /from/source/file /to/target/directory

```
else if it does (resume)
```

rsync -aP --append /from/source/file /to/target/directory

```

Second choice curl.

But thought I am good at Bash Scripts, It's not my first choice when dealing with datastructures or databases. My first choice for that is Python... BUT then you brought up SQLite...

Since small list, and your thought of using SQLite... Great idea. It has a great CLI API, that you can use from BASH, if you setup your record layout to keep your place and pointers under control...
 For example a record layout of:
```

CREATE TABLE FileListTable (file_id INTEGER PRIMARY KEY, path_from VARCHAR(50), file_name VARCHAR(30), completed BOOLEAN);

```
Note SQLite does recognize BOOLEAN as TRUE or FALSE (after version 3.23.0, circa early 2018) but also recognizes and stores as 1 (as True) and 0 (as False) for before that version through current versions.

When you call SQLite from a script, you can save SQL groups of commands in files as a SQL script to tell SQLite to run and use that script file... or run commands directly from Bash like this (pseudo code to map out the logic)
```

#!/bin/bash

# Probably already created prior to this for a complete file list that needs to be done... but shown here as an example from a script, and to show the record layout
# sqlite3 LHammands.db  "CREATE TABLE FileListTable (file_id INTEGER PRIMARY KEY, path_to VARCHAR(50), file_name VARCHAR(30), completed BOOLEAN)"

# Lots of code
#  CurrenFile=1 # counter

#Loop until end of list, use table length (row count) plus 1 for limit.
    # read record where file_id = $CurrentFile
    # if completed equals 0, increment CurrentFile Counter, then continue
    # else path=path_from, file=file_name
        # loop for while not done 
            # rsync -aP --append $path$file $TargetDirectory
            # set successful exit as done, if not (error or interruption) then it continues loop
            # When file rysnc is completed for a file, using the file_id used to transfer that file... as $CurrentFile
            # sqlite3 LHammond.db  "UPDATE FileListTable SET completed = true WHERE (SELECT * WHERE file_id = $CurrentFile);"
            # increment counter Currentfile, being done i will bounce out to outer loop for next file...
# Done

# etc...

```

---

### Post by LHammonds on 2022-02-16
The process of each file is not a file copy...or rsync would be the preferred solution.   The action taken on each file is similar to sending a file via FTP command.

I have finished designing the database tables and how they will be used.

Instead of a boolean for status, I opted for a wider range by using an integer with a default of zero.  Zero means unprocessed, 1 means successful completion, 2 means failure.

Instead of maintaining a loop from a database standpoint, I am simply looping until I reach a condition of "no more records to process"

Each time I touch the database, I query the top 1 records where status = 0.  So each time I run that query, it gives me the next file to process.  No "state" needs to be maintained nor do I have to re-scan anything if the process needs to be stopped and restarted.

Once I finish processing the file, I update the record with the results and other data such as file size, date modified, etc.  If there is an error, I write extra information to an error table and record the file ID as a foreign key.

When it is all done, I can get a summary by grouping and summing the status column.

I can run a similar script that only looks at the failures (status = 2) and try to send them all again using the same process.

The next phase after that would be to get a list of the failed files and examine why they failed (such as validating data file structure using **dciodvfy** from the **dicom3tools** library), fix the issue if possible and re-run again if necessary.  If a file cannot be fixed, set status to 4 and be done with it.

LHammonds

---

### Post by kevdog on 2022-02-17
@LHammonds -- nice design.  Thanks for sharing. Probably should include your mysql database as part of your backup.

---

### Post by LHammonds on 2022-02-18
I have the 1st version of the database creation and file scan completed.  Here is a sample output against a test folder.
```

2022-02-18_12:35:19 - DICOM scan started.
[INFO] Old database file found, deleting it...
[INFO] Creating database file...
[INFO] Scanning /bak/ for DICOM files...
/bak/0002.dcm|1702398|1
/bak/0004.DCM|560498|1
/bak/invalid.dicom|0|0
/bak/0015.DCM|1049988|1
/bak/invalid.dcm|0|0
/bak/invalid.dic|0|0
/bak/0020.DCM|426776|1
/bak/dicom.db|16384|0
/bak/0009.DCM|2615370|1
/bak/0012.DCM|1364618|1
/bak/0003.DCM|577536|1
/bak/t/MRBRAIN.DCM|526336|1
/bak/t/dicom.db|12288|0

RECORD SUMMARY:
Total Send Errors: 0
Total Records: 13
 |_ Total Invalid Dicom: 5
 |_ Total Valid Dicom: 8
    |_ Unprocessed: 13
    |_ Processed: 0

PERCENTAGE SUMMARY:
Valid Unprocessed: 100.00%
Valid Processed: 0%
Send Errors: 0%
Total running time: 0 hour(s) 0 minute(s) 2 second(s)
2022-02-18_12:35:21 - DICOM scan completed.

```
For testing, I have it throwing out a list of files imported so I can see how my script is evaluating the files.  It only shows the filenames with full path, file size and if the file has a valid DICOM structure.

Since there isn't any method for guaranteeing a file will import as a DICOM image, I simply assume it is valid so it will at least have a chance to go through the DICOM send script later...unless the check finds a very-specific chunk of verification results that does not exist when validating against known-good DICOM images.  If it finds this marker, it sets the column to 0 (invalid), otherwise it is valid (1) and will be processed by the send script later.

I record the file size only for the purpose of analyzing failed attempts later.

LHammonds

---

