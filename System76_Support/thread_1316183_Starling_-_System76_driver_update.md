---
title: "Starling - System76 driver update"
date: 2009-11-05
forum: System76 Support
---

### Post by vttay03 on 2009-11-05
So I am still running the Jaunty version of UNR on my Starling and will probably continue to do so even after the System76 driver is updated for Starling support under Karmic.  Everything works so great right now that I just don't feel like messing with it for the time being.  Anyways, my question is I have an update for my System76 driver waiting for me in Update Manager.  I am currently running version 2.3.7 of the driver and assume this is the update to 2.3.9.  Is this update only intended for Karmic or should I install it as well?  Is there backwards compatibility to previous versions of Ubuntu with each driver update?

---

### Post by jmwink on 2009-11-05
The 2.3.9 is not just for Karmic. In fact, if I remember correctly, it's an important one for the Starling. Update away, my friend.

---

### Post by thomasaaron on 2009-11-06
> Is there backwards compatibility to previous versions of Ubuntu with each driver update?

Yes.

---

### Post by ligaa9mm on 2009-11-07
I have a question about how the System76 driver updater itself works. I'm another Linux n00b, but I bought a Starling running 9.04 and have loved it so far. Anyway, my question about the updater is if there's a way for it to display more information? I'd like to see what is being updated, showing at least the newest version number. One of the first updates it did knocked out my wireless card, and it took a couple more for it to come back, only now it doesn't seem to work quite as well.

So not only am I now somewhat paranoid about running the updates, but it seems that when I do, I keep installing an update and rebooting the system, then installing another update and repeating the process ad nauseum. I'm starting to doubt if the updater is actually doing anything, and if there's ever an end to it all.

Can someone shed a little more light on this for me? Thanks!

---

### Post by thomasaaron on 2009-11-09
To see what the driver is doing, run it from a terminal...

sudo system76-driver

Kernel updates can kill your wireless. Running the "Install" functionality of the driver and rebooting will re-compile the driver against the new kernel. Right now, it is necessary. At some point, though, the wireless driver should be included in the Ubuntu kernel, and running the System76 Driver should no longer be necessary.

---

### Post by ligaa9mm on 2009-11-19
So this System76 utility isn't so much an updater but a program that makes updates compatible with the Starling system? If so, is it unnecessary for me to keep running the utility except right after running the Update Manager?

I tried running it from the terminal like you suggested, and this is what it gave me:

Traceback (most recent call last):
    File &quot;/usr/bin/system76-driver&quot;, line 50, in       main()
    File &quot;/usr/bin/system76-driver&quot;, line 44, in main      os.environ['GDMSESSION'] == 'default'
    File &quot;/usr/lib/python2.6/UserDict.py&quot;, line 22, in __getitem__      raise KeyError(key)
KeyError: 'GDMSESSION'

I'm not sure what it means, and a Google search didn't tell me much. Is there a problem with my System76 utility? I've been doing a lot of experimenting with different programs and such so I wouldn't be surprised if I fudged something up somewhere.

---

### Post by thomasaaron on 2009-11-20
> So this System76 utility isn't so much an updater but a program that makes updates compatible with the Starling system?

The System76 driver is a Python program that detects your System76 model number and the version of Ubuntu you are using. Using that information, it applies any patches that may be necessary for *that* system under *that* version of Ubuntu.


```
If so, is it unnecessary for me to keep running the utility except right after running the Update Manager?
```

Running the System76 driver, and then rebooting your system, is a good first step to take if something goes wrong with your system (loss of sound, failure to suspend, etc...).

*Kernel* updates can definitely break things like wireless (on Starlings), etc... So keep an eye out for them and run the driver after loading them if necessary. General security or software updates rarely break anything. So I wouldn't worry too much about those.

> Traceback (most recent call last):
File &quot;/usr/bin/system76-driver&quot;, line 50, in main()
File &quot;/usr/bin/system76-driver&quot;, line 44, in main os.environ['GDMSESSION'] == 'default'
File &quot;/usr/lib/python2.6/UserDict.py&quot;, line 22, in __getitem__ raise KeyError(key)
KeyError: 'GDMSESSION'

If the driver is running through to completion, then that output probably doesn't matter. I'll have to run it from a terminal on a shop machine to know for sure.

---

### Post by cposs on 2009-11-20
I got that error message on my Starling, too, and it turns out that I needed to upgrade grub (Karmic moved from grub to grub2, but the dist-upgrade didn't install that one for me). To get the new grub:
```
sudo apt-get install grub-pc
```The only reason I even tried this out was because I read in a thread about audio problems that someone else had problems with grub.  I'm not sure how it would work, but ideally there would be some way to make the system76-drivers package depend on grub-pc, but only for Karmic.

I have no idea how that error message stemmed from a grub problem, but once I installed grub-pc everything went smoothly.

---

### Post by ligaa9mm on 2009-11-21
thomasaaron:
Running 'sudo system76-driver' gives me *only* that output in the terminal. I can't tell if it's doing anything else.

cposs:
Thanks for that. I tried it out, got an 'Error 11' at bootup, and had to use someone else's trick to get it to default to Grub2 on loading. But it hasn't changed the driver output in the terminal.

It did, however, fix a different error I'd get at bootup about mounting a device. If I remember right, it was referring to the card reader...

---

