---
title: "Root Filesystem Suddenly Full"
date: 2012-03-22
forum: Server Platforms
---

### Post by damo12 on 2012-03-22
Hi,

I support a company running a small Ubuntu server.  It is running Ubuntu 10.0.4 64 bit and has been working fine for months.  The server is headless and I usually access it through Webmin and Putty.

I have checked on it today and discovered that the server hard drive (files are stored on separate drives) is suddenly full.  I have never seen this before and am afraid to delete files without guidance in case I break the server.

The output of df -ah is:
```
> df -ah
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/wmserver-root
                      227G  227G     0 100% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                     0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
none                  491M  220K  491M   1% /dev
none                     0     0     0   -  /dev/pts
none                  496M     0  496M   0% /dev/shm
none                  496M  5.4M  491M   2% /var/run
none                  496M     0  496M   0% /var/lock
none                  496M     0  496M   0% /lib/init/rw
/dev/sdb1             932G  598G  335G  65% /media/backup
/dev/sdc1             932G  303G  630G  33% /media/server
/dev/sda1             228M  190M   26M  89% /boot
/dev/sdd1             932G  598G  335G  65% /mnt/usb_backup
```


The output from "Disc and Network Fileystems" in Webmin is:

[IMG]http://i1170.photobucket.com/albums/r534/damo331/screenshot.png[/IMG]


If I edit the mount for / it is mounted as "LVM VG wmserver LV root".  On another server I run which is working fine, it is listed as "UUID=32273b44-0e3d-4eb7-a8ac-2cbba4ce1f9f".  I am the only one who has access to the server so I'm not sure what has changed.

Can anyone suggest how I can resolve this issue.

Many thanks

---

### Post by Insomn1a on 2012-03-22
[http://ubuntuforums.org/showthread.php?t=1502698](http://ubuntuforums.org/showthread.php?t=1502698)

---

### Post by spynappels on 2012-03-22
As suggested in the above link, run the following
```
cd /
du -h --max-depth=1
```
and see which directory is using up the space. There is a good chance that something has suddenly started writing huge logs in /var/log and that this has filled a disk.

---

### Post by collisionystm on 2012-03-22
I always do

du -chs / | sort -n

---

### Post by damo12 on 2012-03-22
Hi everyone,

Thanks for your quick replies.  I finally got to the bottom of it with a bit of digging and some questioning of the staff in the office.

One of the mounted drives is an external USB drive (mounted at /mmt).  At some point, this drive was accidentally unplugged and then plugged back in at a later date.  While the drive was unmounted, the server ran a backup and it created its own /mmt backing up onto the main drive.

When I carried out the df -ah the /mmt looked fine at 65% because the USB drive was re-mounted and working fine.It was only when I unmounted all other drives apart from the "server" drive and carried out df -ah again that I found what had happened.

Ironically, this happened to me years ago and I fixed it with the help of this forum but on that occasion he USB drive was still unmounted so it was easy to see what had happened once I discovered the df -ah command.

Once again, thank you all for your prompt and exact help.  Hopefully I won't make this mistake for a third time.

Thanks again.

---

### Post by redmk2 on 2012-03-22
> **damo12 said:**
>  Hopefully I won't make this mistake for a third time.

Thanks again.

Here is how I eliminate that problem:

I have the backup script verify that there is no file at the mount point.  I create a file called bkp_chk.1st.  If this file is found by the backup script --  the partition (drive) is not mounted and the script aborts.  If the file is not found then the partition has been mounted and the file can't be seen, so the backup routine is run.

Edit:  You could use something like this```
if [ -f /mnt/backup/bk_chk.1st ] ; then
  echo "You need to mount the backup drive"
else 
 some code here to run your backup
fi

```

---

### Post by damo12 on 2012-03-23
> **redmk2 said:**
> Here is how I eliminate that problem:

I have the backup script verify that there is no file at the mount point.  I create a file called bkp_chk.1st.  If this file is found by the backup script --  the partition (drive) is not mounted and the script aborts.  If the file is not found then the partition has been mounted and the file can't be seen, so the backup routine is run.

Edit:  You could use something like this```
if [ -f /mnt/backup/bk_chk.1st ] ; then
  echo "You need to mount the backup drive"
else 
 some code here to run your backup
fi

```


Hi,

That sounds like a perfect solution but (please excuse my ignorance) where would I store the script and how would I run it?  I currently run the backup as a cron job using the command:
```
rsync -av /media/backup/ /mnt/USB_Backup/ >>/media/cron_log/rsync.lst 2>&1
```

I'm sorry for asking what I'm sure is a really obvious question but I have no experience of programming or running scripts.  I suppose the fact that I have been running Ubuntu servers for the last 6 years and managed so far is a testament to how easy Ubuntu server is to use and how good the forums etc are at providing guidance.

---

### Post by spynappels on 2012-03-23
You would put the command currently in the cronjob (rsync....) in to where the script says "some code here..."

Save the script to some location such as /usr/bin/, remembering to make it executable
```
sudo chmod +x script_name.sh
```
In the crontab you just run the script by referencing it with it's full path i.e. /usr/bin/script_name.sh

---

### Post by damo12 on 2012-03-23
Thank you so much for your help, I'll try that over the weekend and hopefully will never have this problem again.

---

### Post by redmk2 on 2012-03-23
> **damo12 said:**
> Thank you so much for your help, I'll try that over the weekend and hopefully will never have this problem again.
If you have never created scripts I would start with a small script that is only for testing.  You should be able to run it from the terminal.  Then you can automate it using cron.

Every sys admin has their own style.  For my systems I put locally (to this host) used  scripts in /[COLOR="Red"]usr[/COLOR]/[COLOR="Blue"]local[/COLOR]/[COLOR="DarkGreen"]sbin[/COLOR].  Breaking this down:```
[COLOR="Red"]usr[/COLOR] = unix system resources
[COLOR="Blue"]local[/COLOR] = local to this machine
[COLOR="DarkGreen"]sbin[/COLOR] = system executables (bin is for OS related executables)
```

---

### Post by damo12 on 2012-03-23
Hi,

I should have known that this was going far too smoothly.  I created a file called "bkp_chk.1st" and placed it in "/mnt/USB_Backup/".  I then created a script called "usb_bk_chk_1st.sh" with the code:
```
if [ -f /mnt/USB_Backup/bkp_chk.1st ] ; then
  echo "You need to mount the backup drive"
else 
 rsync -av /media/backup/ /mnt/USB_Backup/ >>/media/cron_log/rsync.lst 2>&1
fi
```
I placed the script at "/usr/local/sbin".

Using Putty I ran the command:
```
sudo chmod +x /usr/local/sbin/usb_bk_chk_1st.sh
```
This seemed to work as I did not receive any error messages.


I then tried executing the script with the command:
```
/usr/local/sbin/usb_bk_chk_1st.sh
```
and received the error message:
```
/usr/local/sbin/usb_bk_chk_1st.sh: line 3: syntax error near unexpected token `else'
/usr/local/sbin/usb_bk_chk_1st.sh: line 3: `else
```

When I tried running the command as:
```
sudo /usr/local/sbin/usb_bk_chk_1st.sh
```
I received the error message:
```
/usr/local/sbin/usb_bk_chk_1st.sh: 3: Syntax error: "else" unexpected (expecting "then")
```

I'm sure this is something I've done and if anyone can point me in the right direction I would be extremely grateful.

On a slightly different note, can anyone point me to a guide on how to get the server to email me if there is a problem with a particular cron job ie if the backup fails because the script detects that the drive is not present?  I have had a search and the only guides I can see are to set up a full mail server which seems like overkill or guides that will just email me when each and every job is ran.

Thanks again.

---

### Post by spynappels on 2012-03-23
Sorry, I assumed too much in my answer.

the very first line of any Bash script should be this
```
#!/bin/bash
```
This tells the system that it is a Bash script.

---

### Post by damo12 on 2012-03-23
Sorry,

I cannot stress how much of a novice I am or how much I appreciate all of this help.

My script now reads:
```
#!/bin/bash
if [ -f /mnt/USB_Backup/bkp_chk.1st ] ; then
  echo "You need to mount the backup drive"
else 
 rsync -av /media/backup/ /mnt/USB_Backup/ >>/media/cron_log/rsync.lst 2>&1
fi
```


When I run the command:
```
/usr/local/sbin/usb_bk_chk_1st.sh
```
I get the error message:
```
/usr/local/sbin/usb_bk_chk_1st.sh: /bin/bash^M: bad interpreter: No such file or directory
```

When I change the command to:
```
sudo /usr/local/sbin/usb_bk_chk_1st.sh
```
The error message changes to:
```
unable to execute /usr/local/sbin/usb_bk_chk_1st.sh: No such file or directory
```

I have checked and double-checked the location and name of the file usb_bk_chk_1st.sh and the rsync command is a direct copy and paste from the cron job.  I have tried these commands with the USB drive mounted and unmounted and received the same error messages in both states.

---

### Post by redmk2 on 2012-03-23
> **damo12 said:**
> Sorry,

I cannot stress how much of a novice I am or how much I appreciate all of this help.

My script now reads:
```
#!/bin/bash
if [ -f /mnt/USB_Backup/bkp_chk.1st ] ; then
  echo "You need to mount the backup drive"
else 
 rsync -av /media/backup/ /mnt/USB_Backup/ >>/media/cron_log/rsync.lst 2>&1
fi
```


When I run the command:
```
/usr/local/sbin/usb_bk_chk_1st.sh
```
I get the error message:
```
/usr/local/sbin/usb_bk_chk_1st.sh: /bin/bash^M: bad interpreter: No such file or directory
```

When I change the command to:
```
sudo /usr/local/sbin/usb_bk_chk_1st.sh
```
The error message changes to:
```
unable to execute /usr/local/sbin/usb_bk_chk_1st.sh: No such file or directory
```

I have checked and double-checked the location and name of the file usb_bk_chk_1st.sh and the rsync command is a direct copy and paste from the cron job.  I have tried these commands with the USB drive mounted and unmounted and received the same error messages in both states.

Are you sure you want to be backing up everything while you are testing the script?  I would substitute the command with a simple: echo "some text here" statement.

Do you see the ^M in the error?  This is due to using a Windows text editor.  This is not visable in the file.  Its a windows style carriage return/line end.  Use **gedit** in a text mode or **leafpad** or from the CLI; you can use **nano**.

These are the kinds of things a newbie always uncovers.  You just have to keep going and it will all make sense.

---

### Post by damo12 on 2012-03-23
Ok, I think I'm almost there but somewhere along the line this has got mixed up.  Thanks to Redmk2's advice I have created this text script in nano and not Notepadd++ on the office computer:
```
#!/bin/bash
if [ -f /mnt/USB_Backup/bkp_chk.1st ] ; then
  echo "You need to mount the backup drive"
else
  echo "This has worked"
fi
```


When I run this with the drive mounted I get the message "*You need to mount the backup drive*".  When I run it with the drive unmounted I get the message "*This has worked*.  In other words, the messages are the wrong way round.

Thanks again for your help.

---

### Post by redmk2 on 2012-03-23
> **damo12 said:**
> Ok, I think I'm almost there but somewhere along the line this has got mixed up.  Thanks to Redmk2's advice I have created this text script in nano and not Notepadd++ on the office computer:
```
#!/bin/bash
if [ -f /mnt/USB_Backup/bkp_chk.1st ] ; then
  echo "You need to mount the backup drive"
else
  echo "This has worked"
fi
```


When I run this with the drive mounted I get the message "*You need to mount the backup drive*".  When I run it with the drive unmounted I get the message "*This has worked*.  In other words, the messages are the wrong way round.

Thanks again for your help.

Was the drive mounted when you made the file /mnt/USB_Backup/bkp_chk.1st?  The idea is to place the file at the mount point with the drive NOT mounted (on the local drive).

Edit:  Remove the file from the external drive.

---

### Post by damo12 on 2012-03-23
Thank you so much, that is now working fine.  That is what I love so much about these forums, everyone is so helpful and forgiving of my ignorance.

---

### Post by redmk2 on 2012-03-23
> **damo12 said:**
> Thank you so much, that is now working fine.  That is what I love so much about these forums, everyone is so helpful and forgiving of my ignorance.

No you can see the logic.  If the file is located then drive is not mounted!  There are  more things that can go wrong with the script, so I suggest you find some BASH tutorials and study up.

If you feel you need to try an rsync command, I would create a small test directory with files and back that up.

---

### Post by damo12 on 2012-03-23
> **redmk2 said:**
> No you can see the logic.  If the file is located then drive is not mounted!  There are  more things that can go wrong with the script, so I suggest you find some BASH tutorials and study up.

I suppose when you look at it that way it makes perfect sense.  I still have problems getting my head around the fact that Linux will create a new mount point if a drive is missing.  I guess I've spent too long on Windows machines where they will just spit their dummy out telling me that the drive is not present.

BASH tutorials will be first on my list on Monday morning.  Hopefully I'll find a nice script to email me if the drive is not mounted.

---

### Post by redmk2 on 2012-03-23
> **damo12 said:**
> I suppose when you look at it that way it makes perfect sense.  I still have problems getting my head around the fact that Linux will create a new mount point if a drive is missing.  I guess I've spent too long on Windows machines where they will just spit their dummy out telling me that the drive is not present.

BASH tutorials will be first on my list on Monday morning.  Hopefully I'll find a nice script to email me if the drive is not mounted.

The system does not create a new mount point at all.  The mount point on any file system is just an ordinary directory.  When you have files (and subdirectories) in that directory and then mount a remote file system (partition) at that mount point; you can't access the files in that directory that were there before you did the mount.  look for yourself.  What do you see in the directory when the drive is not mounted.  What do you see when the partition is mounted.

FYI: You don't really "mount a drive".  What you really do is mount a partition with a file system to the existing file system at a specific place in the local file system.  A drive is a physical object.  A partition is a real object (in a computing sense).  It is a block ready device (e.g it's a formatted partition).

---

### Post by damo12 on 2012-03-23
Thank you, I have never looked at it that way but now that makes so much more sense.

---

### Post by redmk2 on 2012-03-23
> **damo12 said:**
> Thank you, I have never looked at it that way but now that makes so much more sense.

This is how Windows and Mac OSX handles this type of thing too.  it's just hidden from the end user.

---

