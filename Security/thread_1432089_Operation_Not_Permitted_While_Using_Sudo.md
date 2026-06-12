---
title: "Operation Not Permitted While Using Sudo"
date: 2010-03-17
forum: Security
---

### Post by Spaceman Spiff on 2010-03-17
Hey gentleman(and ladies),

tl;dr - sudo make -> operation not permitted, sudo chown -R 777 * -> operation not permitted on some of the files 

--------------------

I am trying to install a library and am having some confusing/frustrating issues.  The biggest issue is permissions, if we could tackle this issue I am sure I can figure out the others...

The problem:
 Sudo make is getting permission denied on file 1, while using regular make I am getting permission denied on file 2.  I have noticed some of the directories in the library are under nobody:nogroup.  I tried chown and sudo chown, both didn't work.  Sudo chown got permission errors, while chown didn't change ALL the files. (operation not permitted once again)  Tried sudo su, and working from there, that also did not work. (permission once again).  Using lsattr returned "lsattr: Inappropriate ioctl for device While reading flags on".

```
sudo chmod -R 777 *
chmod: changing permissions of `Makefile': Operation not permitted
chmod: changing permissions of `Makefile.am': Operation not permitted
chmod: changing permissions of `Makefile.in': Operation not permitted
chmod: changing permissions of `queue.c': Operation not permitted
chmod: changing permissions of `queue.h': Operation not permitted
chmod: changing permissions of `ucutil.h': Operation not permitted

```

Note the .libs folder not having write permission....
```
chmod -R 777 *
constantin@Nadfadfo:~/network_home/constantin/libraries/unicap/libunicap-0.9.8/common$ ls -la
total 68
drwxrwxrwx 4 constantin constantin  4096 2010-03-17 11:31 .
drwxrwxrwx 8 constantin constantin  4096 2010-03-17 11:31 ..
drwxrwxrwx 2 constantin constantin  4096 2010-03-17 11:31 .deps
drwxr-xr-x 2 nobody       nogroup       4096 2010-03-17 11:31 .libs
-rwxrwxrwx 1 constantin constantin 15295 2010-03-17 11:31 Makefile
-rwxrwxrwx 1 constantin constantin   130 2010-01-17 08:17 Makefile.am
-rwxrwxrwx 1 constantin constantin 15262 2010-01-17 08:17 Makefile.in
-rwxrwxrwx 1 constantin constantin  6101 2010-01-17 02:49 queue.c
-rwxrwxrwx 1 constantin constantin  1667 2010-01-17 02:49 queue.h
-rwxrwxrwx 1 constantin constantin   125 2010-01-17 02:49 ucutil.h


```

System: Karmic Koala 64-bit

Any help would be appreciated.  Thank you.
------------

---

### Post by 2hot6ft2 on 2010-03-17
The make part doesn't require the sudo. Might try removing the first sudo just before the make command and run all the makes then run the rest that requires sudo.
So instead of make file - sudo chown - make file, try make file - make file - sudo chown
Once you run the sudo you're running as root after that point so when it comes to the next make you're still running it as sudo.

I hope that makes some kind of sense. It looks like a mess.

---

### Post by cdenley on 2010-03-17
Wildcards and sudo don't always mix well. The wildcard is handled before privilege escalation, so if your user cannot list files in the directory the wildcard is searching, the sudo command will fail. You can use an interactive shell, then use wildcards.
```

sudo -i

```

---

### Post by Spaceman Spiff on 2010-03-17
Hmm I'll take a look into sudo and wildcards, never seen that before.  

However, the problem was discovered to be the fact that I am attempting to sudo on my network drive, which obviously has sudo squashed ... I just totally forgot I was on a network :facepalm:

---

### Post by kojart on 2011-07-16
Hello, All ubuntu users
 
I am facing a similar situation. In the beginning I had a ful drive that lead me to a log in > X session warning. I solved this by deleting some personal data with rm a. However, as ubuntu beginner I misunderstood one of the scripts I read on-line and now everytime I use sudo I get the following:
"- bash: /usr/bin/python: Permission denied" and as regards the log in, even though I insert the correct password I get a new log in (the so-called "log in loop")
 
Thank you for your help, Tomas

---

### Post by cariboo on 2011-07-16
@kojart, please don't post your question in multiple threads, especially ones that don't have anything to do with your problem.

This thread is closed.

---

