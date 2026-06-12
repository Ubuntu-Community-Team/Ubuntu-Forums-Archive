---
title: "Jack what the.."
date: 2008-12-28
forum: Ubuntu Studio
---

### Post by j@am1 on 2008-12-28
Im just curious about something.I've just installed the current Ubuntu via Wubi on 2 identical machines. (The only exceptions,hardware-wise being amount of RAM,nics,and vid cards)Ive installed,updated and configured these exactly the same on both machines,also. 
On machine #1, I began to try to muck around with Rosegarden,Zsyn and Hydrogen. Even though Ive installed every Jack package,app,and dependancy,etc I can find on the repositories,I cant -for the life of me-get Jack to start or anything to connect to the Jack server. Ive removed and re-installed it half a dozen times,and followed almost every (vague in the extreme) how-to/tutorial etc. but nothing.Zilch.

On machine #2, I fire it up,launch the apps,and can immediately connect,and begin mucking around recording and editing audio and midi tracks without so much as a hiccup....
For the life of me,I cant find what-if any-discrepancy there might be to cause this difference between the 2 machines. (and I fail to see where any differences in network cards or video cards could even hope to come into play on this matter) 
It's not a crisis,now that I can at least mess with my music on at least one of the machines,but..I'd still like to get both set-up as identicaly as possible.

Another question,If I may,I have an Audigy sound card with the external I/O breakout box in another (windows-yuk) machine,that I am considering installing into the #2 machine. Any issues I need to know about with this before I go to the trouble? I really do lack the time to waste farting around with command-lines,config files,and resisting the temptation to toss the machine through the office window..I love Linux,and this distro especially,but time-consuming,frustrating as heck set-up issues for which I have almost zero patience could well send me -reluctantly-back to windows...

---

### Post by thorgal on 2008-12-28
the very first thing you need to check is if the Audigy has a working ALSA driver (or is it firewire ? in which case check if FFADO supports it). Failing at this will only lead to immense frustration and hair-loss. 
If your card has a good linux driver, then I don't see why it should be a problem. 

I built up a linux DAW, read a lot beforehand and chose RME Hammerfall DSP as my audio system because I knew there was a very good ALSA driver for it. Things worked about OOB and I have no regret after 1.5 year of operation :) But it did require a lot of preliminary homework (reading).

---

### Post by j@am1 on 2008-12-28
Excellent.,ty. 
Is there a repository from which to get Hammerfall? Not at those machines now,but do not recall seeing it in any of the packagemanagers.

---

### Post by thorgal on 2008-12-28
the RME HDSP system is a card (PCI, PCIe or PCMCIA, depending on which model and revision) that often goes in pair with an external IO box, in my case the Multiface II. Have a look here for the Multiface II :

[http://www.rme-audio.de/en_products_multiface_2.php](http://www.rme-audio.de/en_products_multiface_2.php)

The drawback : it is expensive and you will need external preamps for microphones (I own an RME QuadMic preamp, very satisfied as well).

The way to drive it in linux is to have the firmware loader (part of the alsa-firmware package), the hdspconf and hdspmixer apps (part of the alsa-tools packages). But really, make sure you need that many IOs and can invest financially. If you goal is to record yourself only and do limited instrument recordings, it may be too much, in which case a M Audio Delta card will be more suitable and way cheaper.

---

### Post by j@am1 on 2008-12-28
Ah,nm. Way outside my budget anytime soon. Especially since Ive already invested in a fair amount of hardware that does much the same thing anyway.

---

