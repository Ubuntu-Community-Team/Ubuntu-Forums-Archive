---
title: "Inquiry: Advantages of thumb drive installtions"
date: 2010-02-27
forum: The Cafe
---

### Post by OwnLife on 2010-02-27
I recently bought a thumb drive with the idea of having a separate installation that I can keep updated and carry around in the event that I want/need to use my desktop on someone else's computer. 

My question is what are the pro's and con's of doing this and is this even worth the effort?

Thanks!

---

### Post by Kai69 on 2010-02-27
Is it a linux distro you want on there im asking because if you buy a Sandisk stick they come with U3 on it which is what you are asking for but its windows only dosnt work in linux [http://www.u3.com/smart/default.aspx](http://www.u3.com/smart/default.aspx) it might give you an idea.
PROS If you use it on another pc when you disconnect there is no trace of your activitys on the pc.
CONs  If you lose the stick someone can acces the drive even password protection.

If its a linux distro I would use the smallest distro I could find and just have the apps that I need on it and use the rest of the drive for holding info.

---

### Post by 2hot6ft2 on 2010-02-27
> **OwnLife said:**
> I recently bought a thumb drive with the idea of having a separate installation that I can keep updated and carry around in the event that I want/need to use my desktop on someone else's computer. 

My question is what are the pro's and con's of doing this and is this even worth the effort?

Thanks!
Just did it myself over the last few days.
Pros:
It's entertaining.
You don't have to worry about being accused of messing up someone else's pc. Windows users have no idea what you can do without even using their OS.
You can troubleshoot a windows pc from your thumb drive.
No trace of what you did on their pc...history etc..

Cons:
9.10 wouldn't boot with the hard drive in it kept dropping me to the initramfs prompt. Worked fine if there was no internal drive.
8.10 works with no problem but the network manager sucks.
It's a bit slower and that would depend a lot on the pc you put it in.

Unsure:
I don't know how it will work on a pc with a different graphics card since I installed the driver for mine.

---

### Post by OwnLife on 2010-02-28
> **Kai69 said:**
> Is it a linux distro you want on there im asking because if you buy a Sandisk stick they come with U3 on it which is what you are asking for but its windows only dosnt work in linux [http://www.u3.com/smart/default.aspx](http://www.u3.com/smart/default.aspx) it might give you an idea.
PROS If you use it on another pc when you disconnect there is no trace of your activitys on the pc.
CONs  If you lose the stick someone can acces the drive even password protection.

If its a linux distro I would use the smallest distro I could find and just have the apps that I need on it and use the rest of the drive for holding info.

I know the terrors of that U3 nonsense. Thanks for the information!

---

### Post by Lightstar on 2010-02-28
need to keep the usb linux as a live-cd type, that way it re-detects the hardware of whatever computer you plug it in, it's not stuck with your own computer's config.

It's a great thing for emergency, because some computers (like mine) only have one cd/dvd drive, so if i use a live-cd, how can I burn/backup my data?  on USB it's faster, and i can use the dvd-rom to burn stuff.

I suggest keeping linux to basic-needs, and not put your personal accounts anywhere there, only put what is needed for emergency/recovery.  So if you lose your key, you are not in danger.

It's a great idea though, I have one key I always keep just for that, helped other computers too, not just mine.

---

### Post by swisscow on 2010-02-28
Over here in Switzerland lots of school kids are given an installation of Knoppix on a thumb drive. The drive is partitioned, one for the OS and one for the data so that the you don't need to always boot from the thumb drive to access it.

The people who make it (my girlfriend works with one of them funnily enough) use Knoppix because it does so well detecting and using all different configurations, and they load it up with education software, and even 3d effects.

It's pretty cool and I've used it a few times atwork when I can't be bothered to wait for the XP to boot up or when I need to recover a lost file. Also used it when I need to do a one off like convert a music file and do not want to have to wade through windows shareware crud.

---

### Post by OwnLife on 2010-02-28
Okay! Since I have the forum open here definitely want to do Karmic on the USB. I want to reinstall on my desktop but I'm having two issues.

Mounting the ISO so I can use the built in feature, I can figure this out on my own. What I'm not sure about is this computer has a Broadcom(?) wireless card which apparently has proprietary software that can't be released with the distro, so I want to pre-install whatever is needed so the beast doesn't have to travel around my house for the physical connection.

I don't even know what was going on with the driver install, I plugged in the ethernet and half an hour later everything was updated and working. This convenience makes it hard to learn, fellows.

I forget to add, what kind of programs should I add to the usb start-up to troubleshoot microsoft? I've used BartPE in the past so I assume there are more awesome linux options for dealing with crabby windows.

---

### Post by Kai69 on 2010-02-28
> **swisscow said:**
> Over here in Switzerland lots of school kids are given an installation of Knoppix on a thumb drive. The drive is partitioned, one for the OS and one for the data so that the you don't need to always boot from the thumb drive to access it.

The people who make it (my girlfriend works with one of them funnily enough) use Knoppix because it does so well detecting and using all different configurations, and they load it up with education software, and even 3d effects.

It's pretty cool and I've used it a few times atwork when I can't be bothered to wait for the XP to boot up or when I need to recover a lost file. Also used it when I need to do a one off like convert a music file and do not want to have to wade through windows shareware crud.

Can you buy these sticks sounds like a good idea to me :P

---

### Post by -kg- on 2010-02-28
> **Kai69 said:**
> Can you buy these sticks sounds like a good idea to me :P

[Unetbootin]("http://unetbootin.sourceforge.net/")

While Knoppix is not natively supported, it can be installed using a Live CD or DVD image (and, of course, a sufficiently large thumbdrive, especially for the Live DVD image).  IOW, you can (easily!) make one yourself.

---

### Post by Kai69 on 2010-02-28
> **-kg- said:**
> [Unetbootin]("http://unetbootin.sourceforge.net/")

While Knoppix is not natively supported, it can be installed using a Live CD or DVD image (and, of course, a sufficiently large thumbdrive, especially for the Live DVD image).  IOW, you can (easily!) make one yourself.

Thanks ill look into that im now also thinking of making one of these but just with the things i need maybe on a 4gb drive :D

---

### Post by OwnLife on 2010-03-02
I'm going to bump the thread again, a relevant issue just came up. I have a friend who's XP kernel pooped and she's done with monopolysoft.

I don't know what to do once either the usb or a disc loads without making changes, how to navigate to that familiar windows file system. Also what programs would you recommend for an emergency-save-the-day-usb-installation ?

---

### Post by cariboo on 2010-03-02
What I do in a case like that, is boot from the usb thumb drive, then plug in an external hard drive, use nautilus to navigate to the users home directory, and copy all the relevant directories to the external hard drive. Jaunty(9.04)+ auto detects the internal hard drives, so it's just a matter of clicking the icon in nautilus.

I usually run nautilus as root, just in case there are any permission problems.

---

### Post by OwnLife on 2010-03-03
That's totally all I did. It was super easy, and installing from usb is the way to go I've learned. Thanks for your help.

---

### Post by NightwishFan on 2010-03-03
If you need something light go with Puppy Linux on a USB.

[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

---

### Post by J_Stanton on 2010-03-03
> **Lightstar said:**
> need to keep the usb linux as a live-cd type, that way it re-detects the hardware of whatever computer you plug it in, it's not stuck with your own computer's config. It doesn't matter what you do with it, it will recognize and have all the drivers you need. It doesnt lose anything just because you tweaked it.  for example on my desktop, i still get updates for intel video cards and toshiba laptops even though i use neither.

---

### Post by J_Stanton on 2010-03-03
> **nightwishfan said:**
> if you need something light go with puppy linux on a usb. +1

---

### Post by user1397 on 2010-03-03
:( I just bought a SanDisk usb flash drive...didn't know about the U3 thing...is there any way to permanently remove it?  (apparently just formatting it doesn't work)

---

### Post by cariboo on 2010-03-03
Go to SanDisk's web site, the have a U3 removal tool.

---

### Post by user1397 on 2010-03-03
I tried the removal program from the sandisk site, it kept giving me an error.

so i decided to try reformatting it (in windows) but with the option "quick format" unticked...and whoa and behold, it worked...no u3 popping up anymore when I insert the usb stick, awesome.

---

### Post by DZ* on 2010-03-03
> **Kai69 said:**
> CONs  If you lose the stick someone can acces the drive even password protection.

```
sudo adduser --encrypt-home MyName
```

Done.

(Ok, maybe disable or encrypt swap too and put /tmp into RAM)

I've been using a full install to a USB drive since Hardy and it works great. 

I carry the drive around and it boots on various computers.

Distribution upgrades to the same drive worked too, however I did a reinstall for Karmic because I decided to switch from a partition encryption (luks) to an account encryption (as in the above).

---

