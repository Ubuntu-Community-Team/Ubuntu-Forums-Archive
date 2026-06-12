---
title: "Simple backup script solution"
date: 2010-01-11
forum: Server Platforms
---

### Post by toshko3 on 2010-01-11
Hi all!
After lots of google i couldn't find any program or script to do the backup i want. So i did it for myself and wanted to post it here for all who want it :popcorn: !
The way I wanted to backup is as follows:
I wanted to use the "cp -af" command so the time stamps and the permissions are kept. Also there is no need to decompress or extract the files this way. You even could give share via samba to the customers of the backup and they browse for the file they need. If you need some file - you just go there and get it!
Also it seems that the "cp -af" skippes bad sectors and goes on, which is a VERY big plus.
I wanted if something is not successful to receive mail and abort anything even on the next cronjob, until I check what is wrong. Presuming that you use raid1 and the mdadm mail function (if you use soft raid of course) you will have a very stable and informing backup system.
All of the 3 script files need to be in the same directory. They are started as I commented at the script itself and the main script is started via a cronjob. Example:
```

00 00 * * 6 /root/scripts/backup/backup.sh

```
You must initially start the initialBackup.sh for as many times as you want (as many backups as you want to maintain). If you have for example, like me, one 500GB data disk and one 1000GB backup disk you will want to start the initialBackup.sh script 2 times for the creation of 2 backups. So the next time the backup.sh starts it will delete the older one and copy the newest to the 1000GB backup disk. The next time it will do the same - delete the older one (the oldest one to be exact) and copy the newest. This way you will always have 2 backups of the backup source.

This is the main backup.sh script:

```

#!/bin/bash
#################################################################################
#										#
# This script works like this:							#
#1. Check if the last backup is done successfuly and if it has then goes on,	#
#else - aborts itself								#
#2. Get the oldest dir in "target backup dir"                                   #
#3. Delete it                                                                   #
#4. Copy the new archive "source backup dir" in the "target backup dir"         #
#If you have nothing in the "target backup dir" the script will delete nothing  #
#and abort with error message.                                                  #
#If you have 1 backup in the "target backup dir" the script will delete it and  #
#create the new backup.                                                         #
#If you have 2 or more backups, the script will delete the oldest one and       #
#create the new backup.                						#                                         
#If any error occures during the script process, it sends email with the error	#
#log and aborts itself.								#
#This script (backup.sh) is the only file that is needed			#
#for itself to be run. It creates the "backupSuccessValue.txt"			#
#and the "backup$(date +%d%m%y).log" in its containing directory		#
#for they are relatively small and can be stored anywhere.			#
#"backupSuccessValue.txt" is with the value of "0" when the backup is successful#
#and with the value of "1" when it is not. The script will not be executed if	#
#the value is "1" because it may delete the last remained archive. It will	#
#send mails to alert you that it will not be run and will do this at every	#
#reboot of the machine if you get the "backupRcLocalCheck.sh" file to be	#
#started at the "rc.local" script. 						#
#It also creates the "cp.log" and "cpStartEnd.log" files within the newly	#
#created target backup dir, because they are related only to the current	#
#backup and "cp.log" could be very large (some megabytes).			#
#The "cp.log" is the output of "cp -afv $b_source $b_target/$currentdate".	#
#The "cpStartEnd.log" is when the copy started and ended. It is in separate	#
#file because the "cp.log" is often very large to open and wait only for these	#
#two values.									#
#The $date is without hour value because I assume that the minimum interval you	#
#will run this script is 1 day long. If it is not you can add "_%T" in it. Add	#
#exactly "_%T" because the other "date" options may leave interval in certain	#
#circumstances (like when the date is 01.12.10 or similar hour - the first 0 is	#
#ommited and replaced with interval).						#
#										#
#################################################################################

######## Values for user configuration ##############
#Backup source - do not put "/" in the end of the target dir, because it will be doubled in the script commands.
b_source=/home

#Backup target - do not put "/" in the end of the target dir, because it will be doubled in the script commands.
b_target=/media/backup

#Current path which your script resides in, so that the logs could be accessed and created. Otherwise the cronjob will put/search all the files within the user's (by which the cron is ran) home dir. 
dir=/root/scripts/backup

#Mail address for errors to be sent (for mails to be sent, there must be a mail agent
#installed, configured and tested, working with the "mail" command)
mailaddress=mailaddress@maildomain.com

######### Values not to be touched ###############
currentdate=$(date +%d%m%y)
host=$(hostname)
date=$(date +%d%m%y,%T)
oldestdir=$(ls -tad $b_target/* | tail -1 | head -1)
log=backup$(date +%d%m%y).log
oldestlog=$(ls -tad $dir/backup*.log | tail -1 | head -1)

######### The real job ##########

if [ "$(head -1 $dir/backupSuccessValue.txt)" = "0" ]; then #Check for previous success of backup - if not - this script will not be executed
	echo "1" > $dir/backupSuccessValue.txt
	echo "$(date): Backup started but not ended yet." >> $dir/backupSuccessValue.txt
	echo "If you see this message and the script is not running, then it is most probably interrupted by something (power failure?)." >> $dir/backupSuccessValue.txt
	echo "You can force it to run by overwriting the above "1" value to "0" and run it again." >> $dir/backupSuccessValue.txt
	echo "$(date +%d%m%y,%T) Trying to: mkdir -v $b_target/$currentdate"
	echo "$(date +%d%m%y,%T) Trying to: mkdir -v $b_target/$currentdate" > $dir/$log
	mkdir -v $b_target/$currentdate 2>> $dir/$log
	if [ "$?" = "0" ]; then
		echo "$(date +%d%m%y,%T) Succeeded: mkdir -v $b_target/$currentdate"
		echo "$(date +%d%m%y,%T) Succeeded: mkdir -v $b_target/$currentdate" >> $dir/$log
		echo "$(date +%d%m%y,%T) Trying to: rm -vR $oldestdir" >> $dir/$log
		echo "$(date +%d%m%y,%T) Trying to: rm -vR $oldestdir"
		rm -vR $oldestdir 2>> $dir/$log
		if [ "$?" = "0" ]; then
		        echo "$(date +%d%m%y,%T) Succeeded: rm -vR $oldestdir"
		        echo "$(date +%d%m%y,%T) Succeeded: rm -vR $oldestdir" >> $dir/$log
			date > $b_target/$currentdate/cpStartEnd.log
		        echo "$(date +%d%m%y,%T) Trying to: cp -afv $b_source $b_target/$currentdate" >> $dir/$log
			echo "$(date +%d%m%y,%T) Trying to: cp -afv $b_source $b_target/$currentdate"
			cp -afv $b_source $b_target/$currentdate > $b_target/$currentdate/cp.log
		        	if [ "$?" = "0" ]; then
					date >> $b_target/$currentdate/cpStartEnd.log
					echo "0" > $dir/backupSuccessValue.txt #This value "0" means that the backup (copy) is executed successfuly (by bash logic)
					echo "$(date)" >> $dir/backupSuccessValue.txt
					echo "$(date +%d%m%y,%T) Succeeded: cp -afv $b_source $b_target/$currentdate"
					echo "$(date +%d%m%y,%T) Succeeded: cp -afv $b_source $b_target/$currentdate" >> $dir/$log
					rm $oldestlog 2>> $dir/$log
					echo "$(date +%d%m%y,%T) All done!"
				else
					echo "1" > $dir/backupSuccessValue.txt #This value "1" means that the backup (copy) is not executed successfuly (by bash logic)
			                echo "$(date)" >> $dir/backupSuccessValue.txt
					echo "$(date +%d%m%y,%T) Error: cp -afv $b_source $b_target/$currentdate"
					echo "Look at $b_target/$currentdate/cpStartEnd.log and $b_target/$currentdate/cp.log for more info!"
			                echo "Error!"
					echo "$(date +%d%m%y,%T) Error: cp -afv $b_source $b_target/$currentdate" >> $dir/$log
					echo "Look at $b_target/$currentdate/cpStartEnd.log and $b_target/$currentdate/cp.log for more info!" >> $dir/$log 
			                mail -s $host,$date,BackupFailed $mailaddress < $dir/$log
				fi
		else
			echo "1" > $dir/backupSuccessValue.txt
	        	echo "$(date)" >> $dir/backupSuccessValue.txt
			echo "$(date +%d%m%y,%T) Error: rm -vR $oldestdir"
			echo "Catting $dir/$log:"
			echo "########### Start of $dir/$log #########"
			echo "$(cat $dir/$log)"
			echo "########### End of $log #########"
			echo "Error!"
			echo "$(date +%d%m%y,%T) Error: rm -vR $oldestdir" >> $dir/$log
			mail -s $host,$date,BackupFailed $mailaddress < $dir/$log
		fi
	else
		echo "1" > $dir/backupSuccessValue.txt
		echo "$(date)" >> $dir/backupSuccessValue.txt
	        echo "$(date +%d%m%y,%T) Error: mkdir -v $b_target/$currentdate"
	        echo "Catting $dir/$log:"
	        echo "########### Start of $dir/$log #########"
	        echo "$(cat $dir/$log)"
	        echo "########### End of $dir/$log #########"
	        echo "Error!"
		echo "$(date +%d%m%y,%T) Error: mkdir -v $b_target/$currentdate" >> $dir/$log
		mail -s $host,$date,BackupFailed $mailaddress < $dir/$log
	fi
else
echo "$(date +%d%m%y,%T) Error: The previous backup is not successful"
echo "For more info look at $dir/backupSuccessValue.txt"
echo "$(date +%d%m%y,%T) Error: The previous backup is not successful" >> $dir/$log
echo "For more info look at $dir/backupSuccessValue.txt" >> $dir/$log
echo "Ending script - nothing will be done" >> $dir/$log
mail -s $host,$date,BackupFailed $mailaddress < $dir/$log
echo "Ending script - nothing will be done"
fi

exit


```
This is the initial backup script - initialBackup.sh:
```

#!/bin/bash
#################################################################################
#										#
#This is the initial backup script. Run it as many times as backups you want	#
#initially. This is because the main "backup.sh" script works like this:	#
#1. Get the oldest dir in "target backup dir"					#
#2. Delete it									#
#3. Copy the new archive "source backup dir" in the "target backup dir"		#
#If you have nothing in the "target backup dir" the script will delete nothing	#
#and abort.									#
#If you have 1 backup in the "target backup dir" the script will delete it and	#
#create the new backup.								#
#If you have 2 or more backups, the script will delete the oldest one and	#
#create the new backup.								#
#Example: You are currently using one 500GB HDD and 1 1TB HDD. You have 500GB of#
#data on the first HDD and use the 1TB HDD only for backup purpouses. If you had#
#500GB HDD for backup purpouses you would have to delete the old backup, remain	#
#with nothing and then start coppying the new backup. So if something happens	#
#with the new coppying process you end up with nothing. So the smart choice is 	#
#to have at least double sized HDD for backup. So, you want to always		#
#have at least one backup in case something happens with the coppying process 	#
#of the new backup and the last backup remains untouched. Then the script	#
#deletes the oldest one and creates the new one.				#
#										#
#The $date is with %T (hour and minute) at the end so you can backup as many	#
#backups as you want at the beginning (on the same date) without overwriting the#
#older ones. In the main "backup.sh" script it is without the %T value because	#
#I assume that the minimum interval is 1 day for backups. If you want you can	#
#change it in the main script too.						#
#################################################################################

######## Values for user configuration ##############
#Backup source - do not put "/" in the end of the target dir, because it will be doubled in the script commands.
b_source=/home

#Backup target - do not put "/" in the end of the target dir, because it will be doubled in the script commands.
b_target=/media/backup

#Mail address for errors to be sent (for mails to be sent, there must be a mail agent
#installed, configured and tested, working with the "mail" command)
mailaddress=mailaddress@maildomain.com

######### Values not to be touched ###############
currentdate=$(date +%d%m%y_%T)
host=$(hostname)
date=$(date +%d%m%y,%T)
oldestdir=$(ls -tad $b_target/* | tail -1 | head -1)
log=backup$(date +%d%m%y).log

######### The real job ##########

#if [ "$(head -1 backupSuccessValue.txt)" = "0" ]; then #Check for previous success of backup - if not - this script will not be executed
	echo "1" > backupSuccessValue.txt
	echo "$(date): Backup started but not ended yet." >> backupSuccessValue.txt
	echo "If you see this message and the script is not running, then it is most probably interrupted by something (power failure?)." >> backupSuccessValue.txt
	echo "You can force it to run by overwriting the above "1" value to "0" and run it again." >> backupSuccessValue.txt
	echo "$(date +%d%m%y,%T) Trying to: mkdir -v $b_target/$currentdate"
	echo "$(date +%d%m%y,%T) Trying to: mkdir -v $b_target/$currentdate" > $log
	mkdir -v $b_target/$currentdate 2>> $log
	if [ "$?" = "0" ]; then
		echo "$(date +%d%m%y,%T) Succeeded: mkdir -v $b_target/$currentdate"
		echo "$(date +%d%m%y,%T) Succeeded: mkdir -v $b_target/$currentdate" >> $log
#		echo "$(date +%d%m%y,%T) Trying to: rm -vR $oldestdir" >> $log
#		echo "$(date +%d%m%y,%T) Trying to: rm -vR $oldestdir"
#		rm -vR $oldestdir 2>> $log
#		if [ "$?" = "0" ]; then
#		        echo "$(date +%d%m%y,%T) Succeeded: rm -vR $oldestdir"
#		        echo "$(date +%d%m%y,%T) Succeeded: rm -vR $oldestdir" >> $log
			date > $b_target/$currentdate/cpStartEnd.log
		        echo "$(date +%d%m%y,%T) Trying to: cp -afv $b_source $b_target/$currentdate" >> $log
			echo "$(date +%d%m%y,%T) Trying to: cp -afv $b_source $b_target/$currentdate"
			cp -afv $b_source $b_target/$currentdate > $b_target/$currentdate/cp.log
		        	if [ "$?" = "0" ]; then
					date >> $b_target/$currentdate/cpStartEnd.log
					echo "0" > backupSuccessValue.txt #This value "0" means that the backup (copy) is executed successfuly (by bash logic)
					echo "$(date)" >> backupSuccessValue.txt
					echo "$(date +%d%m%y,%T) Succeeded: cp -afv $b_source $b_target/$currentdate"
					echo "$(date +%d%m%y,%T) Succeeded: cp -afv $b_source $b_target/$currentdate" >> $log
					echo "$(date +%d%m%y,%T) All done!"
				else
					echo "1" > backupSuccessValue.txt #This value "1" means that the backup (copy) is not executed successfuly (by bash logic)
			                echo "$(date)" >> backupSuccessValue.txt
					echo "$date Error: cp -afv $b_source $b_target/$currentdate"
					echo "Look at $b_target/$currentdate/cpStartEnd.log and $b_target/$currentdate/cp.log for more info!"
			                echo "Error!"
					echo "$(date +%d%m%y,%T) Error: cp -afv $b_source $b_target/$currentdate" >> $log
					echo "Look at $b_target/$currentdate/cpStartEnd.log and $b_target/$currentdate/cp.log for more info!" >> $log 
			                mail -s $host,$date,BackupFailed $mailaddress < $log
				fi
#		else
#			echo "1" > backupSuccessValue.txt
#	        	echo "$(date)" >> backupSuccessValue.txt
#			echo "$(date +%d%m%y,%T) Error: rm -vR $oldestdir"
#			echo "Catting $log:"
#			echo "########### Start of $log #########"
#			echo "$(cat $log)"
#			echo "########### End of $log #########"
#			echo "Error!"
#			echo "$(date +%d%m%y,%T) Error: rm -vR $oldestdir" >> $log
#			mail -s $host,$date,BackupFailed $mailaddress < $log
#		fi
	else
		echo "1" > backupSuccessValue.txt
		echo "$(date)" >> backupSuccessValue.txt
	        echo "$(date +%d%m%y,%T) Error: mkdir -v $b_target/$currentdate"
	        echo "Catting $log:"
	        echo "########### Start of $log #########"
	        echo "$(cat $log)"
	        echo "########### End of $log #########"
	        echo "Error!"
		echo "$(date +%d%m%y,%T) Error: mkdir -v $b_target/$currentdate" >> $log
		mail -s $host,$date,BackupFailed $mailaddress < $log
	fi
#else
#echo "$(date +%d%m%y,%T) Error: The previous backup is not successful"
#echo "For more info look at backupSuccessValue.txt"
#echo "$(date +%d%m%y,%T) Error: The previous backup is not successful" >> $log
#echo "For more info look at backupSuccessValue.txt" >> $log
#echo "Ending script - nothing will be done" >> $log
#mail -s $host,$date,BackupFailed $mailaddress < $log
#echo "Ending script - nothing will be done"
#fi

exit


```

This is the backupRcLocalCheck.sh to be run from rc.local:
```

#!/bin/bash

#########################################################################################	
#											#
#This script will check at startup (when placed to be run at the rc.local of course)	#
#if the backup is successful or not. If it is not then it will execute the 		#
#"backup.sh" script which will send mail alert to the configured mail address.		#
#This script itself must be contained within the same directory as the "backup.sh" is.	#
#Example command in rc.local: /root/scripts/backup/backupRcLocalCheck.sh		#
#											#
#########################################################################################

if [ "$(head -1 backupSuccessValue.txt)" = "1" ]; then
	./backup.sh
else
	exit
fi
exit



```

All of them must be in the same directory to work. I have posted description of the way they work in the commented space of the scripts.
I'll be glad if you post some comments about it and errors if found!
:-)

---

### Post by barnex on 2010-01-11
For such a job, I would really, really recommend using rsync instead of cp. It's the de-facto way to backup.

---

### Post by fjgaude on 2010-01-13
Yes, **rsync**, or even **Grsync**, for backups.

---

### Post by jocampo on 2010-01-13
what about "tar" combined with anacron ? I know it could be simple, but is another option. If you include compression, you could save some space. "diff" flag can be used to compare missing files.

---

### Post by falconindy on 2010-01-13
In addition to the above recommendations:

1) You're piping, verbosely, STDOUT to your log while ignoring STDERR. As far as automated backups go, this is the uninteresting part. Really, you should only care if your backup failed. In the case of a failure, you're only mailing a user to tell them that it failed. You should be piping STDERR to your log using "2> log.file" so that when the user receives notification of the error, they can wander off to check the log and see exactly what the problem was (and fix, if need be).

2) With a mail daemon such as postfix (common on servers), STDOUT/STDERR from cron is automatically mailed to the owner of the job. When they log in (on the terminal) they'll receive a notice that they have new mail. If you redirect STDOUT to /dev/null and allow STDERR to be output, the user will not only receive notification of the error, but they'll have the cause right in front of them without having to dig through the log.  

3) The script is inflexible as far as defining multiple backup sources. Maintaining a backup for each source in my case would lead to a half dozen cron jobs. cp and rsync both provide functionality to specify multiple sources moving to a singular destination. By using a Bash array, you could easily allow a user to define this, and expand it appropriately in the execution.

4) Having multiple scripts to accomplish the same task (initial and incremental) is kludgy and you're replicating a lot of the same code. Consider creating functions to unify the common parts of the code and using command line arguments to let the user execute the same script with a different purpose. For bonus points, automatically determine if the backup to be run is an initial by detecting the presence of (or lack of) the destination.


Shameless self promotion: I've been working on my own little backup util called [SquashFu](http://github.com/falconindy/SquashFu) the past week or so. I'd been using an rsync-based solution previously but got weary (and bored) of the fact that it didn't provide the ability to do incrementals or compression. SquashFu does both, and I've been really happy with it so far.

---

### Post by llama320 on 2010-01-13
You might also consider rdiff-backup (as an alternative to rsync). It's a great little tool that's easy to set up and does incremental backups

[http://rdiff-backup.nongnu.org/](http://rdiff-backup.nongnu.org/)

---

### Post by toshko3 on 2010-01-22
Thanks for all replies but I find the "cp" the most reliable method for now. Moreover I want full backups every time. It was a "one night" solution and i hope it helps somebody. I'm sure it could be written more intelligently but I'm not a bash scripter :-). This is my second bigger script :D.
I didn't want to use tar, because i wanted the people to browse the backups when needed.
Falconindy, the 2> log.file didn't work. I don't know why. But anyway, THANKS FOR THE PROFESSIONAL TIPS! I appreciate them!

---

