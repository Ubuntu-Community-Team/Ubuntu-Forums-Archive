---
title: "Having trouble accessing encrypted home directory using Live CD"
date: 2016-10-11
forum: Security
---

### Post by malte-taeubrich on 2016-10-11
Hello,
I have a problem accessing my encrypted home directory using a live CD.
I'm trying to do this as I, for reasons I do not understand, am unable to boot Ubunut (it always gets stuck at the dots + ubuntu logo) and thus want to save my data and start with a fresh install.
I try to access my encrypted home directory with the command 
sudo ecryptfs-recover-private

this is what happens:
INFO: Searching for encrypted private directories (this might take a while)...
find: ‘/run/user/999/gvfs’: Permission denied
find: File system loop detected; ‘/sys/kernel/debug/pinctrl’ is part of the same file system loop as ‘/sys/kernel/debug’.

I have been at this problem for 3 hours and can't find any advice online that is helpful.
I am quite desperate at the moment as my last backup is a month old and I really need some files which are in the home directory.

Also, I have been using Ubuntu for a while, but am totally incompetent with using the terminal, so I would be really grateful for step by step advices on what to do.

Thanks in Advance!

---

### Post by mastablasta on 2016-10-11
this is the porblme with encryption. it is made so that it is hard to be accessed. and in case of using it you need good backups.

in your case it look sto me liek ti doesnt' recognise the user. perhaps you missed something in the command where user should be input.

---

### Post by sgian on 2016-10-18
Did you by any chance use a proprietary graphics driver with that encryption?  I did that once and had the same result, not being able to get past the dots.  If I am correct, the proprietary graphics driver is not able to access some files it needs due to encryption, and I suppose if you are able to revert to the open source graphics then you might be able to boot linux.  I would link to instructions to try, but I don't know what drivers you are using.  This search might help... [https://www.google.com/search?client=ubuntu&channel=fs&q=remove+proprietary+drivers+ubuntu+command+line&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=remove+proprietary+drivers+ubuntu+command+line&ie=utf-8&oe=utf-8)

---

