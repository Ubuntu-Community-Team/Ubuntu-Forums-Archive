---
title: "Laptop Shuts off during XP Install. Overheating!!!"
date: 2008-11-05
forum: Windows
---

### Post by kestal on 2008-11-05
I have a major problem here. My laptop overheats during the XP install (like, within the first 15 minutes of it actually installing). Its not an OEM but a store-bought copy of the CD (years ago, but still).

I no longer have my rescue disks (haven't really needed them since I have been using Ubuntu on it). I wanted to Dualboot and to my surprise, I couldn't even get through the installation.

Cooling Pads do not help. Its an older laptop and it has been cleaned out and thermal paste has been re-applied (That somewhat helped, as normally it would have shut down after the first 5).

What can I do? I can get through the Ubuntu 8.04 and 8.10 installation without it even getting warm on my lap. Should I use some kind of virtual software under Ubuntu to install it? What are my options? (with pausing options, maybe?)

Its definitely out of warranty, but I cannot part with it just yet.

**Extra Info:**
Its the strangest thing, during the XP install it gets so hot that it even smells like its about ready to burst in flames.. I'd rather not do that again. Its not comforting to smell burnt plastic half way through an XP Install. >_<

**Specs:**
Gateway 7422gx
1gb of ram
80gb hardrive
2.2ghz CPU (Single-core).

---

### Post by smoker on 2008-11-05
> **kestal said:**
> I have a major problem here. My laptop overheats during the XP install (like, within the first 15 minutes of it actually installing). Its not an OEM but a store-bought copy of the CD (years ago, but still)...

...Its the strangest thing, during the XP install it gets so hot that it even smells like its about ready to burst in flames.. I'd rather not do that again. Its not comforting to smell burnt plastic half way through an XP Install. >_<

unless you cure the overheating you are only going to cause more damage. can you check the cpu temp in the bios, if so, and if the cpu is overheating (even after reseating and repasting), it may need replaced. if it is the hard drive that is overheating (formatting with xp at the start of an install will cause lengthy exercise of the drive), then replace it. you should be able to download a diagnostic from the hard drive manufacturers support site that will check the mechanics of the drive.

i've never came across it myself, but i believe a laptop battery can also be a cause of severe overheating, have you tried it with mains power only and the battery disconnected?

---

### Post by kestal on 2008-11-05
It is the CPU. Not the Hardrive. I remember that it was a problem before when I had my recovery disc's and actually managed to get XP on (plus checking Speedfan). I switched to Ubuntu and that solved everything, but now I wish to Dualboot, but cannot install XP due to that. (even if its completely formatted, as its easier to install XP first then Ubuntu, to let Grub take over).

[COLOR="DimGray"](When I ran my Speedfan a while back, I remember that full throttle/load the HDD was at about 45-50c (which is supposedly about normal for my laptop, unfortunetely), and CPU cuts into automatic thermal shutdown at about 70-75c.) -- this was a common problem I read, for my laptop. I won it. >_<[/COLOR]

Again, Ubuntu installs fine. Is there a program in Ubuntu that could let me virtually install XP on a different partition, within Ubuntu? Even through Wine that work to a significant degree?

I tried the battery bit, but unfortunetely with mine, it throttles when it needs to and there are no options in my bios to change that. I manage to get it to 1.6ghz in Ubuntu and it works perfectly, with NO overheating using one of the CPU freq applets. I will just deal with the bootloader vs grub mess later, if anything create a 3rd partition and put Ubuntu back on it later. or something.

---

### Post by blackraven36 on 2008-11-06
Your overheat has nothing to do with Windows, it will do the same thing with Ubuntu. What I would recommend doing is if your warranty is finished, open the back and take and clean out any heat sinks you find, the problem is probably caused by heat sink being clogged with dust. (PLEASE KNOW WHAT YOUR DOING BEFORE OPENING THE BACK!)

---

### Post by kestal on 2008-11-06
did you just ignore what I said? its perfectly fine in Ubuntu. No overheating. I can install Ubuntu just fine from a formatted drive. I cannot go through the XP install. Heat sink is clean. Like mentioned, Warranty is done. Its an old laptop.

So saying that my overheating problem has nothing to do with it is partly true, but if you would have read my post you would have noticed that I *still* cant complete the XP install, despite the fact that I can complete Ubuntu install without it heating up at all.

So with that said, are there any programs that I can use (through Wine, in Ubuntu), that you think I should try? (and preferably free)

I am trying to find a way to virtually install XP through Ubuntu. (either through an Ubuntu program or an XP program, through Wine)

---

### Post by smoker on 2008-11-06
hi, i would still check out the hard drive, even it is not the chief offender in the overheating, lengthy overheating of the cpu in the confined space of a laptop can have caused a lot of damage.

as to xp, you could install 'virtualbox' thru synaptic in ubuntu and try installing xp on it. some info here:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by ronnielsen1 on 2008-11-06
> as to xp, you could install 'virtualbox' thru synaptic in ubuntu and try installing xp on it. some info here:

not on 1G of ram

---

### Post by smoker on 2008-11-06
> **ronnielsen1 said:**
> not on 1G of ram

> **Memory.** Depending on what guest operating systems you want to run, you will need at least 512 MB of RAM (but probably more, and the more the better). Basically, you will need whatever your host operating system needs to run comfortably, plus the amount that the guest operating system needs. So, if you want to run Windows XP on Windows XP, you probably won't enjoy the experience much with less than 1 GB of RAM. If you want to try out Windows Vista in a guest, it will refuse to install if it is given less than 512 MB RAM, so you'll need that for the guest alone, plus the memory your operating system normally needs. 
[http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation)

---

### Post by ronnielsen1 on 2008-11-06
I know I tried it in qemu with a total of 1.5 GB ram and xp was slowwww! 98 ran like a champ

---

### Post by marsmissionaries on 2008-11-06
Put the machine in the freezer while installing.

---

### Post by Battie on 2008-11-07
You *might* be just fine running XP with less than 512 mb ram in the virtualbox, depending on what you want to do.

Since our admin tools at work have not yet been approved on Vista, I'm running them on XP in Virtualbox (or MS Virtual PC on my laptop).  I can have several light applications running at once and use less than the alloted 256 mb ram.  It idles below 192 mb ram.  I just turned of themes.

It can't hurt your laptop worse if you try it.  I'm not sure it will not overheat even in a virtual pc, but it's another option, at least.

---

### Post by kestal on 2008-11-08
I just want to be able to install XP through Ubuntu. cuz at least through Ubuntu I can set my clock/frequency lower (and that tends to also help with heat issues, anyway).

I hope the freezer comment was somewhat sarcastic, lol... I dont think that would be safe?

---

### Post by starcannon on 2008-11-10
I have VB running on an old Dell Inspiron | 5150 with 1gb of ram, works flawlessly.
When I set up the Virtual Machine for XP I gave it 256mb of ram, and a 16mb video card setting. XP runs very fast, and very smooth with these settings. About the only troublesome thing with Virtual Box is setting up USB, but if you follow the docs at the VB website you should be fine with that.

GL and have fun.

P.S. the only thing the freezer might do is cause condensation, that would be bad; I would not do a freezer install lol.

---

### Post by kestal on 2008-11-10
> P.S. the only thing the freezer might do is cause condensation, that would be bad; I would not do a freezer install lol.

I wasn't planning on it ;) it just made me giggle a bit. :) but thanks for the info. I just wish to dualboot and just can't do a basic install anymore. yay for hardware failure/overheating. lol!

---

