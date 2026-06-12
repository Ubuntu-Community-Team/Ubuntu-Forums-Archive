---
title: "FREE: Bash to convert MySQL tables into Spreadsheets"
date: 2011-04-28
forum: The Cafe
---

### Post by ryandward on 2011-04-28
If anybody is curious I wrote this file for work, and it seems like it should go somewhere, so I am just gonna put it here. Let me know if it belongs somewhere else!

Basically, it queries the user for their MySQL name and Password, and through a series of events, turns MySQL tables into CSV files that are usable in any sort, but more typically for Spreadsheets. This is very useful for those guys at work who have programs like ArcGIS, whose only method of entry is EXCEL! :popcorn:

```
#!/bin/bash
###Convert MySQL files into Excel Files###

#Get user info
echo -e "Enter MySQL user name..." 
    read User

echo -e "Enter MySQL password..." 
    read -s Password

#Authentication successful?
export Valid=`mysql -u $User -e "show databases;" -p$Password`

    if [ "$Valid" == "" ]
    then exit
    fi 

echo -e ""
echo -e ". . . . . ."

###FOR DATABASES###

#Display databases
echo -e "Displaying a list of databases on the system"

mysql -u $User -e "show databases;" -p$Password

#Ask user to pick database
echo -e "Which of these databases would you like to use? Or escape [x]"
    read Dbu
    
        if [ "$Dbu" == "x" ]
        then    echo "... See ya!"
            exit
        fi

#Check to see if database exists
export ExistDbu=`mysql -u$User -p$Password -Bse 'show databases'| egrep -c -x $Dbu`
echo ". . . . . ."
echo "Found $ExistDbu exact match for $Dbu."
echo ". . . . . ."

#Prompt user to fix error if the selection is invalid

while [ "$ExistDbu" == "0" ]
do
    echo "Pick a valid database, or escape [x]."
    read Dbu

        if [ "$Dbu" == "x" ]
        then    echo "... See ya!"
            exit
        fi    
    
    export ExistDbu=`mysql -u$User -p$Password -Bse 'show databases'| egrep -c -x $Dbu`
    echo "Found $ExistDbu exact match for $Dbu."

done

###FOR TABLES###

#Display Tables
echo -e "Displaying a list of tables on the $Dbu database"

mysql -u $User -e "show tables in $Dbu;" -p$Password

#Which table?    
echo -e "Which of these tables would you like to use? Or escape [x]"
    read Table
    
        if [ "$Table" == "x" ]
        then    echo "... See ya!"
            exit
        fi

#Check to see if Table exists
export ExistTable=`mysql -u $User -e "show tables in $Dbu;" -p$Password| egrep -c -x $Table`
echo ". . . . . ."
echo "Found $ExistTable exact match for $Table."
echo ". . . . . ."

#Prompt user to fix error if the selection is invalid

while [ "$ExistTable" == "0" ]
do
    echo "Pick a valid table, or escape [x]."
    read Table

        if [ "$Table" == "x" ]
        then    echo "... See ya!"
            exit
        fi    
    
    export ExistTable=`mysql -u $User -e "show tables in $Dbu;" -p$Password| egrep -c -x $Table`
    echo "Found $ExistTable exact match for $Table."

done

###NAMING CSV###

#Reuqest name for CSV
echo -e "Below is a list of currently existing files"
ls ~/Documents
echo ". . . . . ."
echo -e "What would you like to name the CSV? Or escape [x]"
    read Csv
    
        if [ "$Csv" == "x" ]
        then    echo "... See ya!"
            exit
        fi        

    LocFile=~/Documents/$Csv.csv

while     [ -a $LocFile ]
do
    echo -e "That file name already exists, please pick a new name, or escape [x]."
    echo -e ". . . . . . ."
    read Csv

            if [ "$Csv" == "x" ]
            then    echo "... See ya!"
            exit
            fi

    LocFile=~/Documents/$Csv.csv

done

    echo "Writing table $Table from the $Dbu database."
    mysql -u $User $Dbu -B -e "select * from \`$Table\`;" -p$Password | sed 's/\t/","/g;s/^/"/;s/$/"/;s/\n//g' > ~/Documents/$Csv.csv
    echo "Your new file is located at $LocFile"

```

---

