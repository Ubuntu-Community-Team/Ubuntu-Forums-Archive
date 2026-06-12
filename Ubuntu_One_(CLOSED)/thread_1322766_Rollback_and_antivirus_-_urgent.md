---
title: "Rollback and antivirus - urgent"
date: 2009-11-11
forum: Ubuntu One (CLOSED)
---

### Post by ntrapped on 2009-11-11
Hi, 

I had been using Ubuntu 9 for a few months now. 

1. I want to know is there a way to rollback to an earlier point in Ubuntu, with the files etc. 

I corrupted my system and all the files due to some files that I executed. I unfortunately executed it under my username. I assumed that it would ask for su rights before modifying any important file. But it didnt. 

2. Also, is  there any anti-virus or sort which I could use on the system - as A last hope ... 

Thanks

Pls help ...

---

### Post by howefield on 2009-11-11
> **ntrapped said:**
> 1. I want to know is there a way to rollback to an earlier point in Ubuntu, with the files etc.

Backintime sounds like the program you need. I don't use it so can't give a recommendation, but it seems fairly popular. I just take an image of the disk with clonezilla, and all important stuff backed up in multiple places. 

> Also, is  there any anti-virus or sort which I could use on the system - as A last hope ...

You do know that anti virus isn't required ? If you want it however, (and there are reasons why you might) read this.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by dvlchd3 on 2009-11-11
> 
2. Also, is there any anti-virus or sort which I could use on the system - as A last hope ... 

Antivirus in linux is rather pointless.  Most AV's check for Windows viruses.  Since there are really only a handful of Linux viruses, it is rather pointless to develop a AV suite like Windows users need.

Viable alternative: chkrootkit

This checks for several things within your system, i.e. viruses, files that shouldn't be there, files that were modified oddly, shell bindings (in case you have been hacked), etc.

That package is a command-line utility.  No GUI..sry.

---

### Post by ntrapped on 2009-11-11
Thanks for the replies.
Yes, I know anti-virus is pretty pointless in Ubuntu. 

But I actually downloaded a program and file, which ended up corrupting / modifying most files on my system ... and now that I am reading about it ... 
it tries to connect to remote server, which is my machine name (which is the only good part) ... 

so would want to restore it to the point when I had not done this.

I thought a good solution .. now that I have done this would be ... 
to use an antivirus
and try to rollbk..

pls giude me if you are aware of anything else that I could do.

thanks

---

### Post by howefield on 2009-11-11
> **ntrapped said:**
> But I actually downloaded a program and file, which ended up corrupting / modifying most files on my system...

And the name of this program was ?

> pls giude me if you are aware of anything else that I could do.

I don't think you will be able to retrospectively rollback, at least, not easily. If I got myself into this predicament, I'd back up my important stuff and reinstall Ubuntu.

At least, then I would know for sure I had a clean pristine system, which I could start to protect from myself by imaging the disk, looking at backintime or similar, and installing anti virus whatever. Then I could do stupid things and know I could get back to where I started easily.

---

