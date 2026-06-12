---
title: "It's too late now."
date: 2018-08-02
forum: Ubuntu, Linux and OS Chat
---

### Post by christon74 on 2018-08-02
Hello fellow UbuntersO:)

I do not really like Bionic Beaver (18.04LTS) and I very much regret the 16.04 version of Ubuntu which in my view was more intuitive and user-friendly.I know, I am just a grumpy old fart. I first tried to forced the upgrade, using the "_d" option in the terminal but did something wrong along the way. I was stuck with the ttf fonts EULA and I killed the terminal (wrong move!). I just could not remember I had to hit the tab and then the enter key to accept the agreement. Another member gave me the tip, but too late. I was far too rash in killing the terminal window, so it was my fault. As a result, Ubuntu would no longer load. Thankfully, since I am on dual boot (Windows 7) I first downloaded the iso file, burnt it to a DVD and did a fresh installation of Ubuntu 18.04 LTS. I have obviously lost some data _ but not everything_
Anyway, Ubuntu 18.04 is now correctly installed, I have to make do with it, learn to like it if I can. But I really wish I had not upgraded to Beaver.

---

### Post by sudodus on 2018-08-02
Ubuntu 16.04 LTS has long time support until April 2021, so you need not learn to like 18.04 LTS, at least not now ;-) And if you are lucky, you will like Ubuntu 20.04 LTS better.

I like 18.04 LTS, but I use the community flavour Lubuntu in my main computer because I like the ultra light desktop environment. I suggest that you [try the community flavours (Kubuntu, Ubuntu Budgie, Ubuntu MATE, ... Xubuntu) live without installing (booted from USB)](https://ubuntuforums.org/showthread.php?t=2230389).

If none of these match Ubuntu 16.04 LTS, you can reinstall your old favourite ...

---

### Post by TheFu on 2018-08-02
ALWAYS, ALWAYS, make a full, know-you-can-restore, backup before doing any major changes.  That can be system upgrades or applying patches after a month of not patching. Nothing can replace the need for backups.

And really, the things needed to be backed up can't be over 25G for the OS and applications and most files.  It is usually just media or games that require TBs and TBs of storage.
For example, my current laptop which is used multiple hours a day and only has 1 logical volume (think partition) for data is using 32G total - my HOME is 26G of that total and has thousands of photos,audio, and a few videos. That leaves just 10G for the OS and applications.   Certainly, anyone can backup 10G of stuff before doing dangerous things.

It is a similar story on my primary desktop.  16G used and 7.3G is in my HOME.
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        20G   16G  2.7G  86% /

$ du -sh ~/
7.3G    ~/
```

So under 9G is used for the OS and applications.
If you don't do great backups today, THAT should be the project solved next.

---

### Post by coffeefiend on 2018-08-02
Sorry to hear that. I have had PCs crash without having offline backups before. I know the pain.

---

### Post by poorguy on 2018-08-02
> **sudodus said:**
> 
I like 18.04 LTS, but I use the community flavour Lubuntu in my main computer because I like the ultra light desktop environment.


Exactly, ***Lubuntu 18.04*** runs like a ***bat out of hell*** on my ***2010 Dell Optiplex 380 / core 2 duo e7500 / 4.0 GB DDR3 ram***. :D

---

### Post by mastablasta on 2018-08-03
> **christon74 said:**
>  I have obviously lost some data _ but not everything_


you will then be "happy" to know that you can install without formatting the drive. this just overwrites the system files maybe some setups, but all in all you data (/home) should be left as it was. 

btw you can do the same thing in windows as well. i once wanted to forcefully remove tmp files, but i removed too many including some system files. i just reinstalled without formatting and nearly all settings were there + i kept all the personal files and data.

---

