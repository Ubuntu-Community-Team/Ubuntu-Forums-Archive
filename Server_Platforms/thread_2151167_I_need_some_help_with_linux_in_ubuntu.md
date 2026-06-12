---
title: "I need some help with linux in ubuntu?"
date: 2013-06-03
forum: Server Platforms
---

### Post by Mrno1knows on 2013-06-03
Hello everyone I'm a newb to linux and I would like to write some codes for this BUT I would like some help for this scenario: 

I have been asked to provide a shell script to perform a range of backup and restore tasks.  The program will be menu driven and will provide the following options:
 

[LIST]
[*]Backup all files from a location specified on the command line to a date stamped folder with yesterday’s date
[*]Carry out an incremental backup i.e. only files that have altered since the last backup
[*]Restore files from a specified backup location
[*]Quit the system
[/LIST]
 
Command line parameters will be passed that will indicate the locations of files to be backed up and restored to. 
 
The program should be menu driven and user friendly.  The menu will be displayed repeatedly until the user selects the option to quit.  The program should be robust and should inform the user what is happening.

---

### Post by jonobr on 2013-06-03
What have you researched so far?

---

### Post by grunge09 on 2013-06-04
Have your tried cmd line Rsync, of its GUI froentend GRSYNC ?  Or SBackup/SRestore?  

I use this for a rsync command line.

rsync -avpL  --progress --delete --log-file=/home/user1/rlog/$(date +%Y%m%d)_rsync.log /home/user1/ /mnt/networkuser1save

--progress will show you what it is doing

--delete will do as it says delete remote files that no longer exist on the local host system.  You do not have to use --delete but it will eat up space on your remote system over time.  

--logfile creats a dated log file in a specified user1 path.  in my case I made a folder /home/user1/rlog
replace "user1" with your local /home/userpathname

replace /networkuser1save with network path save name (in my case I have it auto mounted via /etc/fstab)  In my case I use Samba to backup to a Ubuntu Server with RAID5 MDADM, and another box with Freenas hardware raid 5.  using 2 similar rsync cmds.  

my /etc/fstab line addition: 

//mylocalfileserver/backup /mnt/mynetbackup smbfs credentials=/root/.smbcredentials,iocharset=utf8,uid=user1,gid=myhomelan,nounix,file_mode=0777,dir_mode=0777 0 0

"mylocalfileserver" is your servers name or IP address

"mynetbackup" is the name of the folder you create on your local client drive in the /mnt folder

"uid=user1" replace user1 with your smb user name

"gid=myhomelan" replace myhomelan with the smb group on server

UID and GID should be the same on server and client.

1st backup will take a while.  backups after that will be much faster as it will be backing up only changed files.

---

### Post by Mrno1knows on 2013-06-05
#This script is to make backups and displaying username and dates
#
#
clear 
id -un
date
#I have set the case varaible to 0
loopvariable=0
menus()
{
while [$loopvariable !=5]
do
echo
 "Please Choose the following options
1. Option 1 to backup files from a certain locations
2. Make a Incremental backup
3. Restoring a back up
5. End the program


Case $loopvariable in 
1) clear
 option1
read -p "You have selected option1"
;;
2) clear
        option2
read - p "You have selected option2"
;;
3) clear 
        option3 $1
read -p "You have selected option3"
;;
5) exit


#*) echo "The option you have selected is incorrect"
esac
clear
done
}
#This is the last line of the menu
option1()
{
mkdir files
mkdir backup
mkdir backup/'date -i -d "1 day ago"
}
option2()
{
DAY0= 'date -i '
DAY1= 'date -i -d "1 day ago"
SRC=/home/nf/empty/assessment/$DAY0
TRG='date -I'
LNK=/home/nf/empty/assessment/$DAY1
OPT= -avh --link dest=$LNK
rsync $OPT $SRC $TRG
}
option3()
{
cp 'date -i -d "1 day ago" $1
}


clear 
menu $1

I spent hours trying this but I am getting this error.

./assessment.sh: line 60: unexpected EOF while looking for a matching ' ' '
./assessment.sh: line 70: syntax error: unexpected end of file

I would really appreciate if anyone can help me to fix this program so it actually runs and works

---

### Post by SeijiSensei on 2013-06-05
```
mkdir backup/'date -i -d "1 day ago"
```

This line is missing the matching "backtick" ("`").

I recommend replacing the backticks with the $() operator since there are other lines that appear to have the apostrophe where a backtick should be used.

The command above would become:

```
mkdir "backup/$(date -i -d '1 day ago')"
```

---

### Post by Mrno1knows on 2013-06-05
Hello thanks but I done some changes and it kind of works Except I don't understand when choosing the options (1,2,3) I get an error message. I was wondering if anyone know what the code I have to type in to make each of the options work:
#This script is to make backups and displaying username and dates
#
#
clear 
id -un
date
#I have set the case varaible to 0
menu()
{
while 
do
echo
 "Please Choose the following options
1. Backup files from a certain locations
2. Make a Incremental backup
3. Restoring a back up
5. End the program

read loopvariable

Case $loopvariable in 
1) clear
 option1
read -p "You have selected option1"
;;
2) clear
        option2
read - p "You have selected option2"
;;
3) clear 
        option3 $1
read -p "You have selected option3"
;;
5) exit

#*) echo "The option you have selected is incorrect"
esac
clear
done
}
#This is the last line of the menu
option1()
{
mkdirbackup
DEST=backup/`date -i -d "1 day ago"`
#Copy files from location specified at runtime to /backup4-6-13
#copy everything source destination
#destination = folder created DEST
#source = $1 name of the file entered when calling file eg ./assessment.sh stuff
}
option2()
{
DAY0= `date -i `
DAY1= `date -i -d "1 day ago"`
SRC=/home/nf/empty/assessment/$DAY0
TRG='date -I'
LNK=/home/nf/empty/assessment/$DAY1
OPT= -avh --link dest=$LNK
rsync $OPT $SRC $TRG
}
option3()
{
cp $1
}

---

### Post by Mrno1knows on 2013-06-06
anyone able to help me out please

---

### Post by Mrno1knows on 2013-06-07
Menu Selection:

[http://i44.tinypic.com/bjajyw.png](http://i44.tinypic.com/bjajyw.png)


Option1
[http://i40.tinypic.com/2vvl4d0.png](http://i40.tinypic.com/2vvl4d0.png)
Option2
[http://i42.tinypic.com/de68pe.png](http://i42.tinypic.com/de68pe.png)

Option3
[http://i39.tinypic.com/mj7huq.png](http://i39.tinypic.com/mj7huq.png)
--------------------------------------

#This script is to make backups and displaying username and dates
#
#
clear 
id -un
date
#I have set the case varaible to 0
menu()
{
while 
do
echo
 "Please Choose the following options
1. Backup files from a certain locations
2. Make a Incremental backup
3. Restoring a back up
5. End the program

read loopvariable

Case $loopvariable in 
1) clear
 option1
read -p "You have selected option1"
;;
2) clear
        option2
read - p "You have selected option2"
;;
3) clear 
        option3 $1
read -p "You have selected option3"
;;
5) exit

#*) echo "The option you have selected is incorrect"
esac
clear
done
}
#This is the last line of the menu
option1()
{
mkdirbackup
DEST=backup/`date -i -d "1 day ago"`
cp -r /home/nf/$1/home/nf/backup/` date -I -d£1 day ago"`
#Copy files from location specified at runtime to /backup4-6-13
#copy everything source destination
#destination = folder created DEST
#source = $1 name of the file entered when calling file eg ./assessment.sh stuff
}
option2()
{
DAY0= `date -i `
DAY1= `date -i -d "1 day ago"`
SRC=/home/nf/empty/assessment/$DAY0
TRG='date -I'
LNK=/home/nf/empty/assessment/$DAY1
OPT= -avh --link dest=$LNK
rsync $OPT $SRC $TRG
}
option3()
{
cp -r /home/nf/assessment/incremental/home/nf
}
clear
menu $1
#End of file

---

### Post by Mrno1knows on 2013-06-07
I'm having issues selecting the options since I'm not sure what to do, 

If you cannot see the picture properly: these are the errors


-----------------------------------
The following errors 

Option1: backup date:invalid option -- 'i'
Try `date --help for more information
cp: missing destination file operand after `/home/nf/home/nf/backup/2013-06-06
Try `cp --help` for more information


Option2: date invalid option -- `i`
Try `date --help` for more information.
date: invalid option -- `i`
Try `date --help` for more information.
./assessment7.sh: line 56: date -i: command not found
./assesment7.sh: line 60: -avh:command not found
drwxrwxr-x    4096 2013/06/06 00:59.59 .
-rw-rw-r--   13     2013/06/06/ 00:43:26 .txt
drwxrwxr-x  4096 2013/06/06 00:59:59 date


Option3: cp:missing destination file and operand after `/home/nf/assessment/incremental/home/nf`
Try `cp --help for more information

---

