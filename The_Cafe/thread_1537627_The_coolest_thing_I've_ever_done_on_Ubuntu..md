---
title: "The coolest thing I've ever done on Ubuntu."
date: 2010-07-23
forum: The Cafe
---

### Post by Starks on 2010-07-23
Installing Windows to a raw partition using VirtualBox in order to create a dual-boot.

Browsing the web while installing Windows is something Microsoft would never even dream of with their licensing.

---

### Post by Rasa1111 on 2010-07-23
lol cool. 

I dont think I can talk about the coolest thing ive ever done in Ubuntu..
for nat. sec. reasons. :lol: lol :p

it amazes me more and more every day though. :D

---

### Post by CCoder on 2010-07-23
> **Rasa1111 said:**
> lol cool. 

I dont think I can talk about the coolest thing ive ever done in Ubuntu..
for nat. sec. reasons. :lol:  :p

it amazes me more and more every day though. :D
I am interested :D

---

### Post by ubunterooster on 2010-07-23
Try running Ubuntu in windows in Ubuntu :D Just for kicks

---

### Post by Rasa1111 on 2010-07-23
> **CCoder said:**
> I am interested :D

lol, 
good, 
enough interest in the right areas can get you some good stuff. lol. ;)

---

### Post by linux18 on 2010-07-23
> **ubunterooster said:**
> Try running Ubuntu in windows in Ubuntu :D Just for kicks
with my computer, I can transcode video in windows  in ubuntu in windows in ubuntu, of course im using a very lightweight / customized windows and ubuntu.

---

### Post by Rasa1111 on 2010-07-23
> **linux18 said:**
> with my computer, I can transcode video in windows  in ubuntu in windows in ubuntu, of course im using a very lightweight / customized windows and ubuntu.

why?
is there a point to this?
or is it just for kicks?
im windoze free anyway, just wondering why. lol

---

### Post by ubunterooster on 2010-07-23
> **Rasa1111 said:**
> why?
is there a point to this?
or is it just for kicks?
im windoze free anyway, just wondering why. lol
Yup, just for kicks :lolflag:

---

### Post by linux18 on 2010-07-23
> **ubunterooster said:**
> Yup, just for kicks :lolflag:
I might just have too much free time ( see my post #9 here: [http://ubuntuforums.org/showthread.php?t=1537605](http://ubuntuforums.org/showthread.php?t=1537605) ) but it sure is fun!

---

### Post by undecim on 2010-07-23
I had to do that with VirtualBox just recently, because the Windows installer wouldn't work on my hardware. It was funny that it told me from the installer on the CD that it didn't have the necesarry drivers to read the CD, but yet it still let me browse the CD to search for drivers. Using VirtualBox for the first part of the installation though worked out fine.

Also, this has nothing to do with Ubuntu, but I once installed Arch Linux without rebooting. It was on an EeePC. I was able to find a terminal on the crippled Linux OS that comes with them, then create a small chroot in a ramdisk from which to run the installer. Once it was all done, I continued to install packages, create a user, install GDM, and set up the system just like I like it, then one reboot into the installed system and I was good to go.

---

### Post by Khakilang on 2010-07-23
I try Virtual OSE at first but couldn't get the USB to work and so I download the PUEL version thinking I had to use the command line to install. But after the download I just click on the file and it install by itself and able to install Window XP and activate the USB port. I may not be that cool but Ubuntu is cool.

---

### Post by Rasa1111 on 2010-07-23
> **ubunterooster said:**
> Yup, just for kicks :lolflag:

lol, cool. :)

that is a good way to learn for sure. 

ahhhh the things interest can get us.. lol:KS

---

### Post by mkendall on 2010-07-23
> **ubunterooster said:**
> Yup, just for kicks :lolflag:

But don't it seem that Kicks just keep getting harder to find? And all your kicks ain't bringin' you peace of mind?

---

### Post by Starks on 2010-07-24
chrooting into a broken ubuntu install is also one of the cooler things i've done.

---

### Post by ubunterooster on 2010-07-24
> **mkendall said:**
> But don't it seem that Kicks just keep getting harder to find? And all your kicks ain't bringin' you peace of mind?
Yes, it does keep getting harder but I keep getting better so it is an endless cycle and I like it that way :D

---

### Post by chriswyatt on 2010-07-24
Has there been a world record attempt for the most virtualised operating systems (i.e. OS in OS in OS in OS etc.)?

---

### Post by ronnielsen1 on 2010-07-24
> Try running Ubuntu in windows in Ubuntu

Love it! :D Windows takes too long to install but I have installed gOS inside Linux Mint inside Ubuntu

---

### Post by CCoder on 2010-07-24
Try running Mac in Windows in Linux Mint in Ubuntu :lol:

---

### Post by undecim on 2010-07-24
> **CCoder said:**
> Try running Mac in Windows in Linux Mint in Ubuntu :lol:

... in bsd, in Haiku, in DOS, in OS/2

---

### Post by TeoBigusGeekus on 2010-07-24
> **ubunterooster said:**
> Try running Ubuntu in windows in Ubuntu :D Just for kicks

Yo dawg... :p

---

### Post by phrostbyte on 2010-07-24
So I am guessing Virtualbox has advanced in this aspect? Have you been able to use the same OS image as a VM and as a dual boot?

---

### Post by Starks on 2010-07-24
Yes. It's quite fascinating. Windows 7 is flexible enough in its driver detection to allow it.

---

### Post by undecim on 2010-07-24
> **phrostbyte said:**
> So I am guessing Virtualbox has advanced in this aspect? Have you been able to use the same OS image as a VM and as a dual boot?

Yup. You can make a special virtual disk that uses /dev/sda to store its info. Permissions on it tend to be a pain though.

---

### Post by undecim on 2010-07-24
Question: Can you use hardware virtualization with the VM inside of a VM?

---

### Post by Starks on 2010-07-24
> **undecim said:**
> Yup. You can make a special virtual disk that uses /dev/sda to store its info. Permissions on it tend to be a pain though.
You don't use a full disk image. Just image the partition that contains /boot and the blank partition for Windows.

In the end though, you still need to do a gksu'd Vbox environment.

---

### Post by phrostbyte on 2010-07-24
> **Starks said:**
> Yes. It's quite fascinating. Windows 7 is flexible enough in its driver detection to allow it.

I would be careful though, definitely back up everything you have on the Windows side regularly. :)

---

### Post by SoFl W on 2010-07-24
I have one of those discovered "You didn't know you could do that?" things.  After years of using pscp, putty and the command line (Windows and Linux) for everything, I now use a book marked "connect to server..." ssh connection so my remote servers act like local drives when I need them to.
It isn't a big deal but I am old school and was always used to the command line.  Had all these macros and functions set up to make things easier before.

I remember when an Avid video editing system cost $80,000.  I told someone when they got down to about $30,000 that someday people would have them for home.  The person laughed at me.  Linux offers very decent open source video editing tools.

---

### Post by murderslastcrow on 2010-07-24
Lol, I love how a lot of these 'coolest things' are activities most common computers don't understand the significance of. "I run Windows all the time, what's so cool about running it like that?" Like, Virtualization and things like that make no sense to Windows users unless you explain to them what Linux is.

But yeah, outside of running dozens of programs at once without ever having an inkling of a slowdown (even with Flash running), I think it's pretty freaking cool that I can do all my freelance work with open software without skipping a beat. It makes you more productive if you can work on using open standards along with it.

The more XCFs, SVGs, and ODTs you send people, the higher the demand for proprietary applications to support them. Of course, I can open/save theirs, but it'd be nice to make open standards based file formats real standards.

---

### Post by ubunterooster on 2010-07-24
[B]The coolest thing I've ever done on Ubuntu is ```
apt-get moo
``` ;)
[/B]

---

### Post by Starks on 2010-07-24
> **phrostbyte said:**
> I would be careful though, definitely back up everything you have on the Windows side regularly. :)
I don't keep anything on that partition that I'd ever particularly care about.

---

### Post by user1397 on 2010-07-25
> **ubunterooster said:**
> Try running Ubuntu in windows in Ubuntu :D Just for kicks

i wonder whats the most that people have done with respect to putting an OS inside another OS in a virtual machine...

anyone know?

---

### Post by jerenept on 2010-07-25
> **ubunterooster said:**
> [B]The coolest thing I've ever done on Ubuntu is ```
apt-get moo
``` ;)
[/B]

NO,No...
```
aptitude moo
aptitude -v moo
aptitude-vv moo
aptitude-vvv moo
```

etc.

---

### Post by jerenept on 2010-07-25
> **ubuntuman001 said:**
> i wonder whats the most that people have done with respect to putting an OS inside another OS in a virtual machine...

anyone know?

That would be unbelievably slow, and probably awful.

---

### Post by mkendall on 2010-07-25
> **mkendall said:**
> But don't it seem that Kicks just keep getting harder to find? And all your kicks ain't bringin' you peace of mind?

> **ubunterooster said:**
> Yes, it does keep getting harder but I keep getting better so it is an endless cycle and I like it that way :D

Before you find out it's too late, girl, you better get straight.

No, you don't need Kicks.


(For those who haven't figured it out, I quoted the refrain to "Kicks" by Paul Revere and the Raiders.)

---

### Post by Doobie9 on 2010-07-25
When I first got pulseaudio working alongside x-forwarding so I could run sheepshaver (which I use to view files from my *old* Mac) with old Mac Os 9 on my netbook from my Core i7 desktop and show that to my parents. 

I thought to myself: *This* is what it's all about.

Next I'm going to run sheepshaver inside of an x-forwarded virtualbox; and inside of that I'm going to run an old Mac 68k emulator. Just for the hell of it. At this point I'm coming up with solutions in need of problems.

---

### Post by Starks on 2010-07-25
That's pretty cool. Kicks the **** out of me doing an SSH+X into the Linux lab on campus from my house.

---

### Post by cj.surrusco on 2010-07-25
> **linux18 said:**
> with my computer, I can transcode video in windows  in ubuntu in windows in ubuntu, of course im using a very lightweight / customized windows and ubuntu.

I guess you get bored every once in a while when you have an i7 with 6GB of ram.

---

### Post by linux18 on 2010-07-25
> **cj.surrusco said:**
> I guess you get bored every once in a while when you have an i7 with 6GB of ram.
I didn't think it was possible either until it happened, I really should get electricsheep and compile kernels more often to avoid boredom.

---

