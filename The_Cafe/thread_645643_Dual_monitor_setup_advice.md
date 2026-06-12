---
title: "Dual monitor setup advice?"
date: 2007-12-20
forum: The Cafe
---

### Post by jgrabham on 2007-12-20
In a couple of weeks I want to set up a dual (or possibly tri at some stage) monitor setup.

I have an on-board geforce 6100,but I dont know if this will work, so  Ill probabally buy a 16x PCI-E  8600 to plug my new 20 inch monitor in, and a cheap PCI card for my other monitor. 

I want a different keyboard and mouse to control each monitor (so Ill essentially have 2 systems, with only one base unit) do they all have to be USB, or can I have one set PS/2?

Anyway, I dont have a clue how to set this up, what should I be planning to do?

---

### Post by Sugi on 2007-12-20
I wouldn't know how to begin to setup different keyboards and different mouses for each monitor.  Youll probably find out it's a waste of space and time.  Most likely you'll like one keyboard and one mouse for all of your monitors.  Theres no need for multiple keybaords and mouses.  I had three monitors once for one tower.  It was heaven sent and I couldn't see myself using one monitor ever again.

What do you want to know about multiple monitors?  All I can really give to you at this moment is, try to stay away from multiple keyboards and mouse besides from it pointless (at least I would think so).  It will probably be a pain in the neck to setup, if possible.

---

### Post by jgrabham on 2007-12-20
I hardly know anything about it, Im still thing about the seperate keyboards and mice, if you think its a bad idea, Ill probably steer clear for now.

---

### Post by rsambuca on 2007-12-20
I agree with Sugi here.  Go for the extra monitor, but I really see no reason for the extra inputs.  By the way, if you are going to get the 8600, then it can run two monitors without you getting another "cheap PCI card"

---

### Post by ~LoKe on 2007-12-20
> **rsambuca said:**
> I agree with Sugi here.  Go for the extra monitor, but I really see no reason for the extra inputs.  By the way, if you are going to get the 8600, then it can run two monitors without you getting another "cheap PCI card"

Yep.  Unless you use an extremely high resolution while gaming.

---

### Post by Sugi on 2007-12-20
Just a small note:
I have played games with multiple monitors and it's awesome.  Like let me tell you, if you have any plans on playing video games on multiple monitors, get some nice video cards.  Most support for multiple monitors is the base number of three monitors.  So, think about that when you are buying your video games.

---

### Post by BobCFC on 2007-12-20
Multiple monitors is easy to set up if you have an NVIDIA card.

There is a control panel that comes with the proprietary graphics drivers try:

```

sudo nvidia-settings
``` 


You have to launch it as root so that it can save the changes to the xorg.conf file.

Basically it's sets up the screen for you so that you never have to touch xorg.conf by hand.  Choose **TwinView** to enable one big desktop spread across both the monitors, you can even tweek the brightness etc.

Then press button to save changes to xorg.conf so it remembers on reboot.

It's very smooth on modern cards.. you can drag video from one monitor to the other while it is playing with NO SLOWDOWN even with wobbly windows.  Also you can spin the cubes on compiz fusion set to one big cube across both screens


EDIT:  I agree I don't think you will need an extra cheap pci card.  Most 8x00 geforce's have two DVI outs and even come with old analogue adapters.

---

### Post by ljrossi on 2007-12-20
I whant to do the same. 

The basic idea is that 2 persons can use same computer at same time.That means 2 keyboard 2 moues 2 monitors 1 PC.

It will by nice to share computer ,meanwhile Im surfing and updating my web server, my wife can do her Skypes calls and chats with friends and familiars .

I allready have a new Flat LCD  that I use, and a the  old monitor setup on same computer. But allthougt the good dual monitors , we fight because getting control of mouse or keyboards

Old UNIX did work in that maners , with one main computer and several consoles.I guess should be posible to do it.

Julian

---

### Post by boast on 2007-12-20
I hope you don't game. :D

---

### Post by jargs on 2007-12-20
> **boast said:**
> I hope you don't game. :D

...Why?

---

### Post by aeiah on 2007-12-20
it is possible to set it up, although it wont be all that simple i wouldnt think. normally to use multiple monitors you set it up in xorg, or with some control panel setting. if you are wanting to use two keyboards and two mice, you will probably have to run two X servers. this may be even more complicated if you're using one graphics card although im not too sure. there was an ask slashdot on this sorta thing a while back. google will find it.

---

### Post by BobCFC on 2007-12-20
Hope this helps ...  it's a year old and not ubuntu specific..  but it expains how to run 6 users off a single PC!

Two should be easier lol.

[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)


Good luck


EDIT:  one thing I will say is ubuntu doesn't use /etc/inittab anymore....  when it talks about that for runlevels look for a tutorial on   **upstart**... which is the new ubuntu replacement for inittab

---

### Post by ljrossi on 2007-12-21
[http://blog.chris.tylers.info/index.php?/archives/14-Multiseat-X-Under-X11R6.97.0.html](http://blog.chris.tylers.info/index.php?/archives/14-Multiseat-X-Under-X11R6.97.0.html)

A mini Tutorial found there, looking at google =  Multiseat Linux

---

### Post by Choc_Salties on 2008-01-17
Thanks BobCFC for the nvidia settings thing! i now have 2 screens attached to my rig, with compiz working

Appreciate it!

---

### Post by bloodrose on 2008-04-26
> **boast said:**
> I hope you don't game. :D

> **jargs said:**
> ...Why?

Simply put, you'd be taxing any system trying to run 2 users while gaming. You can push a system pretty good running both a graphics-intensive game and voice chat client - let alone while someone else is even surfing the Internet, even if you have a Gigabit connection set up. It is possible, though - especially with the dropping prices of decent hardware... But I wouldn't recommend it. To each their own [computer]...

---

### Post by Jammin80503 on 2008-04-27
I have a dual monitor setup, and I got it all set up with a program called envy - it was really easy, configures it for you and all that. I'm surprised that no one has mentioned it yet.
get it here - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by herbster on 2008-04-27
Been using duals for a while, it couldn't be easier with an Nvidia dual-head card on linux. As mentioned, nvidia-settings gets it going, back that xorg.conf up and you're set.

---

