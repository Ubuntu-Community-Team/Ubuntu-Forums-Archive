---
title: "Ubuntu 15.04 to 15.10: Fresh install or Upgrade?"
date: 2015-05-11
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2015-05-11
Hi everyone,

I finally got my printer working last week (HPLIP 3.15.4) and Ubuntu 15.04 is so quite and stable (no problem at all) that I wish to try Wily Werewolf.  Should I Upgrade via software updater or do a fresh install.?  Running Vivid alone, what should I do?.

---

### Post by MikeMecanic on 2015-05-11
Ubuntu 15.10 is not available via Software Updater but there is a huge patch of 150Mb if you check Pre-released updates (Vivid-proposed).  Last time I did that (Ubuntu 15.04 B2) my computer crash.  This time it didn't. and kernel is at 3.19.0.17.  So will do a fresh install later on this week to see that gipsywort again.
```
$ uname -r
3.19.0-17-generic
```

---

### Post by cariboo on 2015-05-12
If you want to upgrade your current install in a terminal, use the following command:

```
sudo sed -i 's/vivid/wily/g' /etc/apt/sources.list
```

then:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by MikeMecanic on 2015-05-12
Thanks for the upgrade terminal commands,_ will try it first tonight_.  Bur I already built a MKUSB stick (1.01GB):  Download the daily image (AMD64) of Ubuntu 15.10 from here: 
Built the ISO image from there (Stable Version of MKUSB):  [https://help.ubuntu.com/community/mkusb/v9#Installation](https://help.ubuntu.com/community/mkusb/v9#Installation)
When correctly built the ISO image contains 14 files, including the purple one wubi.exe and the code name is **Wily Werewolf Alpha** AMD64.

**Made an error, the link for the daily image of Ubuntu 15.10 is not the good one (I erase it).   This is the one: [http://cdimage.ubuntu.com/daily-live/20150511/](http://cdimage.ubuntu.com/daily-live/20150511/)**
Thanks to:  [COLOR=#424242][COLOR=#000000]Mateusz Stachowski[/COLOR][/COLOR][COLOR=#424242] [/COLOR]

Regards,

---

### Post by cariboo on 2015-05-12
> **MikeMecanic said:**
> the code name is **Wily Werewolf Alpha** AMD64.

Regards,

That should be pre-alpha :)

---

### Post by sudodus on 2015-05-12
I tested live and made fresh installs from the Lubuntu desktop and alternate iso files. I flashed the iso files to USB with mkusb. The basic things work as they should (but I found an issue with cryptswap in the test-case [Alternate Install (Encryption)]("http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/93235/testcases/1439/results"), which is a regression since Vivid).

*Edit*: cryptswap works again in the current daily build :-)

---

### Post by Mateusz Stachowski on 2015-05-12
> **MikeMecanic said:**
> Thanks for the upgrade terminal commands,_ will try it first tonight_.  Bur I already built a MKUSB stick (1.01GB):  Download the daily image (AMD64) of Ubuntu 15.10 from here: [http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)
Built the ISO image from there (Stable Version of MKUSB):  [https://help.ubuntu.com/community/mkusb/v9#Installation](https://help.ubuntu.com/community/mkusb/v9#Installation)
When correctly built the ISO image contains 14 files, including the purple one wubi.exe and the code name is **Wily Werewolf Alpha** AMD64.

Regards,

You downloaded Ubuntu Desktop Next this flavour has Unity 8 and Mir. Currently it isn't usable on desktop so don't install that.

The regular Ubuntu with Unity 7 is here:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

but that still has only Vivid images. In pending there are Wily images:

[http://cdimage.ubuntu.com/daily-live/pending/](http://cdimage.ubuntu.com/daily-live/pending/)

---

### Post by sammiev on 2015-05-12
Hi Mike,

Hope you are using 15.10 for testing and not as your main OS.

Breakage will happen over the cycle.

---

### Post by grahammechanical on 2015-05-12
If you want my opinion, I would not run any development release as the only version of Ubuntu on my system. If 15.04 is working fine for you and you want to try out the future 15.10, then dual boot with it. I have found that the development version has been very stable for the last few cycles but that does not mean that we may not need to re-install to clear away something that is broken.

To give an example. On one of my vivid installs the switch over to systemd gave an unacceptably long loading time. I was not interested in tracking the problem down so, I re-installed.

Also keep in mind that it seems that we shall have 2 versions of 15.10 to test for Ubuntu at least. One version built on Debian packages and updated using apt-get just like every version of Ubuntu that we have seen and a version of Ubuntu built on Ubuntu snappy core. I think that the only way to get that version is from an install of an ISO image which we are many weeks away from getting. And it will be a long time before Ubuntu Snappy Desktop will be the equal of the present Ubuntu Desktop. But an interesting journey anyway.

Regards.

---

### Post by MikeMecanic on 2015-05-12
Got it according to Upgrade Terminal Commands of post # 3 and it's a very long upgrade.  Thanks to Cariboo

```
ibm@IBM:~$ unity --version
unity 7.3.2
ibm@IBM:~$  lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Wily Werewolf (development branch)
Release:	15.10
Codename:	wily
ibm@IBM:~$  uname -a
Linux IBM **3.19.0-17-generic #17-Ubuntu SMP Wed May 6 16:46:12 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux**
ibm@IBM:~$ 

```

It is not shown in About This Computer: Vivid is still there.
Stable and nothing abnormal...

---

### Post by MikeMecanic on 2015-05-12
Your telling me not to install the Daily image that I built and the first link refer to Vivid while the second is a pending one?  What's that mean? ** Should I built the ISO image according to the pending link?**

---

### Post by cariboo on 2015-05-12
About This Computer won't chnage until much later in the cycle.

---

### Post by MikeMecanic on 2015-05-13
Ok!  Got the link now and things are very well explain here: [http://ubuntuforums.org/showthread.php?t=2276942](http://ubuntuforums.org/showthread.php?t=2276942)
Thanks to Cariboo again.  Will redo the mkusb ISO image according to the link provided by Cariboo: [http://cdimage.ubuntu.com/daily-live/20150511/](http://cdimage.ubuntu.com/daily-live/20150511/)
Will be ready to install it before the end of the week.
I enable yesterday Pre-released updates and I'm running the last version of Kernel: the .17 one.  It's disable now.  Is there is something wrong with that?  

All the best,

---

### Post by MikeMecanic on 2015-05-13
I shouldn't ask the Kernel question because on an Intel Motherboard it's rarely if never an issue.  In 2 words, the last upgrade (post # 3) is quite and stable. I now have 3 Kernel versions (.15,.16 and .17)  and because of that my bootable partition of 255MB is now at 46.5% full.  Here's the best way to delete the oldest one (you must have 3 Kernel versions to do so).  **In Synaptic Package Manager: Status / Installed (auto removable) / Mark for complete removal / Delete or apply.**  3.19.0.15 is gone with the wind and the bootable partition is back to normal: 20% full.
Thanks for the advices

---

### Post by cariboo on 2015-05-13
You can use synaptic to remove the kernels you don't need, or open a terminal and run the following commands

```
sudo apt-get autoremove
```

followed by

```
sudo apt-get autoclean
```

---

### Post by MikeMecanic on 2015-05-14
Still, I would open Synaptic to see if it's correctly erased and to verified if 2 Kernel versions remain (That's the GUI Interface approach).  And please don't tell no one, some time I run only one Kernel Version, the last one.

---

### Post by MikeMecanic on 2015-05-14
[B]May 14th 2015

This thread ends the Vivid Vervet cycle for me[/B].  Being half way between Vivid and Wily and run it alone since day one (B1).  The Ubuntu 15.04 Final Release was upgraded 3 days ago successfully.  Will go forward tomorrow with a fresh install of Wily Werewolf first alpha release.


In conclusion, this upgrade is more stable then 12.LTS to 14.LTS one.  I rarely Upgrade, I'm more on the fresh install side but for testing purposes I give you guys an A+ for this one. 

When I applied the Wily upgrade (post#3), the original setting that I previously made under Vivid Final Release remain unchanged.  The same apply for the last 72 hours regarding the updates in Software Updater (on fire since 3 days).  **The Date and Time issue **(halfway working in my case in the Vivid cycle: able to change the New-York setting but not able to add another city) i**s solved under the Wily upgrad**e. This one was a long journey but now I'm able to see at what time uncle Georges goes to bed in Geneva.  Wily Werewolf pass the test of my favorite hot spot on Internet:  Ubuntu 15.10 on NHL Gamecenter gives an exceptional visual rendering (HD quality @ 3000Kps @ best).  


**Things that I lost in the Vivid cycle**:


1)  The hp-doctor terminal command and therefore my printer: HP laserjet 1020.  Lost it between 14.04.1 and 14.04.2LTS:  The terminal command is not properly working since then.  Was shifting between Vivid and Trusty for printing purposes: mom's always need is Medicare In$urance report yesterday.  Try it under Final Release and the drivers were not properly installed but an Internet link was shown in the terminal (at the end) related to HPLIP. That's how I get the drivers: HPLIP 3.15.4
```
hp-doctor

```

2)  In Final Release only, the possibility of running the last Kernel Version alone (A suicidal approach some may say): Synaptic wouldn't allow me to delete the .15 one and run the .16 alone?  **This is the last test I will do under the Vivid cycle: running 3.19.0.17 alone for half a day.**


[B]_Things that when wron_g (I installed Vivid Vervet more then 20 times)

[/B]
**Unity Tweak Tool:**  first half of desktop setting are dead, no change, no effect.  Plus, when you removed it, the original setting remains.  You must reinstall it to go back to Vivid environment or Unity original setup.
**On first installation: **
1)  Slow Internet speed (many new things are shown there);
2)  Unstable desktop environment;
3)  False motherboard reading (RAM and HDD) in **About This Computer** (sometime way out);
4)  Ubuntu Software Center with dark black and grey screen that end in a dead screen and if you try more then 2 installations at the same time, you pile them, a second Windows opens and the freezing one   remains.  I reported that Problem to the Opera team;
5)  **If I don't install Google Chrome first**, **I got Adobe Flash Player problems in Opera Stable 27,28,29** (please forward that one because I never reported that issue and It seems to be a Chromium issue);
6)  There is no need to install Adobe Flash Player if Google Chrome is installed first, the same apply for (not 100% sure on that one but I run Vivid without installing it) Java;
7)  These are what comes to my mind and they are fine tunning issues.  It doesn't take me much to do a second installation. ** I said twice in the Ubuntu forum that Ubuntu runs at best when it's installed from Ubuntu and these are some of the reasons...**


I learned in that cycle that to reach stability, we must stay basic on post installation: shoot for MAC compatible devices (our terminal cousin) and avoid doing too much.  That is the main lesson of Vivid Vervet.


[B]Things that I gain from Vivid Vervet

[/B]
1)  The visualize rendering:  HD quality is now set to high
2)  From Ubuntu After Install 2.6 Beta (IT'S F.O.S.S):  My weather Indicator (beside the network icon), set to Yahoo weather center it runs like a swiss clock (lost it in the 12.LTS to 14.LTS switch)
3) ** HIGH LEVEL OF STABILITY ON A LVM MANNER (255MB bootable partition and a 4.2GB SWAP partition that I clean ounce in a wild)** **ON THE SECOND AND THIRD INSTALLATION**: Default installation / LVM / New-York  /_without the third party codecs_.  [COLOR=#ff0000]**This upgrade is the finality: Smooth. stable and quite.**[/COLOR]  A perfect one!  Good work guys!  


**My last test under Vivid: I'M now running the last kernel version alone, the 3.19.0.17 one and this time Synaptic allow me to do so.**

[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)


See you then,

---

### Post by MikeMecanic on 2015-05-15
I'm out of the testing cycle  

Bye Bye Vivid ):P

---

### Post by steveo314 on 2015-06-25
> **cariboo said:**
> If you want to upgrade your current install in a terminal, use the following command:

```
sudo sed -i 's/vivid/wily/g' /etc/apt/sources.list
```

then:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Follow this to go to the next version except be careful with dist-upgrade when Ubuntu Devel is in Alpha. There may be breakages.

---

### Post by hackbinary on 2015-09-04
> **cariboo said:**
> If you want to upgrade your current install in a terminal, use the following command:

```
sudo sed -i 's/vivid/wily/g' /etc/apt/sources.list
```

then:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

No, to run a 'development' upgrade, you should use:

```
sudo do-release-upgrade -d
```

The Ubuntu upgrader has many advantages to updating the apt repository configuration manually, such as:
[LIST]
[*] making it safe(r) to run remotely through ssh because the Ubuntu upgrader starts a screen session and starts a new sshd session on port 1022. 
[*]Advises you of the package change-set and lets you back out sensibly if you do not like the proposed changes. 
[*]Gives you a reasonable estimate on how long it will take to download the packages you need to upgrade 
[/LIST]

---

### Post by cariboo on 2015-09-04
> **hackbinary said:**
> No, to run a 'development' upgrade, you should use:

```
sudo do-release-upgrade -d
```

The Ubuntu upgrader has many advantages to updating the apt repository configuration manually, such as:
[LIST]
[*] making it safe(r) to run remotely through ssh because the Ubuntu upgrader starts a screen session and starts a new sshd session on port 1022. 
[*]Advises you of the package change-set and lets you back out sensibly if you do not like the proposed changes. 
[*]Gives you a reasonable estimate on how long it will take to download the packages you need to upgrade 
[/LIST]

The commands you quoted are used when the toolchain is first uploaded for the next testing version a couple of days after the final version is released. Update manager doesn't show anything about the development version for a couple of months after that. I agree there could be problems using the commands, but for those of us that want to get in on the development version as soon as possible this is the only way you can do it.

Keep in mind that most of us in this sub-forum have been using development versions for several years, and we know how to solve any problems that arise. Check out the sticky [here]("http://ubuntuforums.org/showthread.php?t=2276942"). The sticky has been continually update since before I took it over during intrepid development cycle.

---

### Post by portugalthephilosoph on 2015-10-22
>[COLOR=#000000][FONT=Ubuntu Mono]3.19.0-17-generic

I'm on [/FONT][/COLOR]3.19.0-31-generic

---

### Post by MikeMecanic on 2015-10-22
Turn on Wily proposed an hour ago (hard to wait):


Update/Software & Updates/Updates/Enable Pre-Release Update (Wily Proposed)/Re-load
And
```
sudo apt-get update && sudo apt-get dist-upgrade
```
Then
```
sudo update-manager -d
```


Software updater is up-to-date.  **Not there yet!**

wily@hp:~$ uname -r
4.2.0-16-generic
wily@hp:~$

---

