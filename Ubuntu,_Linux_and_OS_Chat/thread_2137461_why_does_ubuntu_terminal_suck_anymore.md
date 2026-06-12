---
title: "why does ubuntu terminal suck anymore?"
date: 2013-04-20
forum: Ubuntu, Linux and OS Chat
---

### Post by letitworknow on 2013-04-20
ubuntu used to be the best linux distro out. now im a bit disapointed.  it started when i bought a thinkpad. i wanted to dual boot with the windows 7 that it came with. the install curropted my windows partition. now i can't boot to windows. i would just reinstall windows using fdisk however fdisk is pretty much usesless anymore. no more -d?  no more gparted? how do you do any admin work on ubuntu anymore?  i can't even start my wifi from the command line anymore?  iwconfig does nothing even though i can see the card with ifconfig and i can see the ap i am trying to connect to with iwlist.  i can connect when i use the gui.  this is so dissapointing. who has the best distro out now? mint? fedora?

---

### Post by CharlesA on 2013-04-20
Hmm, I used gparted from a Ubuntu livecd the other day and it ran fine for me. I've always used gparted or parted to create partitions, not fdisk, though.

---

### Post by letitworknow on 2013-04-20
it needs to be downloaded with apt-get now.  it seems ubuntu didn't hesitate to through in some bloatwear like ubuntuone  but they didn't feel the need to add the admin programs

---

### Post by matt_symes on 2013-04-20
Hi

Tools change over time.

check out *nm-tool*, *nmcli* and other related tools. The tools to do the job are still there.

Ubuntu no longer uses hal and many other tool and technologies.

Many of the old tools are still there though. 

Can i recommend you always make a backup before changing any system.

There always the forums for support as well.

Kind regards

---

### Post by deadflowr on 2013-04-20
> **letitworknow said:**
> it needs to be downloaded with apt-get now.  it seems ubuntu didn't hesitate to through in some bloatwear like ubuntuone  but they didn't feel the need to add the admin programs

And yet I, as well as a whole lot of users, feel the opposite.
I would consider having partitioning programs installed by default just as bloating.;)
If a gui can do what a cli can do, why have a cli included. Rather redundant.
Ubuntu isn't designed for just admins, it's designed for all people.

---

### Post by monkeybrain2012 on 2013-04-20
gparted is always in the live iso, but as far as I can remember I always have to apt-get install it myself in a regular install since 10.04.

---

### Post by cariboo on 2013-04-20
@letitworknow , I quess you didn't get the email about how much Ubuntu has changed over the last 6 releases. :-D

---

### Post by CharlesA on 2013-04-20
> **monkeybrain2012 said:**
> gparted is always in the live iso, but as far as I can remember I always have to apt-get install it myself in a regular install since 10.04.

Hrm. I think you are right about that. At least it's on the livecd. :)

---

### Post by Irihapeti on 2013-04-20
It's still possible to connect to wifi from the command line. I've done it from 12.04 and, just the other day, from 13.04. I can't say it's the easiest thing to configure, but it does work.

---

### Post by Gone fishing on 2013-04-20
Gparted has never been included on the default install (I've been using Ubuntu since Hoary). It has always been on the CD (well since there has been a live CD). But gparted isn't a terminal tool anyway parted is. The terminal is as powerful as it has ever been, you might need to install more command line programs such as sudo apt-get install iftop but not everyone needs these tools. Nevertheless all the command-line goodness of Linux is just an alt control F2 away.

---

### Post by iamkuriouspurpleoranj on 2013-04-21
Linux Mint also has GParted in the live environment but not the installation.

No reason to have a partition program by default post-installation.

---

### Post by Rukiri on 2013-04-21
I use gdisk for partitioning my disk, tools change and gdisk is the way to go.

---

### Post by kevdog on 2013-04-21
Gparted on a live CD is the way to go -- anything else is superfluous.

---

### Post by monkeybrain2012 on 2013-04-21
> **kevdog said:**
> Gparted on a live CD is the way to go -- anything else is superfluous.

Not true. I use gparted from my regular install to partition external hard drives.

---

### Post by ibjsb4 on 2013-04-21
The recommended way of using GParted is from the live environment to avoid data corruption.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId661277](http://www.dedoimedo.com/computers/gparted.html#mozTocId661277)

But like others, I do not always use the recommended way when working on partitions.

---

