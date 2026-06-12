---
title: "Trying to install 9.10 from cd on pan5 laptop"
date: 2010-03-05
forum: System76 Support
---

### Post by bro brian on 2010-03-05
[SIZE=2][FONT=Arial Black]I'm trying to do a clean install with a cd on my Pan5 laptop,
The instructions are here: [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

The instructions say:
[/FONT][/SIZE] 1. Insert the Ubuntu Installation CD
2.  Boot from the CD by pressing either the Escape key, F8, F10, F11, or F12 (Depends on your system)
3.  Choose "Install Ubuntu" from the menu

[FONT=Arial Black][SIZE=2]My problem is that I can't get the cd to come up. Am I suppose to put the cd in, and just keep tapping the key or just press the key, and hold it in?

I know - stupid question, but I haven't been able to get past this!
[/SIZE][/FONT]

---

### Post by revlimiter on 2010-03-05
Hmmm.... 

Go into your bios. The screen usually tells you what key to hit for setup. Then change the boot order so that the system tries to boot from the CD before the HDD. 

And then change it back after you get things all installed. :)

---

### Post by marshmallow1304 on 2010-03-06
Should be F2 to get into BIOS.  After that, do as revlimiter says.

---

### Post by bro brian on 2010-03-06
[SIZE=2][FONT=Arial]Yes- Last night I went into the bios (using f2 at start-up), and changed the order of "boot up" to the cd drive first. It wouldn't work last night, however (when I got back home from work this morning), I tried it again, and it worked. So now I have done a clean install, installed the updates, and the system76 driver. I'm pretty much "good to go" now. Thanks for the input for sure! I guess my laptop had to sleep for awhile...lol

  By the way - Now for some reason, I can't seem to find compiz or metacity. the Synaptic shows that they are installed, but I don't see them anywhere (the programs). What do you think about that?

[/FONT][/SIZE]

---

### Post by revlimiter on 2010-03-07
You need to install Compiz Settings Manager... or something. 

compizconfig-settings-manager according to apt-cache search.

---

### Post by bro brian on 2010-03-07
> **revlimiter said:**
> You need to install Compiz Settings Manager... or something. 
compizconfig-settings-manager according to apt-cache search. 
OK - It wasn't installed. I installed it, and there it was. Should've known! Thanks or the help.

---

### Post by riseringseeker on 2010-03-09
> **bro brian said:**
> OK - It wasn't installed. I installed it, and there it was. Should've known! Thanks or the help.

You might also find the fusion-icon helpful, personally I use it quite a bit.

```
sudo apt-get install fusion-icon
```

---

### Post by bro brian on 2010-03-09
> **riseringseeker said:**
> You might also find the fusion-icon helpful, personally I use it quite a bit.

```
sudo apt-get install fusion-icon
```

 I was able to do that as well, and it has the metacity setting there as well. It's nice to have that right on the panel. Thanks!

---

