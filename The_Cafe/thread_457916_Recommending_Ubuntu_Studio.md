---
title: "Recommending Ubuntu Studio"
date: 2007-05-29
forum: The Cafe
---

### Post by eks on 2007-05-29
Hello,

I'm a graphical artist that is switching to Ubuntu. I'm using Feisty and the Studio repositories.

I have a friend that works with audio production and I want to recommend Ubuntu Studio to him but since he is a little bit "less tech savvy" than I am, I have some questions. Which are:

[B]. Does Ubuntu Studio works as a Live CD? If yes, can he ran the audio programs from the Live CD?

. If he install normal Ubuntu Feisty instead of Ubuntu Studio, would someone know about a "graphical tutorial" to install Ubuntu Studio repositories and programs?[/B]


Thanks!!
eks

---

### Post by joejaxx on 2007-05-29
> **eks said:**
> Hello,

I'm a graphical artist that is switching to Ubuntu. I'm using Feisty and the Studio repositories.

I have a friend that works with audio production and I want to recommend Ubuntu Studio to him but since he is a little bit "less tech savvy" than I am, I have some questions. Which are:

[B]. Does Ubuntu Studio works as a Live CD? If yes, can he ran the audio programs from the Live CD?

. If he install normal Ubuntu Feisty instead of Ubuntu Studio, would someone know about a "graphical tutorial" to install Ubuntu Studio repositories and programs?[/B]


Thanks!!
eks


Ubuntu Studio does not work as a livecd it is only a installer cd. So he would not be able to run audio programs off the cd. I also have not seen a graphical tutorial for adding the Ubuntu Studio repositories.

---

### Post by guitarmaniac on 2007-05-29
No, sadly ubuntustudio does not run as a live cd.
However adding the repositories is quite simple.

From a terminal run these commands:
```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
```
```
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get update
```
```
sudo apt-get install ubuntustudio-desktop
```

thats it!
just copy and paste those commands and your set.

---

### Post by shen-an-doah on 2007-05-29
> **guitarmaniac said:**
> ```
sudo apt-get install ubuntustudio-desktop
```

There's a few more packages you need than just that. There's a full list in my blog, [here](http://ubuntumusic.blogspot.com/2007/05/upgrade-to-ubuntu-studio.html). Obviously you don't need all of them if he's just interested in audio work, but "ubuntustudio-audio", "wired" and probably "ubuntustudio-audio-plugins" will be definitely needed.

Edit: Also, you can skip "sudo apt-get update" in guitarmaniac's tutorial, as it's run at the end of the second command.

---

