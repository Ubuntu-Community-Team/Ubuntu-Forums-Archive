---
title: "unfortuntly my dpkg totaly uninstall"
date: 2014-03-16
forum: Ubuntu Development Version
---

### Post by farukajam12345 on 2014-03-16
i am using ubuntu 14.04 LTS

working good...but

unfortuntly my dpkg totaly uninstall,,, now unable to update , cannot open software center 

and when try to update by synaptic package manager then  see




E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: _cache->open() failed, please report.  


sudo apt-get update  also try

---

### Post by Elfy on 2014-03-16
That error generally refers to you having a package manager open or working at the same time. Make sure nothing else is doing anything - you might have update manager working in the background.

---

### Post by farukajam12345 on 2014-03-16
[h=2][/h][INDENT]i am using ubuntu 14.04 LTS

working good...but

unfortuntly my dpkg totaly uninstall,,, now unable to update , cannot open software center

and when try to update by synaptic package manager then see




E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: _cache->open() failed, please report.


sudo apt-get update also try
[/INDENT]

---

### Post by 23dornot23d on 2014-03-16
Have you tried this in a terminal

**sudo apt-get update**

Also if that command works  .... to update/upgrade everything once more .... you could try

[B]sudo apt-get install aptitude

sudo aptitude update

sudo aptitude safe-upgrade

________________________________

[/B]Also do not keep creating the same post - you have 3 now all asking the very same thing[http://ubuntuforums.org/showthread.php?t=2211450](http://ubuntuforums.org/showthread.php?t=2211450)

---

### Post by coffeecat on 2014-03-16
Threads merged. Please do not post duplicates in different parts of the forum.

---

### Post by farukajam12345 on 2014-03-16
i try but nothing to do,,,  i am downlod manualy               dpkg_1.16.1.2ubuntu7.2.tar.bz2


not known how to install

---

### Post by farukajam12345 on 2014-03-16
faruk@faruk-MacBookPro:~$ sudo apt-get install aptitude
[sudo] password for faruk: 
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
faruk@faruk-MacBookPro:~$

---

### Post by farukajam12345 on 2014-03-16
faruk@faruk-MacBookPro:~$ sudo aptitude safe-upgrade
[sudo] password for faruk: 
sudo: aptitude: command not found
faruk@faruk-MacBookPro:~$

---

### Post by 23dornot23d on 2014-03-16
What does this show when you type it in a terminal lowercase (LS) by the way.

**ls /var/lib/dpkg/**

---

### Post by farukajam12345 on 2014-03-16
faruk@faruk-MacBookPro:~$ ls /var/lib/dpkg/
ls: cannot access /var/lib/dpkg/: No such file or directory
faruk@faruk-MacBookPro:~$

---

### Post by 23dornot23d on 2014-03-16
I have been searching for a answer that succeeded in re-creating the 5 directories under that .....

and none were successful ......... 

```

A problem where someone has not got the ability to do a upgrade because a series
of directories were missing ........  

/var/lib/dpkg/
[http://askubuntu.com/questions/383339/how-to-recover-deleted-dpkg-directory](http://askubuntu.com/questions/383339/how-to-recover-deleted-dpkg-directory)

```

you might be better off installing from the live cd again for the daily build

as 14.04 is still in testing a new one comes out each day to test ...........

One other way is to use the daily build and when installing choose " not to format the partition 14.04 is on " and hope
that it re-writes good files back in again ........ but that is a long shot and you may still have to do a full clean install
of the daily build for 14.04.

That is unless you can find a better solution from someone else ...... or wish to wait till another day when another build comes out for Testing .


There is a thread started here on where to get the latest Beta Testing iso from
[http://ubuntuforums.org/showthread.php?t=2211275](http://ubuntuforums.org/showthread.php?t=2211275)

---

### Post by bapoumba on 2014-03-16
That is a very strange output, this file should be populated :
```
bapoumba_lxde@SonyBlue:~$ ls /var/lib/dpkg/
alternatives   cmethopt        info   statoverride      status-old
available      diversions      lock   statoverride-old  triggers
available-old  diversions-old  parts  status            updates

```
What happened when you said dpkg was uninstalled ?

---

### Post by Ubi_one_2014 on 2014-03-16
> **farukajam12345 said:**
> faruk@faruk-MacBookPro:~$ sudo apt-get install aptitude
[sudo] password for faruk: 
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
faruk@faruk-MacBookPro:~$

you overlooked something

try:
sudo su - [enter]
enter your password [enter]
apt-get install aptitude [enter]

---

### Post by bapoumba on 2014-03-16
> **Ubi_one_2014 said:**
> you overlooked something

try:
sudo su - [enter]
enter your password [enter]
apt-get install aptitude [enter]

They did run it with sudo..

---

### Post by alan-pater on 2014-03-16
> **farukajam12345 said:**
> E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: _cache->open() failed, please report.
[LIST=1]
[*]Does the logon id you are using have sudo rights?
[*]Can a user with sudo acces see the /var/lib/dpkg/lock file?
[/LIST]

---

### Post by zika on 2014-03-16
> **alan-pater said:**
> 
[LIST=1]
[*]Does the logon id you are using have sudo rights?
[*]Can a user with sudo acces see the /var/lib/dpkg/lock file?
[/LIST]
If You've unistalled dpkg then try this:
Boot from Live Cd
```
sudo fdisk -l
```
Determine  which is Your drive letter (X)
```
[FONT=Ubuntu Mono]sudo mount /dev/sdaX /mnt[/FONT]
```
navigate to folder where You've DL-ed dpkg*.deb file(s)
```
[FONT=Ubuntu Mono]sudo dpkg --root=/mnt -i dpkg*.deb[/FONT]
```
If You've just erased folder then You have advice below this post of mine...

---

### Post by bapoumba on 2014-03-16
See post #10 : they do not have the file anymore.

To the OP, do you still have a  /var/backups/dpkg.status.0 ?
[http://www.linuxquestions.org/questions/linux-mint-84/dpkg-directory-re-create-862558/](http://www.linuxquestions.org/questions/linux-mint-84/dpkg-directory-re-create-862558/)

---

### Post by zika on 2014-03-16
> **bapoumba said:**
> See post #10 : they do not have the file anymore.

To the OP, do you still have a  /var/backups/dpkg.status.0 ?
[http://www.linuxquestions.org/questions/linux-mint-84/dpkg-directory-re-create-862558/](http://www.linuxquestions.org/questions/linux-mint-84/dpkg-directory-re-create-862558/)Even though it was unclear in first reading I've managed to get to the same conclusion You've derived and I've changed post of mine You (I beleive) refered to...

---

### Post by bapoumba on 2014-03-16
> **zika said:**
> Even though it was unclear in first reading I've managed to get to the same conclusion You've derived and I've changed post of mine You (I beleive) refered to...

Yes, just saw that, was going to edit my post to thank you :)
They may have erased the file trying to erase the lock file.

---

