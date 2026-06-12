---
title: "PC repair MONSTER ubuntu/virtualbox hard drive scanner project....."
date: 2009-04-07
forum: Virtualisation
---

### Post by parkland on 2009-04-07
I have a story here, and I hope to get some feedback. Positive or negative, any feedback is better than none.

Just a little background, the purpose of this project is to scan windows OS hard disks for viruses, and spy-ware.

We currently have a scanning computer, it has XP, and you can hook up a bunch of drives, and start all the scanning programs and they start at the first disk and keep on going till it's done.

I have been using ubuntu for a few years now, and came up with a concept of building a PC, and running a separate virtual machine for each disk so it can scan them all simultaneously. 

After building and testing the system, I am extremely impressed at the abilities such as being able to have a folder full of all our boot utility CD's, and being able to instantly use one on any disk.

So the PC itself, is intel 2.2ghz dual core, 8gb ram, and ubuntu with virtualbox on a 250gb hd.

I plan to have 8 miniXP virtual machines with the scanning tools installed.

I am constantly amazed during initial testing how much CPU resources there are to go around, even installing windows on 4 virtual machines at the same time the systems is still completely responsive, and this is all off the internal 250gb hard drive on virtual drives.

So heres the argument....


My senior technician (boss) tells me that VM's waste lots of CPU cycles...
That 1 computer having disk access to 1 drive at a time will outperform by far, my monster contraption scanning 4-8 drives at once...


I can see this, it makes sense, however, wouldnt the CPU far out perform the hard drive access with all the random read locations from all the scanners scanning at once, and if so, that would make the virtual machine scanners more efficient because the bottleneck would be the processing power?

Couldnt I argue that his scanner wastes 50-90% of cpu cycles waiting for disk access?

For example, lets say I get 4 virtual machine scanners running with the equivelent of 500mhz processing power each, that seems roughly the disk processing limit as far as I can tell.....beyond that CPU power, it seems that the system is waiting on random disk reads instead of matching resources. 


Am I on the right track on this one, or is there a better way?:guitar:):P

---

### Post by parkland on 2009-04-07
I forgot to mention, 

My primary goal is to scan hard drives for malware/viruses overnight on recieved computers, so when they get on the bench, I don't have to fool around for 20 minutes getting processes stopped enough to get networking going, installing all the tools on the customers PC, leaving it on the bench for hours scanning, and then uninstalling everything afterwards as well...

It would be nice to put all the computers on the bench with a pre-scanned hard disk... sure would keep things simpler and quicker...

---

### Post by juancarlospaco on 2009-04-07
1-They already exist.

2-No need to have Windows to scan for Virus, [ClamTK]("apt:/clamtk") and Kaspersky Scan *(Java)* run perfectly, for random examples *(there's more too)*

---

### Post by parkland on 2009-04-07
Cool!

One problem though,

we usually have to run up to 8 scanning products before we completely clean everything out, any idea on the most efficient way to scan for viruses and spyware without needing to run so many scans?

Thats my reason for running windows on virtualmachines, cause the majority of scanners are for windows....

We cant find any scanners that will find everything....one finds some, then another finds some more... etc, till we cant find anything anymore....

I'd love if you could share any links or names I could search, I have dont as much searching and reading as I have time for....

---

### Post by parkland on 2009-04-09
Alright, well,....

I'm writing this right now on a completely responsive interface as I have 5 microXP virtual machines scanning 5 windows hard disk drives. 

Leaving the math and science behind, it seems to be working.

As soon as you run anything in ubuntu, the CPU resources seem to hit 100%, but obviously nothing to take to heart, as even at 100$ CPU usage, everything is running awesome!

I can honestly say that running virtual machines to scan hard drives a completely feasible idea, it takes a while to set up, but now I'm saving real time, time that will easily make up for my setup investment.

I can't say I'm surprised, an identical computer to this one was scanning a hard disk earlier with 6 scanning programs, and I checked it and it was only using 5-12% CPU usage for the entire PC, so it seems that the hard drive scanning is mostly seek time, not CPU time.........

.....

---

### Post by juancarlospaco on 2009-04-10
Try **ReactOS** on the VMs, if work, would be better, more lightweight and OpenSource.

---

### Post by parkland on 2009-04-11
More lightweight than microXP ?

I have considered quite a few options now, but I like using microXP cause its small, fast, and I dont have any error messages or elaborate setup to make it work...

---

