---
title: "Raid 1: software or motherboard/BIOS"
date: 2009-01-02
forum: The Cafe
---

### Post by jbrown96 on 2009-01-02
I'm building a new computer for my family while I'm in town, and I have a question about RAID. The motherboard supports a few RAID modes, and I know that Linux does as well. My question is for Raid 1 (2x 640GB drives), which should I use? 
Here's my planned partition scheme:
1) ~20GB for /
2) the rest for /home
3) no swap (8GB ram and no hibernate/suspend)

I would rather use the software method because I tend to trust Linux more than a budget motherboard, but I have some concerns. If I want to reinstall Ubuntu, or even another distro, will I be able to keep the /home partition unaffected? I've done some reading on ZFS, and one of the features that I really like is that it doesn't have to copy the entire drive to rebuild the array, just parts that are actually in use. Does Linux Raid do this? Does anyone else have other experiences with Raid that might be relevant, especially Linux Raid?

---

### Post by andamaru on 2009-01-02
When using software raid, there is a small overhead, and when using hardware raid there is no overhead (on the CPU). I would use the hardware option, I don't a cheap motherboard would ship with faulty raid.

---

### Post by cmat on 2009-01-02
Always go for hardware. Software RAID isn't that great. I have a few cases where the entire array was taken out by faulty RAID.

---

### Post by toupeiro on 2009-01-02
I've always, always, always used hardware RAID wherever possible for the obvious benefits it provides which have been mentioned in this thread.  However, with the advent of multiple core technologies and the mega amounts of RAM you can now configure in a single machine, there have been some tests recently where SoftRAID has been re-evaluated, and in some cases has surpassed hardware RAID in array rebuild times.  Yes, there is an accompanying CPU overhead, so it will be based on your needs whether these faster SoftRAID rebuild times for larger disk/LUN configurations are worth that overhead..  

The fact is, if you fail a disk in a RAID array, hardware or software, you **will see** a performance degradation on use because you have less spindles, and on rebuild because you are rebuilding a disk from mirror or parity.  With hardware, its just not on your CPU's, but solely on your array controller.  Disk controllers typically do not have the cycles and RAM that your system does, so while its isolated, its not always fast.  Either way, the end result is the same, reduced performance.  Unless you have the need for all of your CPU cycles all the time, you will likely not even notice the CPU overhead of your SoftRAID array.  What you will notice, according to these tests, is that your array rebuilds will complete faster, which when you think about the typical reasons to use RAID on a standard computer or server, fault tolerance and uptime are usually bigger drivers than CPU cycles for your redundancy.  For general home use, I don't think either one is going to matter in the long run.  Hardware RAID is a piece of cake to setup.  SoftRAID is not hard, but different.  There was a pretty good writeup on how to configure SoftRAID in either Linux Journal or LinuxPC's December magazine issue.  Google should also give you an abundance of resources.  You might consider SoftRAID for educational purposes, but if you dont care about that, stick with hardware.

I don't know if I am sold on that concept so far as to ditch hardware RAID if I have it available to me, because hardware RAID is still typically more maintenance-free, but I will be doing more research on SoftRAID based on what I've been reading lately.  I still use pretty beefy array controllers for my RAID arrays in servers, which are pretty quick.

---

### Post by jbrown96 on 2009-01-02
Thanks for the replies. 
I'm building this specifically to work for a long time. It's for my parents, who don't need lots of performance, and I'm getting a Phenom quad-core and 8GB of 1066 ram, so I don't think the overhead is an issue. 


Cmat: Could you give some more info about losing the arrays?

The only other question that I have is about reinstalling a distro. Is it straightforward to re-use existing partitions (without losing data) with software raid? 

As far as the hardware Raid goes, I won't be buying a dedicated card, but the motherboard does support it. If the board goes bad, and I know this depends on the manufacturer, am I likely to be able to recover the array with a new board?

---

### Post by toupeiro on 2009-01-02
> **jbrown96 said:**
> Thanks for the replies. 
I'm building this specifically to work for a long time. It's for my parents, who don't need lots of performance, and I'm getting a Phenom quad-core and 8GB of 1066 ram, so I don't think the overhead is an issue. 


Cmat: Could you give some more info about losing the arrays?

The only other question that I have is about reinstalling a distro. Is it straightforward to re-use existing partitions (without losing data) with software raid? 

As far as the hardware Raid goes, I won't be buying a dedicated card, but the motherboard does support it. If the board goes bad, and I know this depends on the manufacturer, am I likely to be able to recover the array with a new board?

make sure your new board has the same controller chipset as your old one, and you should be OK.  Periodically, check for firmware updates for your controller so  you can be close to the same hardware revision if and when you do change the board.  Doing so will eliminate the majority of conflict in attempting a board replacement.  Your OS may complain about some of the other components in the new board, but your array may be OK.  also, keep track of your disk order.

---

