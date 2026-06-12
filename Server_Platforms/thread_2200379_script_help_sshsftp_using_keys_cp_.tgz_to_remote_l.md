---
title: "script help ssh/sftp using keys cp *.tgz to remote location"
date: 2014-01-19
forum: Server Platforms
---

### Post by chadk5utc on 2014-01-19
Hello 
I am having some trouble scripting a task. I currently have backup script running at remote locations. I am now trying to send only the newest *.tgz files from its output directories and send them to remote server using ssh/sftp with keys. The filenames are like so M_Saturday.tgz, C_Monday.tgz Etc first letter reference the machine then the day of the week. Below is the script Im using.

```
#!/bin/bash

# NAS Remote Backup sript #

red='\e[0;31m'
green='\e[0;32m'
nocol='\e[0m'

### Options: ###

n=$(date --date= +%A)
mess=/var/log/remotebackup.mess

#server directory
dir=/home/jail/d1/lab

m=192.168.4.40
muser=user
mdir=m

pc1=192.168.4.41
pc1user=useruser
pc1dir=pc1

s=192.168.4.42
suser=sitecon
sdir=s

c=192.168.4.43
cuser=c
cdir=c

### Verifying that necessary directories exist ###

if [ ! -d "$dir" ]; then
echo ### Backup Directory doesn't exist, attemting to create directory /$dir ###
mkdir "$dir/"
ls -l "$dir"
else
clear
fi

if [ ! -d "$dir/$mdir/${mdir}_Current_Files" ]; then
mkdir "$dir/$mdir"
mkdir "$dir/$mdir/${mdir}_Current_Files"
else
clear
fi

if [ ! -d "$dir/$pc1dir/${pc1dir}_Current_Files" ]; then
mkdir "$dir/$pc1dir"
mkdir "$dir/$pc1dir/${pc1dir}_Current_Files"
else
clear
fi

if [ ! -d "$dir/$cdir/${cdir}_Current_Files" ]; then
mkdir "$dir/$cdir"
mkdir "$dir/$cdir/${cdir}_Current_Files"
else
clear
fi

if [ ! -d "$dir/$sdir/${sdir}_Current_Files" ]; then
mkdir "$dir/$sdir"
mkdir "$dir/$sdir/${sdir}_Current_Files"
else
clear
fi

### rsync remote directories to local directory , and create tar archives ###

echo "### rsync $mdir $m remote directories to local directory ###"                  
ping -c 1 $m > /dev/null
if [ $? -eq 0 ]; then 
rsync -avzpt --delete --progress -e ssh $muser@$m:/usr/user/data :/usr/fbin "$dir/$mdir/${mdir}_Current_Files/"
cd "$dir"
cd $mdir/${mdir}_Current_Files/
rm $mdir/data/core* $mdir/data/*.tgz $mdir/data/*.gz $mdir/data/*.old $mdir/data/*.sav 
tar czvf ../${mdir}_$n.tgz data fbin 
echo -e "${green}m $m rsync Successful!${nocol}" >> $mess
else
clear
echo -e "${red}m $m rsync Failed!${nocol}" 
fi

echo "### rsync $cdir $c remote directories to local directory ###"
ping -c 1 $c > /dev/null
if [ $? -eq 0 ]; then 
rsync -avzpt --delete --progress -e ssh $cuser@$c:/home/c "$dir/$cdir/${cdir}_Current_Files/"
cd "$dir"
cd $cdir/${cdir}_Current_Files
tar czvf ../${cdir}_$n.tgz c 
echo -e "${green}c $c rsync Successful!${nocol}" >> $mess
else
clear
echo -e "${red}c $c rsync Failed!${nocol}" >> $mess
fi

echo "### rsync $sdir $s remote directories to local directory ###"
ping -c 1 $s > /dev/null
if [ $? -eq 0 ]; then 
rsync -avzpt --delete --progress -e ssh $suser@$s:/home/sitecon "$dir/$sdir/${sdir}_Current_Files/"
cd "$dir"
cd $sdir/${sdir}_Current_Files
tar czvf ../${sdir}_$n.tgz sitecon
echo -e "${green}s  $s rsync Successful!${nocol}" >> $mess
else
clear
echo -e "${red}s  $s rsync Failed!${nocol}" >> $mess
fi

echo "### rsync $pc1dir $pc1 remote directories to local directory ###"
ping -c 1 $pc1 > /dev/null
if [ $? -eq 0 ]; then 
rsync -avzpt --delete --progress -e ssh $pc1user@$pc1:/cygdrive/c/Progra~1/user "$dir/$pc1dir/${pc1dir}_Current_Files/"
cd "$dir"
cd $pc1dir/${pc1dir}_Current_Files
rm user/PCI*.exe user/debugreportfunc.* user/*.zip user/*.tgz 
tar czvf ../${pc1dir}_$n.tgz user 
echo -e "${green}POS $pc1 rsync Successful!${nocol}" >> $mess
else
clear
echo -e "${red}POS $pc1 rsync Failed!${nocol}" >> $mess
fi

clear
cat $mess
rm $mess

```

---

### Post by TheFu on 2014-01-19
Please don't take this the wrong way.  tgz files for backups are "the hard way."  

Also, I've reread the text and don't see a question.  What isn't working? My network isn't anything like yours so I will not be running your script here.

The parts where you store IPs and names?  Replace that with the built-in ~/.ssh/config file. Every program that I've used based on scp, ssh, sftp will honor that file and the settings.  Give each machine an alias, then put in the DNS/IP, userid.  Now all those lines become a list of server names to be looped over.  If you like.

Enable debug output to see what your script is really doing. **#!/bin/bash -x** Be certain to send the output to a log file. Anything funny showing up? Look for lines that do not work, but you are positive they should.

There are lots of backup tools that use ssh and handle daily backups easily even if the remote system isn't running Linux/UNIX and the remote file system is not linux-permissions-friendly.  Duplicity, rbackup, rdiff-backup are just a few.  These only "send" changed data to the backup server ... or the data can be "pulled" if you prefer.

When scripting things, we all start out writing what we would type, then we get a little lazier and start looking to loop over different machines, but use the same main commands ... typed in just once. A shorter script has fewer bugs, right?
It is good form to completely specify all program paths.  rm would be /bin/rm ... using variables makes that simpler.  Why?  When running scripts under a crontab, there isn't much "environment", so things that work in your normal userid thanks to LD_LIBRARY_PATH and PATH variables will not work under cron.  /bin is probably included in the crontab path, but ... other directories with GUI programs probably are not.

Again, what is not working in the process today?

If you are interested in my backup scripts, my profile page here has links.

Oh ... and if you just want to create ssh keys use **ssh-keygen** and copy them to a remote system with **ssh-copy-id**.

---

### Post by nerdtron on 2014-01-19
I assume your destination is also Linux? Ubuntu perhaps?
Why not use rsync to backup you files. If you already configured ssh keys for password less logins, rsync maybe the best way to copy via network.
Rsync can send incremental files, existing files are no longer transferred to the destination if they are the same, it can also resume broken/interrupted copies so backup large files on an unreliable network is possible.
Sample script:

```
#!/bin/bash

#Go the the directory of the files you want to backup
cd /path/to/files/

#Now the rsync command to copy these file to the remote server. syntax is rsync [options] [source] [destination]
rsync -ar filename.tgz username@192.168.x.x:/path/to/destination/
```

You can also try rsync --progress -avrh to show the progress of transferred file, a means copy file permissions, v for verbose, r for recursion to copy folders, and h for human readable format.

---

### Post by chadk5utc on 2014-01-22
Thanks you both for replying 
Nerdtron Thanks
 I think thats exactly what I was looking for. I was trying to find the simplest way to rsync to remote machine.

---

