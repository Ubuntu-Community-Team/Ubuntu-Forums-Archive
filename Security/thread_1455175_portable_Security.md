---
title: "portable Security"
date: 2010-04-15
forum: Security
---

### Post by Xeneth on 2010-04-15
For my windows box, I use portable apps on my USB for encryption and tools so I have an uncontaminated scanner that I can keep with me.  I want to setup a similar for Linux, but I cannot find any pre-setup portable tools.

I am looking for anti-virus, packet sniffer, encryption, and a few other tidbits for portability.

Thanx

---

### Post by bodhi.zazen on 2010-04-15
> **Xeneth said:**
> For my windows box, I use portable apps on my USB for encryption and tools so I have an uncontaminated scanner that I can keep with me.  I want to setup a similar for Linux, but I cannot find any pre-setup portable tools.

I am looking for anti-virus, packet sniffer, encryption, and a few other tidbits for portability.

Thanx

Install Linux into the USB, use the alternate CD to encrypt your installation.

Then install whatever tools you wish.

---

### Post by Sir Jasper on 2010-04-15
Hi,

If you adopt bodhi&#347; suggestion you will have the advantage of a complete Linux Operating System on your USB device. Alternatively, I use Wine v 1.0.1 with many Portable Windows applications installed in my Home directory (as well as on a USB stick).

[http://portableapps.com/apps](http://portableapps.com/apps) has a good selections of applications which work with both Windows and Linux + Wine and there are plenty of other good sources as well.

My regards 

PS I have found that Portable Windows programs tend to work especially well with Wine, but you could always try those you already have and possibly get the best from both worlds.

I normally use Xubuntu 9.10, but I have tried Puppy Linux 4.3.1 which may be the fastest OS for a USB device and it is likely to be worth a trial run.

---

### Post by Xeneth on 2010-04-15
Can you give a little more detail on the setup you mean with the linux running off of the USB?  I'm a novice, so I may be missing something.  If I run linux off of my USB, I would assume that would require not only having a boot sector on my pin drive, but a gamble on rather or not the PC is setup for booting from USB.

I did this with a boot-able CD the first time I messed with Linux, using DSL, but I was hoping for something I can run without having to restart the computer and loading a different OS.

---

### Post by bodhi.zazen on 2010-04-15
> **Xeneth said:**
> Can you give a little more detail on the setup you mean with the linux running off of the USB?  I'm a novice, so I may be missing something.  If I run linux off of my USB, I would assume that would require not only having a boot sector on my pin drive, but a gamble on rather or not the PC is setup for booting from USB.

I did this with a boot-able CD the first time I messed with Linux, using DSL, but I was hoping for something I can run without having to restart the computer and loading a different OS.

If you would like a set of applications that run on Linux and Windows, take a look at the portable apps Sir Jasper gave you.

If you want to run Linux insode windows (without rebooting) you can look at Portable Virtualbox or qemu

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

If you want to make a USB drive installation as I suggested, you would install to the udb drive just as you would to the hard drive. You need to take care where you install grub (install grub on the usb drive and not the hard drive).

See also

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

### Post by node8472 on 2010-04-16
truecrypt can be run portably

---

### Post by Xeneth on 2010-04-16
Portableapps.com is what I use with some of my own thrown in.  Using it with WINE seems to be close to what I was originally thinking and will test it out to see if that will work.  

Because I'm new to Linux, I am having trouble wrapping my head around running a windows program that examines file structurs or opperations.  An anti-virus or registry cleaner made for windows I cannot see working.  Have to play with it.

---

### Post by bodhi.zazen on 2010-04-16
> **Xeneth said:**
> Because I'm new to Linux, I am having trouble wrapping my head around running a windows program that examines file structurs or opperations.  An anti-virus or registry cleaner made for windows I cannot see working.  Have to play with it.

You do not need either of those (antivirus or registry cleaner) in Linux.

---

### Post by Xeneth on 2010-04-16
That I find hard to believe.  Even if it is far more secure, and people are less likely to attack it due to it being "not windows", there are still unix viruses and others that can still affect linux.

---

### Post by Sir Jasper on 2010-04-16
Hi,

bodhi has a wealth of expertise, but you and I are relative novices. I do not suggest we automatically believe anything said by a person of importance, but especially for now, do not worry about what you find hard to believe.

It might help us a little to know why you need the USB programs e.g. are you helping friends or family with safety and security?

Do let us know how you get on.

My regards

---

### Post by HermanAB on 2010-04-16
Is it a default Ubuntu system?  If so, just relax and enjoy your nice, secure system.  There is no need to add other security schtuff to it.

---

### Post by Xeneth on 2010-04-16
"need" is probably not the best choice of words because I really do not need it.  It's more or less me wanting a toy to play with.  To learn how LINUX works and all.  The mobility I want because I want to use the same software for multiple computers.  (which It's 100% preference because my laptop is the only one with Linux.

I just like the Idea of keeping tools with me so that if I need them, I don't have to search and download, assuming that I can get on the internet.  It's purely desire for preparation.

---

### Post by Wiebelhaus on 2010-04-16
> **bodhi.zazen said:**
> Install Linux into the USB, use the alternate CD to encrypt your installation.

Then install whatever tools you wish.

+1 For internal usage on my tech bench , I have several remastered live cd's containing a plethora of tools including bit defender , fprot , clamav etc. You could do the same thing with a usb stick although it doesn't work in the same fashion as "portable" apps that your using now , it works more like a live file system. I suggest using [puppy ]("http://www.puppylinux.com/flash-puppy.htm")for your first experiments.

---

### Post by bodhi.zazen on 2010-04-16
> **Xeneth said:**
> "need" is probably not the best choice of words because I really do not need it.  It's more or less me wanting a toy to play with.  To learn how LINUX works and all.  The mobility I want because I want to use the same software for multiple computers.  (which It's 100% preference because my laptop is the only one with Linux.

I just like the Idea of keeping tools with me so that if I need them, I don't have to search and download, assuming that I can get on the internet.  It's purely desire for preparation.

I highly suggest you start by reading the stickies at the top of these forums.

---

### Post by Xeneth on 2010-04-16
My original post was mainly portability, which I did get a few good Idea's.  I think the discussion got a little off topic, but I do need to read the stickies.

---

### Post by Jive Turkey on 2010-04-18
I agree with others who have said installing ubuntu to the usbkey and using the portable apps in wine off of that key while booted from that key will work great.

An operating system (including windows, linux, or any other) with rootkits installed, by definition, can only be examined reliably from a different operating system.

---

