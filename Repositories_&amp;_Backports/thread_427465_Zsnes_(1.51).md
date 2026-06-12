---
title: "Zsnes (1.51)"
date: 2007-04-29
forum: Repositories &amp; Backports
---

### Post by teHIngo on 2007-04-29
I have been using ZSNES for years and now switched over to Ubuntu. I saw that it is available for Linux, so can  is there a possibility to get it running on Feisty :)?

Thanks in advance! Cheers :popcorn:!

---

### Post by Enfenion on 2007-04-29
Hi!
I did this to install zsnes:

```
wget http://prdownloads.sourceforge.net/zsnes/zsnes151src.tar.bz2
tar -xvf zsnes151src.tar.bz2
cd zsnes_1_51
cd src
sudo apt-get install nasm libsdl1.2-dev libncurses5-dev
./configure
make
make install
```

You might need some other packages (like gcc or g++ or something), which you can install with apt.

---

### Post by chriswyatt on 2007-05-02
This should get added to the repos.  BTW, you also need autoconf and automake, you can find out most of what you need in INSTALL.TXT.

---

### Post by Rizado on 2007-05-02
Just a tip, you should use checkinstall to install programs in Ubuntu. When doing "make install" you copy all files to were they belong but checkinstall puts them in a simple deb archive so that you easily can remove it through synaptic och whatever.

Anyway I have a debian package for zsnes and can upload it if there's any interest.

---

### Post by teHIngo on 2007-05-03
> **Rizado said:**
> Just a tip, you should use checkinstall to install programs in Ubuntu. When doing "make install" you copy all files to were they belong but checkinstall puts them in a simple deb archive so that you easily can remove it through synaptic och whatever.

Anyway I have a debian package for zsnes and can upload it if there's any interest.

Yes, there *is* interest! :)

---

### Post by dellinger on 2007-05-03
I installed Zsnes through synaptic. Looking at the packages properties it is in the multiverse repository.

---

### Post by teHIngo on 2007-05-08
I found ZSNES as a .deb :):

[http://www.getdeb.net/search.php?keywords=zsnes](http://www.getdeb.net/search.php?keywords=zsnes)

---

### Post by dfreer on 2007-05-08
I have also repackaged zsnes for feisty, you can find the link in my sig. Also, I have a repository and plan to add zsnes very soon. good luck!

EDIT: be sure to grab the latest .deb for your architecture.
The zsnes in the repos is version 1.420, the newest stable is 1.51

EDIT: the repo is up! follow these instructions to install zsnes 1.51
[http://ubuntuguide.org/wiki/Ubuntu_Feisty#Super_Nintendo_Emulator_.28ZSNES.29_1.510_for_i386.2FAMD64](http://ubuntuguide.org/wiki/Ubuntu_Feisty#Super_Nintendo_Emulator_.28ZSNES.29_1.510_for_i386.2FAMD64)

---

### Post by penvzila on 2007-05-09
Anyone know how to compile it with custom video filters?

---

### Post by dfreer on 2007-05-10
hmmm. I don't know how, but v1.51 has some filters in it's video section, is that what you are talking about? or putting your own video filters in zsnes?

---

### Post by Ryback on 2007-05-12
> **dfreer said:**
> I have also repackaged zsnes for feisty, you can find the link in my sig. Also, I have a repository and plan to add zsnes very soon. good luck!

EDIT: be sure to grab the latest .deb for your architecture.
The zsnes in the repos is version 1.420, the newest stable is 1.51

EDIT: the repo is up! follow these instructions to install zsnes 1.51
[http://ubuntuguide.org/wiki/Ubuntu_Feisty#Super_Nintendo_Emulator_.28ZSNES.29_1.510_for_i386.2FAMD64](http://ubuntuguide.org/wiki/Ubuntu_Feisty#Super_Nintendo_Emulator_.28ZSNES.29_1.510_for_i386.2FAMD64)

Thanks! Fixed me up a treat.

---

### Post by stefcep on 2008-01-05
I'd much appreciate it if someone would put a package of zsnes for amd64 Ubuntu 7.10 in synaptic?  Thank you.

---

### Post by linq on 2008-01-17
Anyone know of a way to force a 32 bit zsnes install on Gutsy 64 bit? 

I'm getting incompatible architecture errors when running make of course..

How can I fix this?

---

### Post by linq on 2008-01-17
Ah solution found for 64 bit users:

[http://ubuntuforums.org/showthread.php?t=588744&highlight=dfreer+zsnes]("http://ubuntuforums.org/showthread.php?t=588744&highlight=dfreer+zsnes")

---

