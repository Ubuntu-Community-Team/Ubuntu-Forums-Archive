---
title: "DigiBand, help."
date: 2007-09-30
forum: Ubuntu Gamers Arena
---

### Post by kevindubrow on 2007-09-30
Hi, I followed the guide to install Digiband and it worked up to the "mv DigiBand ~/.Games" command.

I get this error: "mv: cannot move `DigiBand' to a subdirectory of itself, `/home/stephen/.Games/DigiBand'"

Any clue why this is happening? I followed the guide twice up to this point and got the same error. Thanks!

---

### Post by Perfect Storm on 2007-09-30
Check if the folder names is with lower/upper letters. Sometime they change that.

---

### Post by kevindubrow on 2007-09-30
The DigiBand folder is capitalized "DigiBand" just like in the command for me. So there might be another problem. Thanks for the help.

---

### Post by Perfect Storm on 2007-09-30
```
cd ~/.Games
ls -a

```

---

### Post by kevindubrow on 2007-09-30
I get this back:
.  ..  DigiBand  (In blue text)

Are the periods the issue? They may of came from this command: cp DigiBand ..
Was I supposed to use the periods? Thanks.

---

### Post by Perfect Storm on 2007-09-30
remove the DigiBand in .Games

---

### Post by kevindubrow on 2007-09-30
Ok, I did. I just follow the guide again now?

---

### Post by Perfect Storm on 2007-09-30
Aye

---

### Post by kevindubrow on 2007-09-30
Alright, Many thanks!

---

### Post by kevindubrow on 2007-09-30
Alright, its in my menu and everything. Thanks very much! It didn't open when I clicked the icon in the menu, but I'm sure it will after a restart! Thanks again, the forums and the quick responses are why I love Ubuntu.

---

### Post by kevindubrow on 2007-09-30
Hi again, sorry for the bother. Digiband will not open. If I open with the terminal I get this message: ./DigiBand: error while loading shared libraries: libavformat.so.50: cannot open shared object file: No such file or directory

I saw something about this in another of your posts. I do have the medibuntu repos. So what else could be the problem. Thanks again for your time!

---

### Post by Perfect Storm on 2007-09-30
Is **libavformat-dev** installed (version 3.0cvs20060823...)

---

### Post by kevindubrow on 2007-09-30
Apparently, I looked it up on the internet and how to install it. I got this code: sudo apt-get install libavformat-dev

I got this response: Reading package lists... Done
Building dependency tree       
Reading state information... Done
libavformat-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Perfect Storm on 2007-09-30
When I get time I'll re-look the guide through. The problem is that the FFMPG is not up to date on feisty.

---

### Post by kevindubrow on 2007-09-30
Alright, well thanks for the help!

---

### Post by Perfect Storm on 2007-09-30
If you wait on gutsy or dare using the beta version of it.
Another option is to compile ffmpeg, but it's a bit tedious.

---

### Post by kevindubrow on 2007-09-30
Well, I honestly don't know how to even begin doing that. I think I'll just stop worrying about the game.

---

### Post by kevindubrow on 2007-09-30
I found a site, this guy runs 7.04 and got DigiBand working by upgrading FFMPEG and gave a file location to download. [http://www.happypenguin.org/show?DigiBand](http://www.happypenguin.org/show?DigiBand)

I don't know how to install though or even really know what this to be able to decide if I should upgrade or not. Is this a good way to fix the problem?

---

### Post by kopinux on 2007-10-11
anyone know how to install this start from tar.gz i downloaded?

---

### Post by chibiskuld on 2007-11-29
Got it Working!!!

2 problems, FFMPEG needs a deprecated package (sort of deprecated) installed.  Liboswego (OpenAL engine) will only compile under g++-3.4, I've just finished doing this and now it works.  I don't know if the binary will work on just anyones machine yet.  but if you feel saucy and want to compile it by hand, compile these libraries with the -dev declaritive:

apt-get install libavcodec
apt-get install libavutil (just in case)
apt-get install libavformat
apt-get install libsdl1.2debian-alsa (swap alsa with oss if you use oss, may already be installed.)
apt-get install libsdl-image1.2
apt-get install libsdl-ttf2.0-0
apt-get install libopenal
apt-get install libmad0
apt-get install libsndfile1
apt-get install g++-3.4


Pics or it didn't happen yah~~~~~:
[http://www.digiband.net/images/ubuntu.png](http://www.digiband.net/images/ubuntu.png)

btw that's ubuntu 7.1 x64

---

### Post by kevindubrow on 2007-11-29
Hey, it keep getting an error that says these packages can not be found. Am I missing a repo or something? Thanks.

By the way, I am also using 7.10 x64

---

### Post by chibiskuld on 2007-12-01
well this howto if followed correctly works perfectly:
[http://gaming.gwos.org/doku.php/guides:digiband](http://gaming.gwos.org/doku.php/guides:digiband)

Otherwise, (If that is what you are following) please post the error you are getting then I can tell you what you need to do.

I've also created an x64 Ubuntu 7.1 tarball that may come in handy, as well as a dependency install script (DOWNLOAD BOTH!):
[http://www.digiband.net/Downloads/digiband-Ubuntu-7.1-x64.tar.bz2](http://www.digiband.net/Downloads/digiband-Ubuntu-7.1-x64.tar.bz2)
[http://www.digiband.net/Downloads/installdeps.sh](http://www.digiband.net/Downloads/installdeps.sh)

---

