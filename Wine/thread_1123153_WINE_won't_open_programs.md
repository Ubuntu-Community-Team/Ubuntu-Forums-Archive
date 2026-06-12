---
title: "WINE won't open programs"
date: 2009-04-11
forum: Wine
---

### Post by Dialos on 2009-04-11
Earlier today, I'd been trying to get Final Fantasy XI to run on WINE. I'd followed [this guide]("http://www.wineffxi.org/ubuntu") and was able to get POL to work up until the actual trade-off with the game. Whenever I clicked play, I would get an error concerning Direct3D. I'm using an integrated AMD 760G chipset which was reported to have run WoW at 31 frames in 1280x1024 resolution. I assumed that my chip should be able to use Direct3D and continued to try and remedy the issue. 

While searching for answers to the problem, I came across [this guide]("http://https://help.ubuntu.com/community/RadeonDriver") in the Ubuntu Documentation section of the website. It called for me to get rid of the proprietary driver (which I did) and to edit my xorg.conf (which I also did). After doing this, It seemed I took a huge step forward, as the errors received in the terminal were cut to a mere few lines headed with: 
```

X Error of failed request:  BadMatch (invalid parameter attributes)
```

This is where the problem starts, I believe. 

I'd been so adamant in searching for a fix (without bothering the community) that I tried installing an nVidia driver. The reason I did this was because WINE had been fooling my POL Viewer Configurator into thinking that my system was using an nVidia card. After doing this, the terminal displayed an enormous amount of errors; not a single process actually succeeded in activating. I then removed the driver that I had just installed and used the CTRL+ALT+Backspace shortcut and logged out. Since then, WINE hasn't been executing any of the lines typed into terminal and when I click the program's icon, a tab comes up for a brief second and then--I guess--crashes.

Since then, I've been messing around in my xorg.conf hoping that would fix the issue.

I'm fairly new to Linux and WINE as a whole. Anyone have any ideas what I should do? If you need any extra details, don't hesitate to ask...although you might have to direct me. :s

---

### Post by asdfoo on 2009-04-11
> **Dialos said:**
> Earlier today, I'd been trying to get Final Fantasy XI to run on WINE. I'd followed [this guide]("http://www.wineffxi.org/ubuntu") and was able to get POL to work up until the actual trade-off with the game. Whenever I clicked play, I would get an error concerning Direct3D. I'm using an integrated AMD 760G chipset which was reported to have run WoW at 31 frames in 1280x1024 resolution. I assumed that my chip should be able to use Direct3D and continued to try and remedy the issue. 

While searching for answers to the problem, I came across [this guide]("http://https://help.ubuntu.com/community/RadeonDriver") in the Ubuntu Documentation section of the website. It called for me to get rid of the proprietary driver (which I did) and to edit my xorg.conf (which I also did). After doing this, It seemed I took a huge step forward, as the errors received in the terminal were cut to a mere few lines headed with: 
```

X Error of failed request:  BadMatch (invalid parameter attributes)
```

This is where the problem starts, I believe. 

I'd been so adamant in searching for a fix (without bothering the community) that I tried installing an nVidia driver. The reason I did this was because WINE had been fooling my POL Viewer Configurator into thinking that my system was using an nVidia card. After doing this, the terminal displayed an enormous amount of errors; not a single process actually succeeded in activating. I then removed the driver that I had just installed and used the CTRL+ALT+Backspace shortcut and logged out. Since then, WINE hasn't been executing any of the lines typed into terminal and when I click the program's icon, a tab comes up for a brief second and then--I guess--crashes.

Since then, I've been messing around in my xorg.conf hoping that would fix the issue.

I'm fairly new to Linux and WINE as a whole. Anyone have any ideas what I should do? If you need any extra details, don't hesitate to ask...although you might have to direct me. :s

31fps with proprietary driver is probably the best you're going to get.

suggest you get ahold of a recent nvidia card, they're quite affordable, drivers work far better than amd/ati/intel

---

### Post by Dialos on 2009-04-12
I'm...not sure you understood my question.

Just to reiterate, I'm asking if anyone has any ideas regarding a fix for my WINE. I've tried reinstalling, but it just doesn't open executable files any more. :s

---

### Post by david_kt on 2009-04-12
> **Dialos said:**
> I'm...not sure you understood my question.

Just to reiterate, I'm asking if anyone has any ideas regarding a fix for my WINE. I've tried reinstalling, but it just doesn't open executable files any more. :s

First step, try below:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and see whether or not it would help.

By the way, could you paste the output of: 

```
lspci | grep VGA
```

DK

---

### Post by Dialos on 2009-04-12
Sure thing.
```
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9616

```

---

### Post by david_kt on 2009-04-12
> **Dialos said:**
> Sure thing.
```
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9616

```

May be you should try below, choose appropriate ubuntu version:

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

DK

---

### Post by Dialos on 2009-04-12
Thanks, I'll see if it works out. :]

Edit:

It works perfectly, now. Not only is WINE opening programs again, but I've even managed to get to the character select screen with FFXI. Thanks a lot, David. ^^

---

