---
title: "Serp 5 Syst76 Driver"
date: 2009-11-11
forum: System76 Support
---

### Post by wrender on 2009-11-11
Out of curiosity what does the system 76 driver do in 9.10?

Im trying to figure out something and curious if I can get away without using it to trouble shoot something.

---

### Post by thomasaaron on 2009-11-11
Version 2.3.9

1.) Add Pangolin Performance 6 (panp6)
2.) Add Karmic support
3.) Add Wildebeest Performance desktop (wilb1)
4.) Add Lemur Ultrathin laptop (lemu1)

I'm not sure of all the little details yet, though. ;)

What are you trying to do?

---

### Post by wrender on 2009-11-11
I was looking for something like this...

[http://knowledge76.com/index.php/Serp5](http://knowledge76.com/index.php/Serp5)


I am having problems mounting usb drives... They worked perfectly in 9.04. Now in 9.10 they only mount if i leave them in and reboot.

I heard some people saying something about the kernel in 9.10 is the cause... so I  may try installing a different distro for the next lil bit until they solve it.

---

### Post by thomasaaron on 2009-11-12
I see.

It isn't 9.10, per se. I've seen a couple of USB problems, touchpad problems, sound problems, etc... all related to grub2 not installing correctly.

Could you try to go to a terminal and run...

sudo apt-get install grub-pc

That will un-install the remnants of the old grub, install grub2 and re-do all of your kernel settings. I *think* that will help.

---

### Post by wrender on 2009-11-13
Some how it auto magicaly fixed itself after trying a live disc... when it rebooted it did a disk check and now everything is good!

knocking on wood! lol

ps. Are they going to update the wiki which tells what the driver is doing for 9.10?

---

### Post by wrender on 2009-11-13
I noticed that the bios version for the serp5 on the wiki says 1.00.115

Mine when it boots up says 1.00.7s

Should I upgrade the bios?

---

### Post by thomasaaron on 2009-11-13
No. Please don't. It doesn't apply any fixes to your system.

---

