---
title: "E-Sword on Ubuntu 10.10"
date: 2011-01-18
forum: Ubuntu Christian Edition
---

### Post by pauloz on 2011-01-18
Hello to all e-Sword experts:

I've recently commenced using Ubuntu 10.10 and I have questions to ask about the reliability of e-Sword under Linux. I'm an extensive user of e-Sword under Windows and have found it to run flawlessly - it is indispensable for my Bible study.

A few months ago, I experimented using e-Sword under Jolicloud - a Linux distro BUT I found it to be "clunky" and froze frequently. I installed it using CrossOver ([http://www.codeweavers.com/via/e-sword](http://www.codeweavers.com/via/e-sword)) which I am led to believe, and correct me if I'm wrong, is a type of big brother to Wine. CodeWeavers gave it a silver medal, which I assume means a few little bugs but otherwise adequate.

I'm pretty keen to wean myself off Windows - the only reason I keep Windows on my netbook is due to e-Sword. I would appreciate if you could respond to these queries:

1. Can e-Sword run flawlessly on Ubuntu 10.10? If so, can you give me any tips 'n tricks for it to do so?

2. Which is better - installing e-Sword through CrossOver OR Wine?

3. I'm a heavy note user and for reasons I won't go into, I'll need to transfer my Journal, Study and Topic notes (the jnlx, notx and topx files respectively) over to a Windows based e-Sword program. Can this be done?

By the way, I don't use UCE (I have Ubuntu Desktop Edition 10.10 on my netbook and it's working grand) but I thought I'd get the most response using the UCE forum.

Thanks in advance:)

---

### Post by jonathonblake on 2011-01-18
> **pauloz said:**
> about the reliability of e-Sword under Linux.

Which version of e-Sword?

There are a couple of things in e-Sword 9.8.2 that don't work under WINE, the way they in Windows. The one that most users will notice is Resource Download Manager functionality.

OTOH, there are things that can be done under WINE, with e-Sword 9.7.2, that can not be done in Windows. (For the record, I do not recommend users to do those things, regardless of platform.)

> 1. Can e-Sword run flawlessly on Ubuntu 10.10?

Yes.

As far as tips and tricks goes, a lot of that depends upon what customizations of the Windows Registry you know how to do.


> 2. Which is better - installing e-Sword through CrossOver OR Wine?

Initially, I'd say that this is a toss up. However, CrossOver has a slight edge, if you run two or more instances of e-Sword at the same time. CrossOver also has the edge, if you want to use two or more different versions of e-Sword. 

> 3. I'm a heavy note user and for reasons I won't go into, I'll need to transfer my Journal, Study and Topic notes (the jnlx, notx and topx files respectively) over to a Windows based e-Sword program. Can this be done?

Yes.

a) Copy those files to backup.filename.extenion;

b) If the file names are topic.topx, journal.jnlx, or study.notx, rename them to something else. [For various reasons, using the default file name is never a good idea.];

c) Burn your e-Sword user directory and e-Sword program directory to DVDs. Make sure that you can easily tell which files were in the user directory and which files were in the program directory.
[I put them in a directory named user and program, respectively.];

d) Verify that your backup DVDs are good. That they have no errors.  Making two sets of backup DVDs is a good way to ensure that you won't lose your e-Sword data.  (Keep the second set with a friend that lives far away.);

e) After you have installed e-Sword on your *Nix box, get those DVDs and copy the resources into the appropriate directories on your *Nix box.
[  I use /home/jblake/e-Sword/program as the program directory and /home/jblake/e-Sword/ as the user directory, and /home/jblake/e-Sword/STEP as the STEP resource directory. ];

f) Backup user.reg in your WINE or CrossOver folder. Make sure that it is named something that won't be written over, or deleted by another program;

g) Now start e-Sword and configure/customise it to the extent that you can do so from within the program.  Close e-Sword. Make another backup of user.reg. Now, if you want to do any customizations that can only be done by configuring the Windows Registry, do it now;

h) Your e-Sword setup on *Nix should now be functionally equivalent to that on Windows. Well, one caveat: Currently, there is no *Nix equivalent of the Smart Starter Tool;

jonathon

---

### Post by pauloz on 2011-01-19
Jonathon - thanks for a most comprehensive reply. I must admit a fair amount of it has gone way over my head, but I'll certainly give it a try.

---

