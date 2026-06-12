---
title: "virtualbox - how good a replacement is it from a real os?"
date: 2010-09-08
forum: Virtualisation
---

### Post by fuzzylogic25 on 2010-09-08
I am installing ubuntu and wish to run windows xp through virtualbox, just so i can run some of the windows apps temporarily until i find a proper replacement for linux. i would much rather this than have to boot into windows xp everytime i need it. but my question is, what is the drawbacks/disadvantages/limitations of running xp on virtualbox than it is in boot?

all i can see is:
1. use up more system memory 
2. use up more cpu

is there any other limitations? I mean, what i really want to know is, can you do EVERYTHING you could do normally in xp when booting?

---

### Post by clhsharky on 2010-09-08
fuzzylogic25

> is there any other limitations?
Yes, Limited 3D.(virtual hardware)
>  I mean, what i really want to know is, can you do EVERYTHING you could do normally in xp when booting?
No, Games would be better with wine.
Every thing else should be normal.

Sharky

---

### Post by gnicko on 2010-09-08
> **fuzzylogic25 said:**
> I am installing ubuntu and wish to run windows xp through virtualbox, just so i can run some of the windows apps temporarily until i find a proper replacement for linux. i would much rather this than have to boot into windows xp everytime i need it. but my question is, what is the drawbacks/disadvantages/limitations of running xp on virtualbox than it is in boot?

all i can see is:
1. use up more system memory 
2. use up more cpu

is there any other limitations? I mean, what i really want to know is, can you do EVERYTHING you could do normally in xp when booting?

You are correct in your assumptions, but VirtualBox seems to handle things very gracefully. Much better than anything else I've used (especially VM Ware.) Be sure to install the VirtualBox Host Extensions...to get the full-screen effect, better mouse controls, etc.


It really depends on how "robust" your computer is. If you have a fairly new machine with a decent amount of memory and so forth, you should be OK. The resource settings are adjustable so you can fiddle around to get the best mix.

I have an XP virtual machine on my computer and it runs pretty good. I haven't had the need to fire it up in months, but its there if I need it. 

Once you get used to Linux, it will seem that XP lags unmercifully...with or without virtual machines. I expect after the first couple of days, you won't need the XP anymore.

---

### Post by fuzzylogic25 on 2010-09-09
Thank's for the replies. My computer specifications are 1.86ghz Core 2 Duo, 4GB Ram, 32-bit Ubuntu OS. 

I have partitioned the drive such that I have 100GB for /root and 8GB for swap. I chose a large swap for hibernation and also because I know I will be in situations where more than 4GB of ram will be used.

Is this sufficient? I want to run Ubuntu as my main OS now because I don't like Windows 7 (Ubuntu is dual booted with Windows 7). 

Another thing is, for the time being, I would like to download files and do some minor things using windows xp in virtualbox. This means that files will be downloaded to the virtual drive C. Is it possible for the virtual Win XP to access/read/write to an actual partition that is of course NTFS.

For example, my main drive is partitioned like this:

WIN7 70GB NTFS
UBUNTU 100GB EXT3 (The virtual Win XP is in this partition)
SWAP 8GB 
DATA 100GB NTFS

So the DATA partition is NTFS and I was hoping that would be used as a partition where both Virtual Win XP and Ubuntu can read/write to so I can exchange files between the Operating systems. 

So my questions are:
1. can you have a drive where ubuntu and the virtual OS can both read/write to, ie an actual partition or another hard disk?
2. Can you change the amount of ram allocated to Win XP? I would like to only dedicate 512 in some instances and when I know im goin to need more I want to be able to allocate 700 or 1GB
3. Can you also change the amount of hard disk space allocated for virtual C drive once it is created?

---

### Post by TNT1 on 2010-09-09
> **fuzzylogic25 said:**
> 

For example, my main drive is partitioned like this:

WIN7 70GB NTFS
UBUNTU 100GB EXT3 (The virtual Win XP is in this partition)
SWAP 8GB 
DATA 100GB NTFS

So the DATA partition is NTFS and I was hoping that would be used as a partition where both Virtual Win XP and Ubuntu can read/write to so I can exchange files between the Operating systems. 

So my questions are:
1. can you have a drive where ubuntu and the virtual OS can both read/write to, ie an actual partition or another hard disk?
2. Can you change the amount of ram allocated to Win XP? I would like to only dedicate 512 in some instances and when I know im goin to need more I want to be able to allocate 700 or 1GB
3. Can you also change the amount of hard disk space allocated for virtual C drive once it is created?

1. The easiest is to setup shared folders. The virtual OS then sees the shares as network drives, they can be pretty much any folder on the host machine. I don't think you will get the virtual machine to read/write to the windows 7 partition you have, it might though.
2. Yes, you can change all those settings as needed. Not on the fly though, you need to close the virtual machine, open the properties of it, adjust the RAM or whatever, and then start it again.
3.Yes, same as above 2.

Also, if you need usb support in the virtual machine, get the one from the virtual box website, the one in the repository has vpn capability but no usb.

---

### Post by deserthowler on 2010-09-09
> **fuzzylogic25 said:**
> is there any other limitations? I mean, what i really want to know is, can you do EVERYTHING you could do normally in xp when booting?

One BIG limitation I found with VBox and XP is if I get a virus, I load the last good configuration.  This severely limits my experience in removing virii and malware.  =D>

Earl

---

### Post by fuzzylogic25 on 2010-09-09
If you get a virus then surely if you have some antivirus software installed within XP before hand it should be ok?

Thats one reason why i like this set up, because it seems like if win xp gets a virus or some hack ubuntu, the main OS will still be fine.

---

### Post by andrew.46 on 2010-09-09
Hi fuzzy,

> **fuzzylogic25 said:**
>  My computer specifications are 1.86ghz Core 2 Duo, 4GB Ram, 32-bit Ubuntu OS.

I run multiple VMs with virtualbox with the same processor but only 2GB Ram so I suspect you will have no trouble :).

Andrew

---

### Post by deserthowler on 2010-09-09
> **fuzzylogic25 said:**
> If you get a virus then surely if you have some antivirus software installed within XP before hand it should be ok?

Thats one reason why i like this set up, because it seems like if win xp gets a virus or some hack ubuntu, the main OS will still be fine.

I have friends who work on XP and much of their income comes from removing viruses and spyware and trojans on systems with anti-virus and anti-spyware software.  I have heard some are extremely difficult and expensive to remove taking hours.  Restore points can become contaminated.  Going back to a safe clean install as allowed by Vbox seems like a good plan.

As I said, I don't remove viruses ... I remove Windows.

Earl

---

### Post by fuzzylogic25 on 2010-09-09
you are right on that. i would say prevention is better than cure but even with an antivirus program ive still managed to have issues. i once had full antivirus/firewall protection and some kinda virus came through firefox and stopped me from accessing virtually ANY program, unless i went to some website and paid for some fake antivirus program. my virus scanner couldnt even work.

can you save images of the virtual winxp? because what i would hate to do is install everything again. I would rather install everything and configure all apps, then save an image of that so i can revert to that. i thought maybe if i just saved that file virtual box creates it should be ok? 

if by restore points u were referring to windows system restore, then i think its useless. i hated that feature.

---

### Post by uRock on 2010-09-09
If your PC has enough power to run an OS within an OS, then it will do fine. This also depends on the OS.

I have an AMD 64bit dual core with 2GB RAM. I can give mostly any OS 512MB RAM and it will run great, though a bit slower. It is definitely good for taking OSes for a test drive before making less temporary decisions of installing in a partition.

---

### Post by Ginsu543 on 2010-09-10
I allocate one of my eight Intel i7 "cores" @ 4.2 GHz and 2 GB out of 6 GB of DDR3 system RAM to run a Windows XP guest on VirtualBox and it runs better than when I used to run Windows XP natively on my previous machine (3.2 GHz Intel Core2Duo E6600 with 2 GB DDR2 RAM).

---

### Post by Iowan on 2010-09-10
Moved to Virtualization

---

### Post by cliffdodger on 2010-09-10
Would someone be crazy to try to do audio recording on win xp 32bit (guest OS) in a virtual box on a 64 bit linux install?  Using line6 hardware (usb asio sound card - requires pretty low latency or you get noise in your recordings) on a Q6600 Intel 2.0Ghz Quad core with 6 gigs of DDR2-800 ram? 

Does that sound achievable or ludicrous? 2 cores and 3 gigs of ram could easily be dedicated to the "recording box" guest OS install of XP and the mobo is an intel board with VT support.

---

### Post by fuzzylogic25 on 2010-09-11
Another thing i wanted to ask is, can you move virtual desktops to other operating systems using same computer hardware?

For example, im currently using Windows 7 now and will move to Ubuntu in 2 weeks (cant do it yet because I am very busy working on other stuff). I want to have as much stuff ready. So I was thinking of installing Windows XP in VirtualBox Under Windows 7, then move that over to Ubuntu when im ready to use Ubuntu. Is this possible?

I was thinking you could literally just move the .vdi file over and open it through the virtualbox run in ubuntu.

---

### Post by fuzzylogic25 on 2010-09-11
also has anyone tried printing from a virtual os? i havnt been able to find linux drivers for my printer so i would love to use virtualxp for printing word docs.

---

### Post by uRock on 2010-09-11
Set up network printing between your host and VM, they should see each other in the network. [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by fuzzylogic25 on 2010-09-13
This is the problem. There are no drivers for my printer for linux. thats one of the major reasons why i wanted to have virtualbox win xp installed since there are drivers for windows xp.

so is this possible? i was thinkin maybe somehow once the printer is plugged in, virtualbox could pass that port into the OS (something like that, dont really know how it works with VB).

---

### Post by Dr. C on 2010-09-13
> **fuzzylogic25 said:**
> This is the problem. There are no drivers for my printer for linux. thats one of the major reasons why i wanted to have virtualbox win xp installed since there are drivers for windows xp.

so is this possible? i was thinkin maybe somehow once the printer is plugged in, virtualbox could pass that port into the OS (something like that, dont really know how it works with VB).

This is possible with the PUEL version of Virtualbox for a USB printer, but not with the Open Source Edition.

---

### Post by fuzzylogic25 on 2010-09-14
hhmm this is quite a limitation. so hardware cant be used properly through the virtualbox OS unless its through the virtual network?

Eg, if theres two or three hard disks in the computer, i cant see any of them under virtual OS unless its networked? What about the CD-ROM?

---

