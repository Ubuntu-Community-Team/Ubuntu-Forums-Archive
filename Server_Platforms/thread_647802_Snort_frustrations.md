---
title: "Snort frustrations"
date: 2007-12-22
forum: Server Platforms
---

### Post by StormWatcher on 2007-12-22
I tried to search different areas for an answer to this issue before I post, but I did not find an answer here or on Google.

I have tried to install Snort (version 2.7) on three different Ubuntu installs and always get the same error when I tried to use oinkmaster to get new rules.

This is just one line of many:
tar: doc/signatures/9921.txt: Cannot write: No space left on device

sample:/var/run/oinkmaster$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/sniffer-root
                       5640304    729980   4623812  14% /
varrun                   62368        56     62312   1% /var/run
varlock                  62368         0     62368   0% /var/lock
udev                     62368        60     62308   1% /dev
devshm                   62368         0     62368   0% /dev/shm
/dev/sda1               241116     24284    204384  11% /boot

I am new to Linux in general and I am trying to get this to work.  I did try this on a 200 GB drive with the same error of not space left.  Please someone point out the obvious solution.

I thought it might be a permissions issue so I 
sudo chmod -R 777 /var/run/oinkmaster
sudo chmod -R 777 /ect/snort/rules

I also get:
sample:/etc/snort$ sudo makesidex.pl /etc/snort/rules >autodisable.conf
-bash: autodisable.conf: Permission denied

Oinkmaster does download the file correctly.

This is the last line of the error.
/usr/sbin/oinkmaster: Error: failed to untar /var/run/oinkmaster/oinkmaster.xWHxFxFOyY/url.o3a4YtRNcQ/snortrules.tar.

Thanks for your help.

---

### Post by mgariepy on 2008-05-07
Hi,

Today i had the same problem than you, I've only changed the tmpdir = /var/run/oinkmaster  in /etc/oinkmaster.conf

and now it run smootly.

Marc

---

### Post by zchef on 2008-06-24
I have completed those same chmod's and still no joy with first oinkmaster download. It spills lotsa "Cannot write: No space left on device tar: Error exit delayed from previous errors" to the screen. I have drwxrwxrwx on /var/run/oinkmaster which is where it appears oinkmaster would like to untar the rules snapshot. Any help appreciated.

---

### Post by Sarmacid on 2008-07-22
To get around this I just created a directory in my user and changed the snort.conf file, couldn't get it to work with the default path there

```
cd
mkdir snortrulestemp
sudo nano /etc/oinkmaster.conf
```

There look for the line that's not commented and starts with tmpdir, and add your directory

```
/home/<your username>/snortrulestemp
```

---

