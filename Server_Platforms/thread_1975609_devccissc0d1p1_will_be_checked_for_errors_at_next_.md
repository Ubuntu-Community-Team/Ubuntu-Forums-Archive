---
title: "/dev/cciss/c0d1p1 will be checked for errors at next reboot"
date: 2012-05-07
forum: Server Platforms
---

### Post by anonymouschief on 2012-05-07
Hello,

Please help me with a command force a disk check on the next restart on Ubuntu Server 12.04.

When I ssh into the server, I get the "*** /dev/cciss/c0d1p1 will be checked for errors at next reboot ***" displayed in MOTD.

I then ran the following:
```
sudo dumpe2fs /
``` only to realize that the server will automatically check the disk every 6 months as displayed below:

```
Last checked:             Thu Jan 26 20:58:30 2012
Check interval:           15552000 (6 months)
Next check after:         Tue Jul 24 21:58:30 2012

```

Please help me with the command to run to manually check the disks on the next restart without changing that 6 month cycle. I got this "*** /dev/cciss/c0d1p1 will be checked for errors at next reboot ***" after upgrading to 12.04, so I would like to schedule the disk check as soon as yesterday.

Thanks,
:popcorn:
AnonymousChief

---

### Post by CharlesA on 2012-05-07
```
sudo shutdown -rF now
```

[http://unixhelp.ed.ac.uk/CGI/man-cgi?shutdown+8](http://unixhelp.ed.ac.uk/CGI/man-cgi?shutdown+8)

---

### Post by anonymouschief on 2012-05-07
[QUOTE=CharlesA;11915255]```
sudo shutdown -rF now
```

I ran that command, but that message is still showing up in MOTD. Unfortunately I cannot see the boot cos the server has no monitor or keyboard connected to it. Is there a log file where I can tell if the disk check ran?

Thanks,
:popcorn:
AnonymousChief

---

### Post by CharlesA on 2012-05-07
Is it your boot drive? If it's not, unmount it and runs fsck on it manually.

---

### Post by anonymouschief on 2012-05-07
> **CharlesA said:**
> Is it your boot drive? If it's not, unmount it and runs fsck on it manually.

I checked the contents of /dev/cciss. It is the 5th partition (I don't know if this helps):

**c0d0  c0d0p1  c0d0p2  c0d0p5  c0d1  c0d1p1**

```

drwxr-xr-x  2 root root     160 May  7 15:17 ./
drwxr-xr-x 16 root root    4060 May  7 15:17 ../
brw-rw----  1 root disk 104,  0 May  7 15:17 c0d0
brw-rw----  1 root disk 104,  1 May  7 15:17 c0d0p1
brw-rw----  1 root disk 104,  2 May  7 15:17 c0d0p2
brw-rw----  1 root disk 104,  5 May  7 15:17 c0d0p5
brw-rw----  1 root disk 104, 16 May  7 15:17 c0d1
brw-rw----  1 root disk 104, 17 May  7 15:17 c0d1p1

```

It is located on my primary drive /, I guess (I am still unsure about when to use either "drive" or "partition" references in my tech lingo).

My system has two drives in raid, one is / and the other is mounted as /data

Thanks,
:popcorn:
AnonymousChief

---

### Post by CharlesA on 2012-05-07
Oh, raid array?

[http://cciss.sourceforge.net/](http://cciss.sourceforge.net/)

Does running this:

```
sudo touch /forcefsck && sudo reboot
```

Cause it to be checked?

---

### Post by anonymouschief on 2012-05-07
> **CharlesA said:**
> Oh, raid array?

[http://cciss.sourceforge.net/](http://cciss.sourceforge.net/)

Does running this:

```
sudo touch /forcefsck && sudo reboot
```

Cause it to be checked?

I ran the command you suggested, the message is still showing up in MOTD. The forcefsck file is still in the root:

*** /dev/cciss/c0d1p1 will be checked for errors at next reboot ***

Is there a log file I can check to see if disk check actually ran, or the existence of the forcefsck means that it did not run?

Thanks,
:popcorn:
AnonymousChief

---

### Post by CharlesA on 2012-05-07
It did not run. Try the livecd approach and see what happens.

---

### Post by fade2gray on 2013-03-22
Thread marked as [SOLVED] with no obvious solution.

The answer provided here worked for me...

[http://askubuntu.com/questions/163184/repeated-disk-will-be-checked-messages-when-logging-into-cli-server](http://askubuntu.com/questions/163184/repeated-disk-will-be-checked-messages-when-logging-into-cli-server)

---

### Post by deadsea on 2013-04-20
This problem is caused often caused by [FONT=Courier New]/var/lib/update-notifier/fsck-at-reboot[/FONT] (which contains the message) having a future timestamp and never getting regenerated. 

You can remove that file and reboot.

Here is the command line that fixes the problem without rebooting by regenerating motd immediately through the update-motd system.

[FONT=Courier New]sudo rm /sudo bash -c 'rm /var/lib/update-notifier/fsck-at-reboot && for file in /etc/update-motd.d/*; do $file; done > /var/run/motd' && cat /etc/motd[/FONT]

---

