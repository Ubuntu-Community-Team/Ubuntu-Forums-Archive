---
title: "Simple backup script solution with Rsync, logs and emails"
date: 2021-02-04
forum: Server Platforms
---

### Post by toshko3 on 2021-02-04
I searched for a backup bash script for Ubuntu/Linux to backup folders locally and remotely (from Linux or Windows), but didn't find any serious and up-to-date one. So, I wrote a script, which has the following features:

[LIST]
[*]Source and target could be local or remote, on Linux or Windows
[/LIST]
[LIST]
[*]Secure copying to/from remote locations, through SSH with keys, instead of passwords
[/LIST]
[LIST]
[*]Using rsync to copy/sync files with a one way direction (from source to target folder), ensuring only the changes are synced, saving traffic and data writes
[/LIST]
[LIST]
[*]Using rsync like this, also means we are "overwriting" the old backup every time we run this script. If you need multiple backup copies, you could schedule more copies of this script, every one at different time, configured with the same source, but different target.
[/LIST]
[LIST]
[*]Using sshfs to mount remote folders/partitions as source or target, no matter Linux or Windows (the machine running the script must be Ubuntu, but source or target could be Windows or Ubuntu)
[/LIST]
[LIST]
[*]
[*]Mail notifications. Uses s-nail to send email logs to Gmail (only Gmail supported)
[/LIST]
[LIST]
[*]Human readable log from every instance, deleting the last one.
[/LIST]
[LIST]
[*]Full verbose rsync log, so we could know what happened to every file
[/LIST]
[LIST]
[*]Pausing of scheduled execution if the last backup had any errors, so we could save if something was partially backed the last time and not damage it with new bad attempts (for example, when the source has bad sectors)
[/LIST]
[LIST]
[*]**The script works only when started by root user or root's crontab, tested on Ubuntu 18.04 and 20.04**
[/LIST]


**I wrote a Mini-HOWTO in the config file itself, so everyone could get up and running in no time. **

**1.** Just login with root and create a folder for every source you want to backup (for example, for the HDD partition mounted on /media/data, create a folder /root/scripts/backup/bypartition/data)
**2.** Create the files "backup.conf" and "backup.sh" there.
**3.** Copy the content from below to both of them.
**4.** Read the included Mini-HOWTO in "backup.conf" and set the requirements mentioned.
**5.** Set the variables in "backup.conf" and create a cronjob as mentioned in the Mini-HOWTO. All of the variables are well commented, so everyone could set them.
**6.** That's it! All the logs are created in the folder where the script is located.

**Release notes:**
```

ver6 - 2021.Feb.11
File backup.sh:
1. Changed date format to internationaly accepted standard - "date +%Y-%b-%d,%T"
2. Added job name in the Subject field of mails in "f_SendEmail" - "$(basename "$dir")"
3. Changed order in the Subject field of mails in "f_SendEmail" - Job result/status to be first for ease of reading when we have many emails with different jobs/servers
4. Added functionality at the beginning of the script to check if the first parameter (the config file) is given - "if [[ $1 ]]"
5. Addes functionality at the beginning of the script to check if "dir" variable is configured at all - "if [[ ! $dir ]]"
6. Added functionality to check if the config file version is compatible with the current version of the script - "if [[ ! $configver -eq $compatibleconfigver ]]". When developers change the version of the config file, they should change the value of "compatibleconfigver" variable in "backup.sh" to match the new version of config file.
7. Some comment changes.
File backup.conf:
1. Added "configver" variable, so the script could get the version number and check for compatibility.
2. Some comment changes.
All other variables are the same, so their values should just be copied if old config files are updated from ver5.

```

Please enjoy! :popcorn:
I hope the admins don't close this thread soon, so you could write me some feedback :)

**This is the "backup.conf" file:**
```

# ver6 - 2021.Feb.11
# When developers change the code of this config file, they should change the version in the "configver" variable.
# Tested on Ubuntu 18.04 and 20.04, only with root user.
#
#####################################################
#################### Description ####################
#####################################################
# This file (backup.conf) is the user configuration file. The other file (backup.sh) should not be edited by users.
#
# The backup script uses rsync for copying and syncing folders. It compares source and target, and syncs in direction - source to target.
# It copies only new/modified files and folders and deletes deleted ones. 
# This means that it creates an exact copy of the source folder, at the target folder.
# Be carefull to give an empty specially created folder as a target, because it will delete everything that doesn't match the source folder!
#
# Dependencies of the backup bash script:
# rsync - the software used for copying/syncing
# sshfs - when source or target is on remote server
# s-nail - for sending emails through Gmail
#
# This is a file with user configurable variables.
# If some variables are not used, they should not be commented, but should be leaved empty instead, like this: "variable=".
# The "backup.sh" script is tested only with root user, started by command or by cronjob. For example the umount command wants privileges.
# If you need to further develop the script don't change the variable names themselves, but keep them and create new ones if needed, so backward compatibility could be maintained.
# The whole backup script is realized by these 2 inseparable files, contained in the same specifically created folder:
# backup.conf - the file you're reading, human configurable, which is read/sourced by "backup.sh" for variable values.
# backup.sh - the script which is not supposed to be edited by users, so could be updated, without touching config file's values, in-place. This is the script that does the real job of backup.
# This script creates the following files directly in it's folder:
# backupSuccessValue.txt - value of 0 or 1 to check if the last backup is successfull. If it's not, the script doesn't run and sends a message to the user. When the problem is resolved, the user should manually replace the value of 1 to 0, so the script runs next time.
# backup010121,01:01:01.log - a human readable and meaningfull log file for every instance, which is sent by email, too. One current file is maintained and older ones deleted.
# RsyncProgram.log - The verbouse log of the rsync command, which could reach many megabytes. It sometimes contains precious file-by-file info, so we could know what exactly happened to every file.
# RsyncStartEnd.log - This is a file with only start and end dates of the rsync command. It is separate, because we're using verbouse option for the rsync command and the real log is very large. This is just for convenience of human reading.
# RsyncErrorsOnly.log - Only the errors of the rsync process, again, extracted for convenience of human reading.
# All of the above "Rsync..." log files are replaced on every rsync run and not preserved historically. If you need any, copy it to external folder, before the next script run.

#################### END Description ################


#####################################################
#################### mini-HOWTO #####################
#####################################################
# A small HOWTO for Ubuntu 18.04/20.04 with root user:
# 
# The script has only one source and one target. 
# However, you could create a separate copy of the script and config file and put them in another folder for multiple backup jobs. Then just start every copy with it's own command line in crontab.
# For the purpose of this mini-HOWTO, we are configuring one backup job, which you could repeat for every other backup job you want to create.
# Here, for example, we want to backup our whole data partition, mounted on /media/data to another dedicated partition, mounted on /media/backup-data.
# The script overwrites and deletes everything it sees in the target folder without asking, until it fully syncs with the source, so be carefull with the target folder.
# In this HOWTO, the target /media/backup-data partition is dedicated for this backup and has no files in it.
# 
# 0. Login with root user:
# su
# 1. Create a separate folder for the backup job of backing our whole data partition.
# mkdir -p /root/scripts/backup/bypartition/data
# 2. Copy "backup.conf" and "backup.sh" to the above folder.
# 3. This script uses only Gmail to send messages and the password is written here in plain text, so be sure to protect it with good permissions:
# chown root:root backup.sh && chmod u=rwx,go= backup.sh
# chown root:root backup.conf && chmod u=rw,go= backup.conf
# 4. The mailing functionality depends on s-nail. To install it:
# apt install s-nail
# You could test with the following command (replacing with your credentials) from command line, to be sure that the script will send emails successfully:
# echo test | s-nail -r "mail@gmail.com" -s "hostname,test,$(date +%d%m%y,%T)" -S smtp=smtp://smtp.gmail.com:587 -S smtp-use-starttls -S smtp-auth=login -S smtp-auth-user="mail@gmail.com" -S smtp-auth-password="mailpass" -S ssl-verify=ignore mail@gmail.com
# Be sure to have the Gmail setting for "Less secure apps" turned on, so standard SMTP works.
# You could create a separate Gmail address only for script emails, to be sure not to expose personal email password in this file, or enable less secure access on your personal email.
# 5. Config the variables in "backup.conf", keeping exactly the same format, given and explained at their comments.
# 6. You could start the backup in 2 ways:
# 6.1. Manually with root user: /root/scripts/backup/bypartition/data/backup.sh /root/scripts/backup/bypartition/data/backup.conf
# DO NOT WRITE "/" in the end of paths!!!
# Note, writing the full path of "backup.conf" is critical, so backup.sh could successfully read it's config file, especially in a cron job, where root's environment is not started and it cannot find it if given with relative path.
# 6.2. By cronjob of the root user: 
# For example, a cron file which starts one backup of the "data" partition at 1:00, every Monday:
# crontab -e 
# add the following line at the end of the file:
# 00 01 * * 1 /root/scripts/backup/bypartition/data/backup.sh /root/scripts/backup/bypartition/data/backup.conf
# DO NOT WRITE "/" in the end of paths!!!
# Again, the full paths are critical.
# 7. If the script could not complete the rsync job successfully, for any reason, it writes a "1" value in backupSuccessValue.txt.
# The next time it runs, it will check for this value and if it's still "1" (which means last backup was not successfull), it won't start the backup.
# So, to start the backup again, we should manually replace the first line "1" value to "0".
# This is for example, particularly usefull if the source has bad sectors and the backup has partially backed some files. The next time they may not be readable and if the backup starts again, it could damage the healthy ones.


# Additional HOWTO:
# 1. The remote source and target functionality depends on sshfs, and pre-configuration of SSH to login automatically to remote servers with keys, without asking for password. You could accomplish this by doing:
# Login with root user:
# su 
# Install sshfs:
# apt install sshfs
# Create a private and public key pair for your root user, if you don't have one already:
# mkdir ~/.ssh && chmod 700 ~/.ssh && ssh-keygen -t rsa -b 4096  (just press Enter for defaults)
# Copy public key to remote server for automatic login. Works only if remote server is Linux. If it's Windows, you should add your public key manually to the Windows machine (/root/.ssh/id_rsa.pub):
# ssh-copy-id root@office.example.com

############### END mini-HOWTO ######################


#####################################################
############### Only for developers #################
#####################################################
#Version of this config file, so the script could check for compatibility
#This value should be updated +1 for every change in code (not values).
#When this value is changed, it should also be changed in the "compatibleconfigver" variable in "backup.sh"
configver=6
############### END Only for developers #############




#####################################################
############### User configuration ##################
#####################################################

############### Script location ###############
#Where am I located 
#Current path which your script resides in, so that the logs could be accessed and created. Otherwise the cronjob will put/search all the files within the user's (by which the cron is ran) home dir. 
#Value format:
#Do not put "/" in the end of the target dir, because it will be doubled in the script commands.
#Linux: /root/scripts/backup/bypartition/data
dir=


############### Backup values ###############
#Backup source / Remote source mount point
#If backup source is a local folder, write it here.
#If it's on a remote server, write the mount point here. The mount point should have been CREATED ALREADY MANUALLY for the script to work.
#This way the script will mount the remote source on this locally created mount point through sshfs and the other script commands will see no difference.
#Value format:
#Do not put "/" in the end of the target dir, because it will be doubled in the script commands.
#Linux: /media/data
#Linux remote folder: /media/data (The same, because this will be the mount point of the remote folder)
#Windows remote folder: /media/data (The same, because this will be the mount point of the remote folder)
b_source=

#Backup source if it's on remote server
#YOU SHOULD HAVE SET UP AUTO KEY LOGGING FOR SSH TO THE REMOTE SERVER, and tested it with the user you are running this script (only root for now), using a command like "ssh root@office.example.com". It should connect automatically without asking for password before running this script.
#Value format:
#Do not put "/" in the end of the target dir, because it will be doubled in the script commands.
#Linux remote source: root@office.example.com:/media/data
#Windows remote source: user@office.example.com:D:\\data (using double slash, one of which is interpreted as "escape character" by bash) 
#If source is not remote leave the value blank, but don't delete the variable (leave it like this: "b_source_remote=")!!!
b_source_remote=

#SSH port of backup source if it's on remote server
#Value format: 22
#If source is not remote leave the value blank, but don't delete the variable (leave it like this: "r_s_port=")!!!
r_s_port=

#Backup target / Remtoe target mount point
#Be carefull to give an empty specially created folder as a target, because the script will delete everything that doesn't match the source!
#If backup target is a local folder, write it here.
#If it's on a remote server, write the mount point here. The mount point should have been CREATED ALREADY MANUALLY for the script to work.
#This way the script will mount the remote target on this locally created mount point through sshfs and the other commands will see no difference.
#Value format:
#Do not put "/" in the end of the target dir, because it will be doubled in the script commands.
#Linux: /media/backup-data
#Linux remote folder: /media/backup-data (The same, because this will be the mount point of the remote folder)
#Windows remote folder: /media/backup-data (The same, because this will be the mount point of the remote folder)
b_target_user=

#Backup target if it's on remote server
#Be carefull to give an empty specially created folder as a target, because the script will delete everything that doesn't match the source!
#YOU SHOULD HAVE SET UP AUTO KEY LOGGING FOR SSH TO THE REMOTE SERVER, and tested it with the user you are running this script (only root for now), using a command like "ssh root@office.example.com". It should connect automatically without asking for password before running this script.
#Value format:
#Do not put "/" in the end of the target dir, because it will be doubled in the script commands.
#Linux remote target: root@office.example.com:/media/backup-data
#Windows remote target: user@office.example.com:D:\\backup-data (using double slash, one of which is interpreted as "escape character" by bash)
#If target is not remote leave the value blank, but don't delete the variable (leave it like this: "b_target_remote=")!!!
b_target_remote=

#SSH port of backup target if it's on remote server
#Value format: 22
#If target is not remote leave the value blank, but don't delete the variable (leave it like this: "r_t_port=")!!!
r_t_port=


############### Email notifications ###############
#Email address for logs to be sent 
#For emails to be sent, there must be a mail agent installed, configured and tested, working with the "s-nail" command. (for more info, look at the mini-HOWTO above)
#This script uses only gmail.com and uses the same email address for sender and receiver, so the mails never get to the spam folder.
#Value format: example@gmail.com
mailaddress=

#Email user, (we are using Gmail, without us being a mail server, although you still need postfix, it just uses an external mail server)
#Value format: example@gmail.com
mailuser=

#Email pass
#Value format: examplepass
mailpass=


```


**And this is the "backup.sh" script:**
```

#!/bin/bash
# ver6 - 2021.Feb.11 - this version is working on Ubuntu 18.04, 20.04, only with root user.
# Users should not touch this file. All of the user configuration is made in "backup.conf".
# If developers update the code of config file, they should update the "compatibleconfigver" valule here to match the new config file version.
# The whole backup script is realized with 2 files, which should be placed in one folder, specifically created for the backup task:
# backup.conf - human configurable, which is read/sourced by this script (backup.sh) for variable values.
# backup.sh - the file you're reading, not supposed to be edited by users, so could be updated, without touching config file's values, in-place. This is the script that does the real job of backup.

##############################################################################
######### DEVELOPER MUST DEFINE THIS ON EVERY UPDATE OF CONFIG FILE ##########
##############################################################################
# When config file version is updated, the new version should be written here. If only this script is updated and there is no change in config file's code, leave the current value.
# This way, if user updates only this script and it is not compatible with his older config, the script would not start.
compatibleconfigver=6
######### END ################################################################


######### Check for prerequisites #########
# Take the config file, given as first parameter, when running this script
# Also, check if there is any config file, given as the first parameter to the script
if [[ $1 ]]; then
        configfile=$1
else
        echo "Error: There is no config file, given as first parameter to this script. Please, start the script with this exact syntax:"
        echo "/full/path/to/script/backup.sh /full/path/to/configfile/backup.conf"
        echo "DO NOT PUT backslash on the end of paths, because it will be doubled in the script!!!"
        echo "Note, the script and config file should be at the same new directory, specifically created for the script job."
        exit
fi
# Source config file for all variables, including it's version
source "$configfile"
# Check if dir variable is configured, so we could write logs. If not, exit script and warn user on console.
if [[ ! $dir ]]; then
        echo "Error: There is no dir value defined, the script could not run without it. EXITING."
        exit
fi
# Create a log file value for later creation and check if there is older one for later deletion
log=backup$(date +%Y-%b-%d,%T).log
                if find "$dir" -type f -name "backup*.log" | grep . ; then # We are using "grep ." here, because find doesn't change it's exit code of 0 if it doesn't find anything.
                        oldestlog=$(ls -tad "$dir"/backup*.log | tail -1 | head -1)
                        echo "$(date +%Y-%b-%d,%T) There is/are older logs, the oldest one will be deleted if rsync is successfull!"
                else
                        echo "$(date +%Y-%b-%d,%T) There is no older log, assuming this is the first time you are running this script!"
                fi
# Check config file version for compatibility
if [[ ! $configver -eq $compatibleconfigver ]]; then
        echo "$(date +%Y-%b-%d,%T) Error: The config file is not compatible with this version of the script. Please, update the config file and don't forget to configure the variables according to their new comments. EXITING." >> "$dir"/$log
        exit
fi

######### Values not to be touched ###############
# Get some values from system permanently for the current script run
host=$(hostname)
date=$(date +%Y-%b-%d,%T)

# When the source is /, i.e. the root partition, the script cannot create the / directory with the name of "/" in b_target_user. So it creates all the files/folders of / directly in b_target_user.
# This creates an exception, because otherwise rsync creates a folder within b_target, with the name of source's folder.
# So, we create a folder in the target, with the name "root_partition" and modify the target to be not b_target_user, but "b_target_user/root_partition".
# But first, we ensure that the $b_target_remote_rsync var which is used only in the rsync command is equal to the user provided $b_target_remote, if it is set at all.
if [[ $b_target_remote ]]; then
        b_target_remote_rsync="$b_target_remote"
fi
if [ "$b_source" == "/" ]; then
        b_target="$b_target_user"/root_partition
        if [[ $b_target_remote ]]; then
                b_target_remote_rsync="$b_target_remote_rsync"/root_partition
        fi
else
        b_target="$b_target_user"
fi

# Function to send email to yourself through your own Gmail. Sending from your email to the same email, so no chance for Gmail to mark it as a spam.
# Ext. parameters given to this function in order:
# 1 - The message part of the subject - MUST BE ALWAYS with no intervals (the rest is always the same - hostname, date, etc.)
function f_SendEmail {
        cat "$dir"/$log | s-nail -r "$mailaddress" -s "$1,$host,$(basename "$dir"),$(date +%Y-%b-%d,%T)" -S smtp=smtp://smtp.gmail.com:587 -S smtp-use-starttls -S smtp-auth=login -S smtp-auth-user="$mailuser" -S smtp-auth-password="$mailpass" -S ssl-verify=ignore $mailaddress 2>> "$dir"/$log ; echo "Sent mail to $mailaddress" >> "$dir"/$log
}

# Function to write the value of the backupSuccessValue.txt file. The file serves to stop the script from running if the last backup wasn't successfull, until the admin fixes the problem. The purpose of this is to save what has been backed up and not try to write on it again. It is very usefull for example when a backup source has bad sectors, which could have caused some errors. If we try to run it again it could be worse and wipe the partially successfull backup from the last time.
# Ext. parameters given to this function in order:
# 1 - the value which we want to write to the first line in the backupSuccessValue.txt file. This is the line the script reads to know if it should continue or stop. The rest is comments for the user.
function f_WriteBackupSuccessValue {
        echo $1 > "$dir"/backupSuccessValue.txt
        echo "$(date)" >> "$dir"/backupSuccessValue.txt
        echo "When the first line value is 0 - the script has completed successfully and could be started again." >> "$dir"/backupSuccessValue.txt
        echo "When the first line value is 1 - the script has exitted due to an error and it WILL NOT BE STARTED AGAIN, until you resolve the problem and modify this value to 0 manually." >> "$dir"/backupSuccessValue.txt
}


######### The real job ##########
echo "$(date +%Y-%b-%d,%T) To see the log of this script, use tail -f "$dir"/$log"

# If the script is started for the first time, write a backupSuccessValue.txt file with a 0 value, so the script starts normally.
if [[ ! -e "$dir"/backupSuccessValue.txt ]] ; then
        echo "$(date +%Y-%b-%d,%T) The file: backupSuccessValue.txt is missing. Assuming this is the first time you run this script!" >> "$dir"/$log
        f_WriteBackupSuccessValue 0
fi

# Check for previous success of backup. If it didn't finish successfully - backup will not be executed. Otherwise start the real job.
if [ "$(head -1 "$dir"/backupSuccessValue.txt)" = "0" ]; then
        f_WriteBackupSuccessValue 1
        echo "$(date +%Y-%b-%d,%T): Backup started but not ended yet." >> "$dir"/backupSuccessValue.txt
        echo "If you see this message and the script is not running, then it is most probably interrupted by something (power failure?)." >> "$dir"/backupSuccessValue.txt
        echo "You can force it to run by overwriting the first line "1" value to "0" and run it again." >> "$dir"/backupSuccessValue.txt
        # Mount the backup source READ-ONLY if it is remote. For safety reasons, to be sure that the source is not changed (for example with NTFS file system).
        if [[ $b_source_remote ]]; then
                echo "$(date +%Y-%b-%d,%T) Trying to: mount "$b_source_remote" to "$b_source"" >> "$dir"/$log
                if ! mountpoint -q "$b_source" 2>> "$dir"/$log ; then # Check if the folder is not already a mountpoint of a currently mounted device.
                        sshfs -o ro -p $r_s_port "$b_source_remote" "$b_source" 2>> "$dir"/$log
                        if [ "$?" = "0" ]; then
                                echo "$(date +%Y-%b-%d,%T) Succeeded: mount "$b_source_remote" to "$b_source"" >> "$dir"/$log
                        else
                                f_WriteBackupSuccessValue 1
                                echo "$(date +%Y-%b-%d,%T) Error: mount "$b_source_remote" to "$b_source". EXITING." >> "$dir"/$log
                                f_SendEmail MountOfRemoteBackupSourceFailed
                                exit
                        fi
                else
                        f_WriteBackupSuccessValue 1
                        echo "$(date +%Y-%b-%d,%T) Error: mount "$b_source_remote" to "$b_source". "$b_source" is already a mountpoint of a currently mounted device. EXITING." >> "$dir"/$log
                        f_SendEmail MountOfRemoteBackupSourceFailed
                        exit
                fi
        fi
        # Mount the backup target if it is remote.
        if [[ $b_target_remote ]]; then
                echo "$(date +%Y-%b-%d,%T) Trying to: mount "$b_target_remote" to "$b_target_user"" >> "$dir"/$log
                if ! mountpoint -q "$b_target_user" 2>> "$dir"/$log ; then # Check if the folder is not already a mountpoint of a currently mounted device.
                        sshfs -p $r_t_port "$b_target_remote" "$b_target_user" 2>> "$dir"/$log
                        if [ "$?" = "0" ]; then
                                echo "$(date +%Y-%b-%d,%T) Succeeded: mount "$b_target_remote" to "$b_target_user"" >> "$dir"/$log
                        else
                                f_WriteBackupSuccessValue 1
                                echo "$(date +%Y-%b-%d,%T) Error: mount "$b_target_remote" to "$b_target_user". EXITING." >> "$dir"/$log
                                f_SendEmail MountOfRemoteBackupTargetFailed
                                exit
                        fi
                else
                        f_WriteBackupSuccessValue 1
                        echo "$(date +%Y-%b-%d,%T) Error: mount "$b_target_remote" to "$b_target". "$b_target" is already a mountpoint of a currently mounted device. EXITING." >> "$dir"/$log
                        f_SendEmail MountOfRemoteBackupTargetFailed
                        exit
                fi
        fi
        # Check if backup source and target folders exist, to avoid the case when this script is started for the first time and the user forgot to create/mount the folder. In this case rsync creates it for itself, but the user may not want this. For example if the target is supposed to be on another HDD or remote folder, which we want to mount to the b_target_user folder and forgot to do so, rsync just creates the folder in the current path, like /media/backup-data and starts to write into it, which results in most cases in writing into the root filesystem. It is dangerous because it could overflow the root filesystem.
        echo "$(date +%Y-%b-%d,%T) Trying to: validate that "$b_source" and "$b_target_user" exist and have reading rights" >> "$dir"/$log
        if ! ls "$b_source" "$b_target_user" 2>> "$dir"/$log ; then
                f_WriteBackupSuccessValue 1
                echo "$(date +%Y-%b-%d,%T) Error: validate that "$b_source" and "$b_target_user" exist and have reading rights. Please unmount manually if anything is mounted by this script (written above in this log). EXITING." >> "$dir"/$log
                f_SendEmail SourceOrTargetIsMissing
                exit
        else
                echo "$(date +%Y-%b-%d,%T) Succeeded: validate that "$b_source" and "$b_target_user" exist and have reading rights" >> "$dir"/$log
        fi
        if [[ -e "$dir"/RsyncProgram.log ]] ; then
                rm "$dir"/RsyncProgram.log
        fi
        if [[ -e "$dir"/RsyncErrorsOnly.log ]] ; then
                rm "$dir"/RsyncErrorsOnly.log
        fi
        date > "$dir"/RsyncStartEnd.log
        # Sync the source and target with rsync. If the target is on remote server the rsync command is different because rsync produces errors like "rsync: failed to set times on No such file or directory" on symlinks, which are pointing to targets, not backed up (like /dev/...), because we don't want them. This occurs mainly on Root filesystem backups. So the rsync command is directly syncing between hosts, but still mounting the remote filesystem with sshfs. Mounting is the easiest way, so all the commands are still valid when the backup target is remote linux server through ssh (for example "du").
        if [[ $b_target_remote ]]; then
                # Check source and target folder sizes before backup (and later - after the backup) to additionally compare for additional safety.
                echo "$(date +%Y-%b-%d,%T) Source and target sizes before rsync:" >> "$dir"/$log
                du -shx "$b_source" "$b_target" >> "$dir"/$log
                echo "$(date +%Y-%b-%d,%T) Trying to: rsync "$b_source" to "$b_target_remote_rsync"" >> "$dir"/$log
                rsync -aHWxh --no-specials --no-devices --progress --delete-during -e "ssh -p $r_t_port" --log-file="$dir"/RsyncProgram.log "$b_source" "$b_target_remote_rsync" 2>> "$dir"/RsyncErrorsOnly.log
        else
                # Check source and target folder sizes before backup (and later - after the backup) to additionally compare for additional safety.
                echo "$(date +%Y-%b-%d,%T) Source and target sizes before rsync:" >> "$dir"/$log
                du -shx "$b_source" "$b_target" >> "$dir"/$log
                echo "$(date +%Y-%b-%d,%T) Trying to: rsync "$b_source" "$b_target"" >> "$dir"/$log
                rsync -aHWxh --no-specials --no-devices --progress --delete-during --log-file="$dir"/RsyncProgram.log "$b_source" "$b_target" 2>> "$dir"/RsyncErrorsOnly.log
        fi
        # Check if rsync completed successfully.
        if [ "$?" = "0" ]; then
                date >> "$dir"/RsyncStartEnd.log
                # Write success value 0 to the backupSuccessValue.txt file, because the backup finished successfully, no matter if we could unmount the remote folders later, or not.
                f_WriteBackupSuccessValue 0
                echo "$(date +%Y-%b-%d,%T) Succeeded: rsync" >> "$dir"/$log
                # Now that the backup is finished successfully we can remove the older log.
                if [[ -e "$oldestlog" ]] ; then
                        echo "$(date +%Y-%b-%d,%T) Trying to: rm "$oldestlog"" >> "$dir"/$log
                        rm "$oldestlog" 2>> "$dir"/$log
                        if [ "$?" = "0" ]; then
                                echo "$(date +%Y-%b-%d,%T) Succeeded: rm "$oldestlog"" >> "$dir"/$log
                        else
                                echo "$(date +%Y-%b-%d,%T) Error: rm "$oldestlog"" >> "$dir"/$log
                                f_SendEmail RemovalOfOldestLogFailed
                        fi
                fi
                # Verify with rsync's integrated dry-run after the real rsync. If source is root partition, skip verification because it's not so important, but will produce long logs with skipping special files and so on, overloading regular mail notifications.
                if [[ "$b_source" == "/" ]] ; then
                        echo "$(date +%Y-%b-%d,%T) Skipping rsync verification with dry-run, because source is root partition." >> "$dir"/$log
                else
                        echo "$(date +%Y-%b-%d,%T) Verification with dry-run after real rsync:" >> "$dir"/$log
                        echo "                Files not synced:" >> "$dir"/$log
                        rsync -niaHWxh --no-specials --no-devices --progress --delete-during "$b_source"/ "$b_target"/$(basename "$b_source")/ >> "$dir"/$log
                        echo "                End." >> "$dir"/$log
                        echo "                If there are no listed files, rsync has done it's job successfuly. Otherwise the files shown are not synced." >> "$dir"/$log
                fi
                # Check again source and target folder sizes to additionally compare for additional safety.
                echo "$(date +%Y-%b-%d,%T) Source and target sizes after rsync:" >> "$dir"/$log
                du -shx "$b_source" "$b_target" >> "$dir"/$log
                # Unmount the source folder if it's remote.
                if [ "$b_source_remote" ]; then
                        echo "$(date +%Y-%b-%d,%T) Trying to: umount -f "$b_source_remote"" >> "$dir"/$log
                        umount -f "$b_source_remote" 2>> "$dir"/$log
                        if [ "$?" = "0" ]; then
                                echo "$(date +%Y-%b-%d,%T) Succeeded: umount -f "$b_source_remote"" >> "$dir"/$log
                        else
                                echo "$(date +%Y-%b-%d,%T) Error: umount -f "$b_source_remote"" >> "$dir"/$log
                                f_SendEmail UmountOfRemoteSourceFailed
                        fi
                fi
                # Unmount the target folder if it's remote.
                if [ "$b_target_remote" ]; then
                        echo "$(date +%Y-%b-%d,%T) Trying to: umount -f "$b_target_remote"" >> "$dir"/$log
                        umount -f "$b_target_remote" 2>> "$dir"/$log
                        if [ "$?" = "0" ]; then
                                echo "$(date +%Y-%b-%d,%T) Succeeded: umount -f "$b_target_remote"" >> "$dir"/$log
                        else
                                echo "$(date +%Y-%b-%d,%T) Error: umount -f "$b_target_remote"" >> "$dir"/$log
                                f_SendEmail UmountOfRemoteTargetFailed
                        fi
                fi
                # Send email with the log and subject that it's finished OK.
                f_SendEmail BackupOK
        else
                # If anything has gone wrong with the rsync command (respectively the sync process), write a value of 1 in backupSuccessValue.txt file and send email with the log and subject that the backup failed.
                f_WriteBackupSuccessValue 1
                echo "$(date +%Y-%b-%d,%T) Error: rsync" >> "$dir"/$log
                echo "Look at "$dir"/RsyncProgram.log, "$dir"/RsyncErrorsOnly.log and "$dir"/RsyncStartEnd.log for more info!" >> "$dir"/$log
                echo "Fatal error! Ending script!" >> "$dir"/$log
                f_SendEmail BackupFailed
        fi
        echo "$(date +%Y-%b-%d,%T) Finished script!" >> "$dir"/$log
else
        # If the previous backup is not successfull, we don't want to run this script. Send email that nothing will be done, so the admin could check what's wrong and if anything is backed successfully the last time.
        echo "$(date +%Y-%b-%d,%T) Error: The previous backup is not successful" >> "$dir"/$log
        echo "For more info look at "$dir"/backupSuccessValue.txt" >> "$dir"/$log
        echo "Ending script - nothing will be done" >> "$dir"/$log
        echo "THE SCRIPT HAS NOT STARTED THIS TIME AND WILL NOT BE STARTED THE NEXT TIME, until you resolve the problem and change the first line value of backupSuccessValue.txt file to 0 manually!!!" >> "$dir"/$log
        f_SendEmail BackupDidNotStart
fi

exit

```

---

### Post by LHammonds on 2021-02-04
Awesome.  Thanks for creating and sharing.

I keep my scripts on [github]("https://github.com/LHammonds/ubuntu-bash") which allows me to see the various incantations and versions over time...such as how my script worked on Ubuntu 16.04 vs how it works on Ubuntu 20.04, etc.

LHammonds

---

### Post by toshko3 on 2021-02-04
I don't have an account there, but I should consider putting it there.

---

### Post by #&amp;thj^% on 2021-02-04
> **toshko3 said:**
> I don't have an account there, but I should consider putting it there.

+1
Nice Share! :)

---

