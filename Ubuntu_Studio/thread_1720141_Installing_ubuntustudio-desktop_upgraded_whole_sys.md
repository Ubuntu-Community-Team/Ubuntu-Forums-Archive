---
title: "Installing ubuntustudio-desktop upgraded whole system"
date: 2011-04-02
forum: Ubuntu Studio
---

### Post by fudoki on 2011-04-02
Running Ubuntu 10.10 was having problems with mp3 audio files "skipping" during playback.  Went to Ubuntu Help Wiki 
[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu) 
and found advice to install the Ubuntu Studio Real Time (-rt) kernel by simply installing "aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt".  Simple enough.  Having run Ubuntu Studio in the past with good results, this seemed straightforward and good advice - especially since Ubuntu studio had recently iterated to the 10.10 level.

After the files installed, I rebooted and ran "uname -r" to verify the new kernel was running and learned, to my horror, that the ENTIRE SYSTEM had been upgraded to UBUNTU 11.04 ALPHA!!!!  The linux-rt kernel had not installed, since it is NOT YET AVAILABLE IN THE REPOSITORY TREE!

Having used Linux since the early mid-90's, and being a programmer/software engineer, I knew what it would take to "unring the bell" - a re-install.  This would put me in limbo for at least a week since this is my main production box!

Found an available "low-latency" kernel in the ppa-launchpad repository,
[https://launchpad.net/~abogani/+archive/ppa](https://launchpad.net/~abogani/+archive/ppa)
 and the updated Nvidia drivers to work with this kernel.  Allesio does wonderful, very competent work - and I highly recommend anything he offers to the Community.

The kernel works great, is brilliantly fast and smooth, and solves the latency problems and then some.  Can't wait until the -rt kernel becomes available.  The problems are: 1) I cannot update over 1000 files because they want to REMOVE MY VIDEO DRIVERS TO INSTALL.  Just can't work with NO MONITOR folks...  Need the real graphics for graphic and video production - not the lame "nv" or "fbdev" generic drivers, and 2) THERE WAS NO WARNING, REQUEST FOR CONFIRMATION, OR OTHER INDICATION THAT A DISTRO UPGRADE TO AN EXPERIMENTAL RELEASE WAS GOING TO OCCUR!!!  There were not even installation candidates for half the software, and I wound up with Ubuntu, NOT Ubuntu Studio as the command line ordered.

This is a big problem IMHO.  Were I not a linux user for many years and a programmer in Unix/Linux for nearly 30 years winding up with an inert system would be almost a certainty.  I will not bother to list the half-dozen discrepancies in the sound advice provided by the Help Wiki due to the [mis-]behaviour of the upgrade process.

If there are any questions, or should I need to point out specifics, feel free to let me know and I'll help out in any way I can.

Mainly, folks need to be aware of this issue if they need to install the Ubuntu Studio rt kernel in their 10.10 Ubuntu system - they should do the process manually using dpkg and not use aptitude (and I would guess synaptic).

Have had to update almost 1000 files that WILL update correctly BY HAND.  My system is working GREAT!  The 11.04 kernel just SINGS, seems ROCK SOLID, and I am very happy with it.

It would have just been real nice to have some idea - IN ADVANCE - what I was getting into.  Unless you type "UPGRADE DISTRO", this should NEVER happen - particularly when there are not even available update candidates for the progs specifically ordered on the command line.

Sorry for the prolix post, just can't be any more brief with this kind of issue.

Again, I recommend 11.04 - I am impressed, especially with the low-latency kernel build; but this glitch could really mess up all but the most experienced users, and had I not typed "uname -r" FIRST I would have been SO screwed...

---

### Post by fudoki on 2011-04-02
OK, just found this page: [https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)
that answered a lot of questions - like "Why did this happen??"

Still, some confirmation or warning message would be in order to keep the unsuspecting user simply following the straightforward advice in the Help Wiki from falling off a cliff unawares...

fudoki

---

### Post by Rasa1111 on 2011-04-02
damn that's messed up Fudoki! :o

Good thing it was you and not some other poor newb! (like me!) lol
Glad you got it worked out man. 
So audio is good now to eh? 

Cool to hear about the 11.04 kernal being so nice.
Gives me something to look forward to in natty i suppose. lol 
Thanks. :)

---

