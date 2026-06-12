---
title: "best guide to install Opera in ubuntu ?"
date: 2007-09-06
forum: The Cafe
---

### Post by RAV TUX on 2007-09-06
I found this guide really easy to follow:

[http://www.go2linux.org/opera-from-repository-for-ubuntu-or-debian](http://www.go2linux.org/opera-from-repository-for-ubuntu-or-debian)

---

### Post by Dr Small on 2007-09-06
It's a shame you didn't write this an hour sooner... I just installed Opera from the debian they provide on their website :p

Dr Small

---

### Post by RAV TUX on 2007-09-06
> **Dr Small said:**
> It's a shame you didn't write this an hour sooner... I just installed Opera from the debian they provide on their website :p

Dr SmallAn hour ago I was out to dinner ;)

Lets hope this helps someone else out.

---

### Post by aysiu on 2007-09-06
What about going to the Opera website, downloading the Ubuntu .deb, and double-clicking it?

---

### Post by RAV TUX on 2007-09-06
> **aysiu said:**
> What about going to the Opera website, downloading the Ubuntu .deb, and double-clicking it?I tried that it does nothing to help me figure out how to install it.

sudo apt-get install opera doesn't work until you edit the file  /etc/apt/sources.list



aysiu if you have a better way please post it here or in pschocats

---

### Post by Billy_McBong on 2007-09-06
[COLOR="Blue"]isn't opera already in repositories?[/COLOR]

---

### Post by Dr Small on 2007-09-06
> **aysiu said:**
> What about going to the Opera website, downloading the Ubuntu .deb, and double-clicking it?
That's exactly what I did, and it worked perfect for me.

---

### Post by RAV TUX on 2007-09-06
> **Billy_McBong said:**
> [COLOR=Blue]isn't opera already in repositories?[/COLOR]
nope, not that I could find


keep in mind that I haven't used ubuntu in about a year, I just installed Xubuntu so I will be asking, searching, finding and sharing alot.

I may not have the right answers but I hope to inspire dialog so that these answers can be found and shared

---

### Post by aysiu on 2007-09-06
> **RAV TUX said:**
> I tried that it does nothing to help me figure out how to install it.

sudo apt-get install opera doesn't work until you edit the file  /etc/apt/sources.list



aysiu if you have a better way please post it here or in pschocats
Double-clicking the .deb file should install it if you have gDebi installed already. If you don't have gDebi installed, just paste this command into the terminal: ```
wget -c http://ftp.wayne.edu/opera/linux/923/final/en/i386/shared/opera_9.23-20070809.6-shared-qt_en_i386.deb && sudo dpkg -i opera_9.23-20070809.6-shared-qt_en_i386.deb
```

---

### Post by RAV TUX on 2007-09-06
> **aysiu said:**
> Double-clicking the .deb file should install it if you have gDebi installed already. If you don't have gDebi installed, just paste this command into the terminal: ```
wget -c http://ftp.wayne.edu/opera/linux/923/final/en/i386/shared/opera_9.23-20070809.6-shared-qt_en_i386.deb && sudo dpkg -i opera_9.23-20070809.6-shared-qt_en_i386.deb
```

aysiu; Thanks for that I didn't have gDebi installed.

Installing it now...

Thanks alot

(please let me know, was it safe to follow that guide?)

Also I am in root, I have heard people say don't use root (su) but is this ok?

have patience with me while I rediscover ubuntu ;)

---

### Post by RAV TUX on 2007-09-06
ok installed:

this is what I got
```

 wget -c http://ftp.wayne.edu/opera/linux/923/final/en/i386/shared/opera_9.23-20070809.6-shared-qt_en_i386.deb && sudo dpkg -i opera_9.23-20070809.6-shared-qt_en_i386.deb
--22:38:21--  http://ftp.wayne.edu/opera/linux/923/final/en/i386/shared/opera_9.23-20070809.6-shared-qt_en_i386.deb
           => `opera_9.23-20070809.6-shared-qt_en_i386.deb'
Resolving ftp.wayne.edu... 141.217.1.55
Connecting to ftp.wayne.edu|141.217.1.55|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,653,754 (5.4M) [application/x-debian-package]

100%[====================================>] 5,653,754    185.31K/s    ETA 00:00

22:38:55 (165.73 KB/s) - `opera_9.23-20070809.6-shared-qt_en_i386.deb' saved [5653754/5653754]

dpkg - warning: downgrading opera from 9.23-20070809.6feisty1 to 9.23-20070809.6.
(Reading database ... 91132 files and directories currently installed.)
Preparing to replace opera 9.23-20070809.6feisty1 (using opera_9.23-20070809.6-shared-qt_en_i386.deb) ...
Unpacking replacement opera ...
Setting up opera (9.23-20070809.6) ...

```

---

### Post by John.Michael.Kane on 2007-09-06
Package: opera is listed as being in this ubuntu repo.Architecture: i386
```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
```

---

### Post by Polygon on 2007-09-06
rav... where have you been? honestly? ive seen you on these forums for like ever, how did you NOT know about gdebi? it was like the hot cool feature.... in dapper!

---

### Post by fuscia on 2007-09-06
just use automatix. bwahahahahahaaaaaaaaaa!!17

---

### Post by RAV TUX on 2007-09-06
> **Polygon said:**
> rav... where have you been? honestly? ive seen you on these forums for like ever, how did you NOT know about gdebi? it was like the hot cool feature.... in dapper!

I haven't actually used Ubuntu for quite some time, been experimenting, with every other Linux distro.

I have missed a lot....

gDebi is simply awesome!


I wonder how come I never heard about it?

oh well,....I have it now and I love it!

---

### Post by RAV TUX on 2007-09-06
> **fuscia said:**
> just use automatix. bwahahahahahaaaaaaaaaa!!17hmmm, I'll think I'll pass|18

---

### Post by tbroderick on 2007-09-06
> **RAV TUX said:**
> ok installed:

this is what I got

It's fine. It just slight different package names. I'd use the specific Ubuntu repo.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

---

