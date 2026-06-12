---
title: "Ubuntu Partioning tool"
date: 2006-01-12
forum: The Cafe
---

### Post by tonyisntcreative on 2006-01-12
I was wondering if there was any way to use the tool that I used in the installation without having to use the install disk.  I've put in the install disk once before and went to the partioner just to use that once, but I still have to wait for it to detect a bunch of hardware before it even gets to the partitioner.

I've always used a Windows ME "emergency" floppy to partion with fdisk.  After using the Ubuntu tool, though, I've found that I like it better and I wouldn't mind using it in the future over fdisk.  The one on my Ubuntu CD allows me to resize and format with all kinds of different file systems...fdisk only lets me create and delete, meaning I'd lose everything every time I want to change something.

I know there are a whole bunch of programs you can use to partition with...but I was wondering if there was any way I could get the Ubuntu partitioner to a floppy or CD or something so that I could put it in my computer and boot right to that when I want to change something.

---

### Post by aysiu on 2006-01-13
I don't know, but if you want a live CD that you can boot to and use partitioning with, PCLinuxOS (DiskDrake) and Knoppix (QTParted) would be good choices.

---

### Post by gord on 2006-01-13
or if you have an ubuntu live cd laying around (breezy), it has gparted on it, and would take a guess that kubuntu has qparted on that too.

---

### Post by aysiu on 2006-01-13
[QUOTE=gord]or if you have an ubuntu live cd laying around (breezy), it has gparted on it, and would take a guess that kubuntu has qparted on that too.[/QUOTE] I may be remembering it wrong, but I don't believe either has the programs you mention. I seem to remember having to ```
sudo apt-get install gparted
``` when using the live CD to partition.

---

### Post by hillbilly on 2006-01-13
Yeah, qtparted is not available on ubuntu, I am not sure about gparted though !!

---

### Post by curuxz on 2006-01-13
I found gtparted in the repos (not sure which ones since I have so many sorry). But when it comes to live partitioning I keep a copy of knoppix running around since it contains loads of tools for system recovery/preping for new install. :)

Would always recomend having a copy of knoppix since its the swissarmy knife of distros :)

---

