---
title: "Your Ideal Partition Set Up?"
date: 2007-04-08
forum: The Cafe
---

### Post by steevk on 2007-04-08
Hey guys-

A while ago I got two 160 GB SATA drives, and set out to partition them in the best way that I thought at the time...

So here's the deal, it's not working out that well. I basically have everything on one drive, and nothing on the second.

Here's where I want to get:

[LIST]
[*](K)Ubuntu (I plan on having both ubuntu-desktop and kubuntu-desktop installed
[*]Gentoo, eventually...I'd like for my Linux knowledge to not just be Debian centric.
[*]A small Windows partition for games that don't run well under WINE.
[/LIST]

Other details:

[list][*]I'd like to be able to share data between the Ubuntu and Gentoo partitions...I guess just the same $HOME.
[*]The Windows partition doesn't need access to anything that's on Linux. I want a sleek, minimal install so I can play my game or two, and then get out. I do all real work in Linux.
[*]I have a lot of data that I'd like to back up, and not nuke if possible. It took me a while to re-rip my CD collection and fill in the gaps from various other sources, and I have it all set up how I'd like it, and so I don't want to mess with that, if at all possible...
[*]I like to update my OS fairly frequently. For instance, I'd like to do a fresh install of Feisty from the CD when it is released, rather than just dist-upgrade. Or maybe upgrade to Vista someday when it turns out that Warhammer Online works best with it, or decide that Gentoo is lame and install Slackware, or maybe that Roll Your Own business... point is, I need to keep the OS and the data separate.
[*]As I get a little bit older, I'm starting to realize that I'd like to start backing up stuff. I'm starting to use the computer for things that aren't just games or screwing around, and would like to save them for later. There's stuff that I'm starting to do that I'd be sad if I lost, so I need to come up with some kind of backup scheme. Maybe a separate parition for that? Buy a reel of DVDs? I'm not sure where to go with this, either...[/list]

So that's my deal. So I figure the plan of attack is to partition and create a new directory for $HOME on drive #2, copy my current home over, and then nuke drive #1 and set it up with three partitions for the three OS-es.

Does that sound right? How should I set them all up? All ext3 for linux, ntfs for windows? How should I go about creating the partitions on the second drive?


I have all day to mess around with this, I'm not going anywhere or doing anything...I'm just looking for some guidance from those who have contemplated something like this before. Any help is appreciated.

---

### Post by rai4shu2 on 2007-04-08
Don't forget the swap partition.

---

### Post by Nils Olav on 2007-04-08
how much free space do you have?

---

### Post by steevk on 2007-04-08
I have a whole second 160GB disk free.

Here's how I have my files set up on the first one:
```
steev@steev-desktop:~$ df -hl
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              20G  5.5G   14G  30% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M   92K  506M   1% /proc/bus/usb
udev                  506M   92K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   28M  478M   6% /lib/modules/2.6.20-14-386/volatile
/dev/sda4             107G   81G   21G  81% /home
/dev/sda3              20G  129M   19G   1% /other

```

---

### Post by maniacmusician on 2007-04-08
didn't have time to read your whole post, but I did catch a bit of it. It's not a good idea to share the /home dir's between distros. I'm pretty sure some things are handled differently between distros and it would not be a good idea to overlap settings; or so I'm told. You already have 21GB for your /home partition right now. So I would take the second drive, leave 60 GB at the beginning of that drive (install OS's onto there; 20GB per OS. this works very well with Linux-based distros), partition the last 100GB as an ext3 partition and use it for storage.

---

### Post by Nils Olav on 2007-04-08
> **maniacmusician said:**
> didn't have time to read your whole post, but I did catch a bit of it. It's not a good idea to share the /home dir's between distros.

That's not something to worry about. Anyway do you want me to give detailed help or is there just a few things you need help on? You seem to know what you are doing.

---

### Post by steevk on 2007-04-08
For the most part, I know what I'm doing. However, I'm not sure how big to make the partitions, and if there were any huge problems with my logic about how to go about doing this.

---

### Post by Nils Olav on 2007-04-08
> **steevk said:**
> For the most part, I know what I'm doing. However, I'm not sure how big to make the partitions, and if there were any huge problems with my logic about how to go about doing this.

Sense you want to back stuff I suggest some thing like this:
1st drive:
20   Gb ext3 (for ubuntu)
20   Gb ext3 (for your other linux)
120 Gb ext3 (for home)

2nd drive:
120 Gb ext3 (for home's backup)
40 Gb NTFS (for windows)

---

### Post by maniacmusician on 2007-04-08
as a previous poster mentioned, you should probably throw a swap partition in there.

---

### Post by steevk on 2007-04-08
I have a gig of RAM, so that's a good size for swap, no?

This leaves me with this rough setup:

/dev/sda1 20 GB, ubuntu
/dev/sda2 20 GB, other linux
/dev/sda3 1GB, swap
/dev/sda4 119 GB, /home

/dev/sdb1 120GB, /home backup
/dev/sdb2 40 GB, Windows

Sounds good to me. I mean, I'm sure I could compress my home backup somehow, but I guess I'll see how using the uncompressed backup goes right now, and do that in the future if I need to.

Thanks for all the help everyone, I'm going to get on that plan now...

---

### Post by Nils Olav on 2007-04-08
> **maniacmusician said:**
> as a previous poster mentioned, you should probably throw a swap partition in there.

opps

---

### Post by prizrak on 2007-04-08
It really depends. The way I used to have it set up was 64MB /boot 4GB / and the rest would be /home with a 1 gig swap. However, the last big Feisty update needed more room on /boot so I have merged /boot with / and kept the rest the same. You basically need to find your usage style. I don't tend to go much beyond the stock Ubuntu setup with software so 4 gig is plenty. If you like to install alot of stuff that will go into / then you might need more space. In general only two things matter, have your /home a separate partition and have a swap partition.

---

