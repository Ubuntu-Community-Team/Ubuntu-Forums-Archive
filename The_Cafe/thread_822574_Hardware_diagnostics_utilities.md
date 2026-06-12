---
title: "Hardware diagnostics utilities?"
date: 2008-06-08
forum: The Cafe
---

### Post by mips on 2008-06-08
Anyone know of good hardware diagnostics utilities that basically tests MB components, CPU & RAM? Ones that run from DOS or a self contained boot cd would be great as I cannot even get the kernel started.

My PC is on the blink and I need to find out what is wrong.

---

### Post by PmDematagoda on 2008-06-08
I do not know of any such software, but what exactly is up with your PC?

---

### Post by mips on 2008-06-08
> **PmDematagoda said:**
> I do not know of any such software, but what exactly is up with your PC?

I get various different errors (I have not recorded any of the errors). Sometimes the kernel won't even load, other times it loads but then less than a minute into my desktop the pc crashes & reboots. Somtimes it hangs during the boot process. The same happens with liveCDs so it is not my OS. Everything so far points to a hardware problem of sorts.

I do not have access to spare components so I could swap things out and find the fault via a process of elimination unfortunately.

---

### Post by jrusso2 on 2008-06-08
Most of the hard drive companies offer a diagnostic and it sounds like the hard drive.

Are you getting any beep codes?

---

### Post by nick_h on 2008-06-08
There is always memtest86+ on the Ubuntu CD to test the memory.

Hard drive manufacturers supply their own diagnostics utilities as jrusso2 has already mentioned.

You could try the [Ultimate Boot CD](http://www.ultimatebootcd.com/) which contains a lot of diagnostic utilities.

---

### Post by mips on 2008-06-09
> **jrusso2 said:**
> Most of the hard drive companies offer a diagnostic and it sounds like the hard drive.

Are you getting any beep codes?

Trust me, it is not the hard drive. The HD is a brand spanking new Seagate. This happens with LiveCDs as well which eliminates the HD.

My BIOS is fine. I get the normal single post beep and then things carry on from there.

---

### Post by az on 2008-06-09
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by Robux the great on 2008-06-09
Hi

If I get a fault and I think it is hardware related I 
use the Knoppix live CD.

It has lots of great tools on there for systems diagnosis

check out [http://www.knoppix.org](http://www.knoppix.org)

The hardware detection is excellent

I hope this helps

Regards

Rob

---

### Post by mips on 2008-06-09
> **Robux the great said:**
> 
The hardware detection is excellent


Not on my pc :) The earlier versions worked fine but I gave up after trying two later versions.

---

### Post by mips on 2008-06-09
> **nick_h said:**
> There is always memtest86+ on the Ubuntu CD to test the memory.

Hard drive manufacturers supply their own diagnostics utilities as jrusso2 has already mentioned.

You could try the [Ultimate Boot CD](http://www.ultimatebootcd.com/) which contains a lot of diagnostic utilities.

I will try that thanks. Hopefully it has dos utils on it as trying to get the linux kernel to load is a hit&miss affair.

---

### Post by mips on 2008-09-20
I found [Micro-Scope]("http://www.micro2000.com/microscope_suite/index.php")

---

### Post by revleo on 2008-09-20
i was gonna mention microscope it has some really good diag and test utilities

---

### Post by mips on 2008-09-20
> **revleo said:**
> i was gonna mention microscope it has some really good diag and test utilities

I must say I like it seeing it is a bootable livecd.

I ran a batch test and the only thing that failed was extended memory.

So now I'm busy testing each dram stick individually until I find the culprit.

Memtest86 & some other utils found nothing nothing wrong after extensive testing so I'm hoping this does the trick. A bit late as I got a new computer but this one I will give away.

---

### Post by smoker on 2008-09-20
> **mips said:**
> I get various different errors (I have not recorded any of the errors). Sometimes the kernel won't even load, other times it loads but then less than a minute into my desktop the pc crashes & reboots. Somtimes it hangs during the boot process. The same happens with liveCDs so it is not my OS. Everything so far points to a hardware problem of sorts.

I do not have access to spare components so I could swap things out and find the fault via a process of elimination unfortunately.

if the memtest is ok, this could be symptoms of a failing power supply. if you can't swop it to try another, try disconnecting some of the power drawing devices, eg, hard drive, 2nd hard drive if any, 2nd cd drive if any, floppy, and boot with just cd rom with live cd and see how it goes. if all goes well, start reconnecting stuff. one of the best buys i ever made was a power supply tester, great to have handy!

you also mentioned a new hard drive, even though it boots a live cd and you still have problems, i would still double-check all the cable connections to the motherboard.

best of luck

---

### Post by mips on 2008-09-20
> **smoker said:**
> if the memtest is ok, this could be symptoms of a failing power supply. if you can't swop it to try another, try disconnecting some of the power drawing devices, eg, hard drive, 2nd hard drive if any, 2nd cd drive if any, floppy, and boot with just cd rom with live cd and see how it goes. if all goes well, start reconnecting stuff. one of the best buys i ever made was a power supply tester, great to have handy!

you also mentioned a new hard drive, even though it boots a live cd and you still have problems, i would still double-check all the cable connections to the motherboard.

best of luck

I also thought it might be the PSU but purchased a new one and that did not help. I now have that MB installed in brand new case with another new 500W PSU (that is what my new pc came in but I did not fancy the case).

I tested with nothing connected but the bare essentials & also with a new HD. Still the same issue. Even without hard drives installed the problem persists.

The GPU has also been tested although I doubt that would have caused issues. I swapped between a 6600 & a 9600GT with no change.

Th only thing left is faulty memory which normal tests did not detect but micro-scope did. This might even be a faulty DIMM socket on the MB. The MB tests come up clear though.

Right now I'm individually testing each of my four dimms in the first dimm socket of the MB. Hopefully I can determine which one is the faulty one by doing it this way.

---

### Post by mips on 2008-09-30
> **mips said:**
> 
Right now I'm individually testing each of my four dimms in the first dimm socket of the MB. Hopefully I can determine which one is the faulty one by doing it this way.

Just some feedback. The problem was a faulty Kingston 512MB DDR400 DIMM.

I give Micro-Scope two thumbs up :)

---

