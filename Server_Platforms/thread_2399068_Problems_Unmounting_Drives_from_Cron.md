---
title: "Problems Unmounting Drives from Cron"
date: 2018-08-21
forum: Server Platforms
---

### Post by damo12 on 2018-08-21
Hi,

Overnight I run a bash script which carried out a number of backups to internal drives and Google Drive (using [Rclone]("https://rclone.org/")) and once each week to external USB drives.

The script works perfectly until the last stage when I am trying to unmount the backup drives.

The internal drives are called "*media_backup*" and "*server_backup*" and the USB drives are called "*usb_media_backup*" and "*usb_server_backup*".

At the start of the script, the internal drives are mounted using the command:
```
sleep 5m
mount /media/media_backup
sleep 5m
mount /media/server_backup
```


Once the internal backups have been completed the script checks the day of the week giving the day the variable "*$DOW*".  If it is a Sunday, the USB drives are mounted using the command:
```
sleep 5m
mount /mnt/usb_media_backup
sleep 5m
mount /mnt/usb_server_backup
```


Once all backups are complete (regardless of the day of the week), the script runs the command:
```
sleep 5m
umount /mnt/usb_media_backup
sleep 5m
umount /mnt/usb_server_backup
sleep 5m
umount /media/media_backup
sleep 5m
umount /media/server_backup
```


Sometimes one or both of the USB drives unmount but there is no consistency to this and the internal drives rarely if ever unmount.

Throughout the backup, the script outputs to a log file so I can check the progress and examine any errors.  The log shows that all backups have completed before the script progresses to the unmount section.  I have tried outputting the section to the log by amending this section to:
```
sleep 5m
umount /mnt/usb_media_backup >> /media/backup_log/"$DOW"/backup.log
sleep 5m
umount /mnt/usb_server_backup >> /media/backup_log/"$DOW"/backup.log
sleep 5m
umount /media/media_backup >> /media/backup_log/"$DOW"/backup.log
sleep 5m
umount /media/server_backup >> /media/backup_log/"$DOW"/backup.log
```


However the log remains empty for this section.

I would be grateful if anyone can show me where I am going wrong

---

### Post by LHammonds on 2018-08-21
Are you absolutely sure backups are not continuing at the time you try to unmount?  Check for and document the return code of your backup command in your log file.  You could also get the process ID and make sure it is not running before continuing the next step.

Run a "sync" command before the umount to make sure all cached writes are flushed before trying to unmount.

You are not capturing any return codes when you issue the umount command.  Capture the return code and print that to the error log.  Example:

```

umount /mnt/usb_media_backup >> /media/backup_log/${DOW}/backup.log
ReturnCode=$?
printf "Unmount USB return code: ${ReturnCode}" >> /media/backup_log/${DOW}/backup.log

```

On a side note, when extracting data from variables, it would be better to be in the habit of doing it this way ([reference]("https://stackoverflow.com/questions/8748831/when-do-we-need-curly-braces-around-shell-variables")):

```
>> /media/backup_log/${DOW}/backup.log
```

I would also simply my code a bit more by creating a "LogFile" variable at the top and just reference that everywhere to cut down on potential typos and reduce the places you need to change if your path needs to be updated.  Example:
```

DOW="Sunday"
LogFile = "/media/backup_log/${DOW}/backup.log"
printf "Script Start" >> ${LogFile}
printf "Script End" >> ${LogFile}

```

You also do not specify the full path to "umount" so it relies on the path variable to find the program.  Crontab's reduced environment does not have a path variable (usually) so I assume you are setting one.  To avoid any potential change of location, you could include the full path to the umount command in the script.  But I don't think that is related to your current issue.

LHammonds

---

### Post by damo12 on 2018-08-21
Hi LHammonds,

Thank you for your suggestions.  I'll amend my code accordingly.  I have no training in coding so the code is formed from forums and Google searches.

I'm quite sure that the backups have finished.  When the backup finishes it writes to the log file and sends an email.  I left it out of the original post for brevity but the script for one backup is:
```
echo >> /media/backup_log/"$DOW"/backup.log
echo >> /media/backup_log/"$DOW"/backup.log
echo >> /media/backup_log/"$DOW"/backup.log
echo >> /media/backup_log/"$DOW"/backup.log
echo "****************************************" >> /media/backup_log/"$DOW"/backup.log
echo "Checking USB Media drive is mounted" $(date +"%A %d %B %Y %R")  >> /media/backup_log/"$DOW"/backup.log
echo "****************************************" >> /media/backup_log/"$DOW"/backup.log
echo >> /media/backup_log/"$DOW"/backup.log
#
	if [ -f /mnt/usb_media_backup/media_usb_chk_first.1st ] ; then

sendEmail -f "server_email_address" -t "my_email_address" -u "Failed backup" -m "The weekly USB media backup has failed" -s "SMTP_server" -xu "server_email_address" -xp "email_password"
else
echo >> /media/backup_log/"$DOW"/backup.log
echo "****************************************" >> /media/backup_log/"$DOW"/backup.log
echo "Running USB Media backup" $(date +"%A %d %B %Y %R")  >> /media/backup_log/"$DOW"/backup.log
echo "****************************************" >> /media/backup_log/"$DOW"/backup.log
echo >> /media/backup_log/"$DOW"/backup.log
#
	rsync -av /media/media_backup/ /mnt/usb_media_backup/ >>/media/backup_log/"$DOW"/backup.log 2>&1
  
sendEmail -o tls=yes -f "server_email_address" -t "my_email_address" -u "Weekly USB Media Backup Completed" -m "The weekly USB media backup has completed" -s "SMTP_server" -xu "server_email_address" -xp "email_password"
fi

echo "****************************************" >> /media/backup_log/"$DOW"/backup.log
echo "Media backup completed" $(date +"%A %d %B %Y %R")  >> /media/backup_log/"$DOW"/backup.log
echo "****************************************" >> /media/backup_log/"$DOW"/backup.log
echo >> /media/backup_log/"$DOW"/backup.log
```


Each backup follows the same pattern with updates to the log file and an email sent on completion.  I know that this is quite a long winded pattern but it makes the logs easy to read, especially when there have been a large number of changes.

I have added your lines to return the code from unmount command to the log and will see what that produces tonight.

Please forgive my ignorance but when you mention the full path to "umount" are you referring to the path of the drive or the command itself?  The drives are mapped in fstab using the UUID of each drive but I did not know that umount had a path.

Thanks,

---

### Post by SeijiSensei on 2018-08-21
You cannot unmount a device if it has open files or you are in a directory on the device when trying to unmount. Add the command 

```
lsof > /media/backup_log/open-file-list
```

You can use "grep" to find specific entries like this:

```
grep media_backup /media/backup_log/open-file-list
```

to find lines with "media_backup" in them. Repeat the procedure for the other mounted devices.

---

### Post by LHammonds on 2018-08-21
> **damo12 said:**
> when you mention the full path to "umount" are you referring to the path of the drive or the command itself?  The drives are mapped in fstab using the UUID of each drive but I did not know that umount had a path.
When you type the following:
```
which umount
```
It should give you the full path to the umount program.  Example:
```
/bin/umount
```

To ensure your script calls the same "umount" program no matter how many other "umount" programs exist on your system or in your search path, you can add the full path to the command in your script and rest assured it will call the same program every time.  This can also mitigate security issues with malicious copies of the same-named program being called from other locations.  Although, you can specify the search path/order in your scripts as well.

LHammonds

---

### Post by damo12 on 2018-08-21
Thanks SeijiSensei and LHammonds,

I have added the "grep" line to the backup and changed the USB backup day meaning that all will backups will run tonight.

I have also amended the "*umount*" to show the full path.

Fingers crossed, that will do the trick but I will report back either way tomorrow.

---

### Post by LHammonds on 2018-08-21
It will still likely fail tonight.  Our suggestions were to help you troubleshoot the "why" it is failing.  The only "corrective" action I suggested that might help with the dismount is the "sync" command but that is just a shot in the dark.  The additional changes to the script will help you resolve what is happening at the time the script is running.

I assume you can manually mount and dismount the USB with those commands without any problem (multiple times in a row)?

LHammonds

---

### Post by damo12 on 2018-08-21
Thanks LHammonds,

The drives will mount and dismount repeatedly without any problems when I run the commands through PuTTY.

Hopefully the logs will point me in the right direction but with regards to your "sync" suggestion, am I right in thinking that the code for that would be:
```
sync /media/media_backup
```


Thanks

---

### Post by LHammonds on 2018-08-21
> **damo12 said:**
> with regards to your "sync" suggestion, am I right in thinking that the code for that would be:
```
sync /media/media_backup
```
No, just run the sync command without any options.  If you specify file options, it will limit the sync to just those files and I'm willing to bet your backup is more than just 1 file being written.

You might even want to put a pause in there to give it time to work.  But running sync should not take very long to execute.

Example:
```
/bin/sync
/bin/sleep 15s
```

If your log shows files open on the USB drive tomorrow, you can add specific search checks using lsof and grep to look for and handle the case when files are open on the USB drive.

However, if files are open, you need to figure out what process is running that keeps them open....such as your backup job saying it completed but not letting go of the files.  If the backup is not letting go of the file, you could get the process ID (PID) and kill it.  However, that is not fixing the source of the problem.

Best to see what the problem is rather than speculate at this point.

LHammonds

---

### Post by damo12 on 2018-08-22
The backups ran last night without an issue however the drives remained mounted.  The return codes on the log were:
```
Unmount USB Media Backup return code: 0Unmount USB Server Backup return code: 32Unmount Media Backup return code: 0Unmount Server Backup return code: 0
```

Although USB server backup is showing a return code of "32", the "Open File Log" did not show any files open.

I have added the lines:
```
/bin/sync
/bin/sleep 15s
```


and have manually set the script running this morning.  Due to the size of the script and the number of "sleep" commands, it will take a few hours to run.  I'll report back later

---

### Post by damo12 on 2018-08-22
Hi,

Just want to say that this is now working fine.  I had a few issues but that was due to typing errors on my side.

Thanks again for all of your help

---

