---
title: "Setting Up a RAID Array"
date: 2009-02-07
forum: Server Platforms
---

### Post by MOGuy78 on 2009-02-07
I plan on setting up a simple file server for my home
network, and I chose to use Ubuntu Server because of
past experience that I've had with Ubuntu plus all of
the great help that I've recieved from so many other
users in these forums.

My main purpose is to have one place to store all of my
music, software, videos, and other misc. data files.
I will mainly be accessing these files from my Windows
computers, and most likely be using Putty to work with
the linux system through remote access, so I plan on
installing the Samba File server and the OpenSSH Server.

My server computer has:
- (1) 10 gig HD for the OS, and
- (2) 750 gig HD's connected to a RAID controller that I'm
  wanting to set up in a RAID1 Array for Storage.

My question is:
When I'm partitioning my HD's during the linux installation
using the "Guided - use entire disk" option, I'll view the
layout of the partitioned drives and it shows all three drives
listed.  Should it not just show 2 drives (the 10 gig HD and
the 750 gig RAID Array)?  If it is supposed to show all 3, how
do I set it up where the 2 drives in the RAID array will mirror
each other?

Any help would be appreciated.

---

### Post by fjgaude on 2009-02-07
Many ways to go, but if you are thinking of using the BIOS raid on your motherboard, that's another matter. Here's some links that will get you going:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://users.telenet.be/mydotcom/how...skfakeraid.htm](http://users.telenet.be/mydotcom/how...skfakeraid.htm)
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)
[http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing](http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing)

Let us know how you are doing.

---

### Post by MOGuy78 on 2009-02-07
How can I tell if it is a Fakeraid?
I'm using a Promise Tech. FastTrak100 TX2 RAID Controller.

---

### Post by fjgaude on 2009-02-07
> **MOGuy78 said:**
> How can I tell if it is a Fakeraid?
I'm using a Promise Tech. FastTrak100 TX2 RAID Controller.

Well, if the controller costs less than $300 retail, then it uses the computer's CPU, memory through a bus on the card, either PCI, PCI-X, or PCI-E. Which is it?

Next, if no driver you can somehow set an array up and use **dmraid** to recognize it from Linux.

Do you have a driver disk that loads into Linux for the card? If not, then you will likely have to use the card as a simple controller and use Linux's **mdadm** to create the raid array.


Lot of learning required to do raid in Linux; not so in Windows. <smile>

---

### Post by MOGuy78 on 2009-02-07
I'm still trying to figure out if I have a real hardware RAID
controller or a cheaper one that uses the computer's CPU and
memory.
When I start the computer up, right after the memory check a
screen comes up that shows:

FastTrak TX2 Bios 2.00.0.33
Scanning IDE Drives . . .
ID: 1              RAID Mode: 1x2 Mirror
Size: 500000M      Status: Functional

Press <CTRL-F> to enter FastBuild Utility . . .


It then boots into whatever OS is installed.

Is it saying that the controller itself has its own BIOS?
Does this happen with both true hardware RAID controllers AND
the cheaper ones, or with only one of them?

---

### Post by fjgaude on 2009-02-08
Did you setup the raid array using the FastBuild utility?

When you bootup, do you go through a grub menu that gives you options, like to Ubuntu and Windows?

With what you have given us I can't tell for sure but it would seem you have a real raid controller... the next question is are you able to mount the raid1 array?

If not then you don't have a driver disk to load into Ubuntu so it can see the array as an array.

Or else it is fakeRAID and you can use **dmraid** to mount and use the volume.

---

### Post by mn_voyageur on 2009-02-08
[http://forum.soft32.com/linux2/Promise-Fast-trak-100-TX2-Raid-card-ftopict24688.html](http://forum.soft32.com/linux2/Promise-Fast-trak-100-TX2-Raid-card-ftopict24688.html)

A post indicates it is fakeRAID.  

I am currently trying to decide if I should invest in a NAS or add a RAID array to an existing machine.

Should I post separately? 

MN

---

### Post by fjgaude on 2009-02-08
> **mn_voyageur said:**
> [http://forum.soft32.com/linux2/Promise-Fast-trak-100-TX2-Raid-card-ftopict24688.html](http://forum.soft32.com/linux2/Promise-Fast-trak-100-TX2-Raid-card-ftopict24688.html)

A post indicates it is fakeRAID.  

I am currently trying to decide if I should invest in a NAS or add a RAID array to an existing machine.

Should I post separately? 

MN

Likely you would get more attention if you post separately. Just my opinion.

---

### Post by MOGuy78 on 2009-02-08
After searching through the support section from the Promise
web site, I still wasn't able to find the correct driver for
my card to use with either the Ubuntu or Debian OS (isn't
that what Ubuntu is based off of?)

After reading about using Raid cards, I was wondering if it
wouldn't be better to use a software raid anyway?  Some of the
FAQs that I've read say that if your specific hardware raid card
messes up, you would no longer be able to have access to any of
your files that you've stored on the HD's connected to it.  But
software raid doesn't require you to use any specific hardware
such as that.  Is this correct?

---

### Post by fjgaude on 2009-02-09
Well, you are going through all the ifs, ands, and buts of hardware versus software raid. So much to learn... all of it depends on so many things, like what are you doing with raid, why, where, etc.?

If your motherboard has enough ports to handle the number of drives you wish to use in your array then software using **mdadm** is a good choice. It's what I do, and data is everything to me. I cannot lose it, period, no matter what. But there is alot to learn to cover yourself with mdadm as things go wrong down the way, when things break, etc.

If you have read, studied all the links given you, you can be your own judge as how to proceed.

Let us know what you choose to do.

---

### Post by Pumpino on 2009-02-10
If you decide to go with software RAID, consider installing Ubuntu using the alternate ISO rather than the desktop ISO (if you want a GUI). The reason being that the desktop ISO partitioning section does not allow you to set up RAID during the installation process. If you use the alternate CD (based on Debian's text installation), you're able to set up software RAID easily and avoid manually setting up RAID after the installation has completed.

---

### Post by handy on 2009-02-10
I'm using [*_FreeNAS_*]("http://www.freenas.org/"), which sounds like it would suit you down to the ground.  It comes with a very large range of communication services, & RAID.  It is tiny, less than 70Mb, can be set up as a torrent slave, has an incredibly polished GUI accessed via a clients web browser.

It sets up really easily, can be set up on CF or USB Flash; can run entirely in RAM.

I've been using it for maybe 2 months & have found it to be faultless. 

There are forums & such on sourceforge for it.

---

