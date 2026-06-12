---
title: "Shell Script Help for backing up data"
date: 2009-08-07
forum: Server Platforms
---

### Post by rbishop on 2009-08-07
Hello all,

I need some help setting up a shell script.  I am trying to setup a shell script to take a folder and write the contents to a CD/DVD and then delete the contents of the folder.  I have a couple of cron jobs setup to run  backing up certain files to this one folder.  

Thanks in advance for any help/suggestions.

---

### Post by jordilin on 2009-08-07
There are apps already in the repos that do that like mondorescue. If you have a doubt about that shell script, show it here or ask that in the programming section.

---

### Post by rbishop on 2009-08-17
Well here I am back again.....This time I have to say that I have been able to come up with a script to accomplish this small challenge.  Here is the script I wrote, please use/change it to fit your needs.

```



# Backup Script by me

TD=$(date '+%m-%d-%y')
FILE="$TD.iso"


#Making database folder and moving SQL tables into it.
mkdir /backups/database
mv /backups/*.sql /backups/database
zip -r /backups/database.zip /backups/database

# Making Nagios folder and moving all of the files into it.
mkdir /backups/nagios
cp -r /usr/local/share/nagios/etc/*.* /backups/nagios
mv /backups/NC /backups/nagios/
mv /backups/NR /backups/nagios/
zip -r /backups/nagios.zip /backups/nagios

# Making Virtual Machine Backups
mkdir /backups/DNS-Server
cp -r /var/lib/vmware/Virtual\ Machines/DNS-Server/* /backups/DNS-Server
zip -r /backups/DNS-Server.zip /backups/DNS-Server

mkdir /backups/WinXP
cp -r /iso/Windows\ XP/* /backups/WinXP
zip -r /backups/WinXP.zip /backups/WinXP

mkdir /backups/TrixBox
cp -r /home/files/isos/TrixBox/* /backups/TrixBox
zip -r /backups/TrixBox.zip /backups/TrixBox

mkdir /backups/Xandros
cp -r /iso/Xandros/* /backups/Xandros
zip -r /backups/Xandros.zip /backups/Xandros

# Remove VM Folders
rm -fr /backups/WinXP /backups/DNS-Server /backups/TrixBox /backups/Xandros /backups/nagios

# Make DVD ISO
mkisofs -o /backups/$FILE -r -J /backups

# Recording DVD
cdrecord -v -pad speed=1 dev=6,0,0 /backups/$FILE

# Removing all files
rm -fr /backups/*



```What you end up with is a CD/DVD with the label of the day(ie 081709) and a disc containing zips of all the files I need backed up.  The script makes all the zip files, makes the disc iso, burns the disc and then wipes the folder clean for the next days backup.

---

