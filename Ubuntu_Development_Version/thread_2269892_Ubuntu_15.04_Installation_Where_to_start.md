---
title: "Ubuntu 15.04 Installation: Where to start?"
date: 2015-03-18
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2015-03-18
Don't know where to start to install 15.04?  Running 14.04.2 LTS and it works so fine that I'm seeking for a new challenge.  So, someone wana show me where to start? Wana do a fresh installation, meaning that I'm gonna erase 14.04.2 LTS.  X86? / AMD 64?

This is my machine: intel® Core™ i3-2100 CPU @ 3.10GHz × 4 / 64 bit / HP all-in-one

---

### Post by QIII on 2015-03-18
Moved to Ubuntu Development Version.

---

### Post by cariboo on 2015-03-18
> **MikeMecanic said:**
> Don't know where to start to install 15.04?  Running 14.04.2 LTS and it works so fine that I'm seeking for a new challenge.  So, someone wana show me where to start? Wana do a fresh installation, meaning that I'm gonna erase 14.04.2 LTS.  X86? / AMD 64?

This is my machine: intel® Core™ i3-2100 CPU @ 3.10GHz × 4 / 64 bit / HP all-in-one

If you want to keep 14.04, you could use gparted to create some empty space on your hard drive, and then install Vivid on that. I'd suggest using AMD64 as you've got a 64-bit cpu.

---

### Post by grahammechanical on 2015-03-18
I have learnt that when running the development release it is best to have one stable release of Ubuntu to use as a fall back OS if the development release gets broken. So, I dual boot with 14.04. Well, it is a bit more than that as I have development installations of the flavours of Ubuntu as well.

This is the place to get the latest daily build of Ubuntu

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Another place to go is here

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

Just click on vivid daily to see links to the downloads for the development version of all the Ubuntu family of distributions. If we are serious about testing the development release we can go here

[https://wiki.ubuntu.com/QATeam](https://wiki.ubuntu.com/QATeam)

Welcome to getting involved in using the development version

Regards.

---

### Post by MikeMecanic on 2015-03-18
Many problems in the pass with dual boot and *gparted* doesn't look friendly user.  Also, if like you say *the development release gets broken *it takes 20 minutes to reinstall 14.04. In the pass, I was testing Windows Beta version alone. Feel like have it alone. 

Download of VIVID-DESKTOP-AMD64.ISO (1.1Gig) **Failed!  Have to restart.**
Was it you that told me ounce that a fresh installation provides more stability...

---

### Post by MikeMecanic on 2015-03-18
To: Blöder Esel 					
This is the information I'm getting in the terminal and I'm not able to do nothing on the AMD web site:**~$ lspci -vvnn | grep VGA**

Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09) (prog-if 00 [VGA controller])

---

### Post by MikeMecanic on 2015-03-18
Download failed for a second time in Firefox.  Trying on Opera...

---

### Post by MikeMecanic on 2015-03-19
**Full installation: erase 14.04.2 LTS**
**Choose the LVM Option with erase disk and install Ubuntu**

**1st attemp**t: freeze on Creating ext2 file for/boot in partition /of SCSI (0,0,0) (sda)...Never seen copying files process. Turn OFF the power

**2nd attempt**: Black screen / Turn off power and unplug Internet

**3rd attempt**: freeze on Creating ext4 file for...Here I didn't choose the LVM Option. Turn OFF the Power.

**4th attempt**: My computer is empty and I choose to reinstall 14.04.1 LTS with my ISO DVD.  Internet unplug without upgrading.  At the end of the process i<m ask after rebooting to eject the DVD.

**5th attempt**: Internet Unplug / LVM option is check.  After New-York, I finally see the copying files process, meaning that the installation occurs.  At the end, the process should ask me to eject the DVD but it's not. **A second installation restarts**.  I stop it. ** I'm now running 15.04**.  :wink:

---

### Post by rrnbtter on 2015-03-19
Greetings,

> **MikeMecanic said:**
> 
Was it you that told me ounce that a fresh installation provides more stability...

I not the one that told you that but I do agree with it. A clean install eliminates all of the user tweaks and other user errors and allows the user to get a feel for the default install. 

That being said, your OP asks where to start with 15.04. The problem is that your are actually downloading and trying to install Ubuntu Vivid **15.02** which is a prerelease version. I agree with the post that suggest downloading the daily instead of the beta or alpha but either way you are testing, pure and simple. This is a testing section and I would suggest not installing the Ubuntu 15.02 disk unless you have the guts for it. I have been using these development versions continuously since Karmic Koala and I now consider myself to be an expert re-installer (at least on my own systems). Utopic as an alternative is a pretty good finished system and it will get some of the already established Vivid features once installed. Seem like a better choice than Vivid at the moment (if you don't want to test).

---

### Post by syntaxerror74 on 2015-03-19
> **MikeMecanic said:**
> To: Blöder Esel
HAHA...funny...this is German for "*Stupid donkey*"

But you actually looked at the wrong line...his username is **QIII**, just pointing out ;)

---

### Post by MikeMecanic on 2015-03-19
I'm note sure what you mean but I burn an ISO DVD of the following version:
Ubuntu Version Install: hp@hp-610-1130f:~$ **lsb_release -a**
**Result in march 2015: Description:	Ubuntu Vivid Vervet (development branch)**
**Release:	15.04**
**Codename:vivid**

---

### Post by rrnbtter on 2015-03-20
Greetings,
If you are not sure what you are running check this out [https://launchpad.net/ubuntu/vivid](https://launchpad.net/ubuntu/vivid). All of us that are running Vivid will be on 15.02 until March 31 when it becomes 14.03.  The final release will be 15.04. It could take 30 days following the final release for things to get really stable due to catch-up by a few software developers. We are however testing the development of Vivid 15.04 which is what is reported by the LSB.

---

