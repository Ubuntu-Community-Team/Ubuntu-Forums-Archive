---
title: "Checking Suckit rootkit False positive."
date: 2010-08-16
forum: Security
---

### Post by MadMax2 on 2010-08-16
I'm trying to understand this a little better:

- The SucKIT rootkit allows an attacker to hide malicious files by giving them a particular ending. The current attacker is hiding code that ends in xrk or mem. To test for the presence of the rootkit, create a file whose name ends in xrk or mem, then execute an "ls -l". If the files you just created are not shown in the output of ls, it means that the rootkit is hiding them, ie. your system is compromised and needs to be rebuilt.
++++++++++++
[**negative** so no problem and rkhunter didn't find it - forget it]
++++++++++++++++++++
- Change directories to /sbin and execute an "ls -l init" -- the link count should be 1. 

max@max-desktop:/lib$ ls -l init
total 36
-rw-r--r-- 1 root root 1801 2010-05-09 18:12 fstab
-rwxr-xr-x 1 root root 9824 2010-03-30 20:17 readlink
drwxr-xr-x **2** ??root root   40 2010-08-17 09:54 rw
-rw-r--r-- 1 root root 2847 2009-09-08 06:58 splash-functions-base
-rwxr-xr-x 1 root root 1830 2010-08-13 12:26 upstart-job
-rw-r--r-- 1 root root 5791 2009-09-08 06:58 usplash-fsck-functions.sh
-rw-r--r-- 1 root root  571 2009-09-08 06:58 vars.sh
max@max-desktop:/lib$ 
+++++++++++++++
link count is 1 & 2? means? If infected will be all 1?
+++++++++++++++++++=
Create a hard link to init using ln, and then execute the "ls -l init" again. If the link count is still 1, the SK rootkit is installed.

- Rooted systems send usernames and passwords to other compromised machines using TCP port 55, so if you keep records of network connections, traffic to destination port TCP/55 merits further investigation.

---

### Post by uRock on 2010-08-17
The link count for that directory is two because it is linked twice in the directories(meaning it falls within two different folders but are linked so that the system didn't have to create duplicates on the HDD and therefore saving space.

---

### Post by uRock on 2010-08-17
This will allow you to see that the output of ls is the same for both of us. Your system is fine. It is a false positive.
```
rabbit@rabbit-desktop:/lib$ ls -l init
total 36
-rw-r--r-- 1 root root  1801 2010-05-08 23:14 fstab
-rwxr-xr-x 1 root root 10792 2010-03-30 07:30 readlink
drwxr-xr-x 2 root root    40 2010-08-16 20:28 rw
-rw-r--r-- 1 root root  2847 2009-09-07 11:58 splash-functions-base
-rwxr-xr-x 1 root root  1830 2010-08-12 16:10 upstart-job
-rw-r--r-- 1 root root  5791 2009-09-07 11:58 usplash-fsck-functions.sh
-rw-r--r-- 1 root root   571 2009-09-07 11:58 vars.sh

```

---

### Post by MadMax2 on 2010-08-17
Fantastic.
Thanks I wish I understood how things work better but don't really have the time.

---

### Post by uRock on 2010-08-17
> **MadMax2 said:**
> Fantastic.
Thanks I wish I understood how things work better but don't really have the time.
Your welcome. I only knew about linking from taking a UNIX/Linux summer class. Then I figured it would be most helpful to look at the directory you posted to see if it looked the same.

Sometimes I think it'd be nice to have a sticky with all of the false positives and their identifying info.

Cheers,
uRock

---

### Post by bodhi.zazen on 2010-08-17
> **MadMax2 said:**
> Fantastic.
Thanks I wish I understood how things work better but don't really have the time.

IMHO, running tools such as rkhunter, chkrootkit, etc, without taking the time to research the output is an exercise in futility.

I advise you either make the time or do not run these tools.

---

### Post by noway2 on 2010-08-17
MadMax2, did you perchance do an update today and then not reboot?

I performed an update this morning and then received the same warning.  First, I received an Ossec alert claiming that '/proc/1/maps' had the suckit rootkit, based on the 'init' signature.

I then ran chrootkit which claimed the /sbin/init was infected.  Rkhunter found nothing.  I too ran the same checks for Suckit and all came up negative.  I also found a bug report on Launchpad that went back a little ways, but apparently this has popped up from time to time.  I didn't fully understand the cause but it looks like an extra space gets placed after the word init in the '/proc/1/maps' file and this registers as the signature.  A reboot clears the condition and then chrootkit comes up clean.

---

### Post by MadMax2 on 2010-08-17
> **noway2 said:**
> MadMax2, did you perchance do an update today and then not reboot?

yes I think I did. I leave the PC on so the electronics last longer.

Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/xulrunner-1.9.2.8/.autoreg /usr/lib/pymodules/python2.6/.path /usr/lib/firefox-3.6.8/.autoreg
 that would be logged in to forum while doing a chkrootkit?

Searching for Suckit rootkit...                             nothing found

---

