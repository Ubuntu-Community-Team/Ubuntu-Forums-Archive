---
title: "Troubles installing PP-a2 in VirtualBox"
date: 2012-02-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by AnrDaemon on 2012-02-22
I'm rolling my tests through a virtual emulation of my production network. I mean, i've tried to roll them. But the bunch of issues arising seems to be unbeatable.
The testing environment built using VirtualBox 4.1.8 for Mac and windows.
The list of issues start and end at installation times.
Attempt 1.
precise-desktop-amd64.iso, EFI mode. Start with GRUB menu instead of normal Ubuntu installer screen. Installation finishes without an issue ONLY AND ONLY if NO ANY NETWORK CONNECTION AVAILABLE.
However, it does not boot afterward, going into EFI fallback shell instead.
Attempt 2.
precise-desktop-amd64.iso, BIOS mode. It start as usual, with graphical display et all, but partitioning tool crashes right after it finishing partition scanning. Subsequently shown Unity desktop immediately get an Ubuquity application crash. Which means, the previous crash report disappears them Dash.

Tried multiple ways to combat the issue, played with options, chnaged chipset emulation and mode... No luck.
Is there any known issues with it, or any newer installation images? (Though I doubt it, the Alpha 2 was just released shortly before I started to play with it...)

---

### Post by larrypg on 2012-02-22
Hello,

Maybe I am missing something but I did not need to partition anything before installing 12.04a2 in virtualbox.  Just start virtualbox and install the iso into it.  Make sure you have downloaded the guest-additions and then install them from the device menu. This was using Ubuntu as host though.

---

### Post by AnrDaemon on 2012-02-22
You missing the fact that default partitioning is not virtual media friendly.
Also, the question remains: why it EVER crashes?
And no, I didn't came to the point of installing Guest Additions. It just won't fly in first place. (Though I'm able to start it in LiveCD mode... and operate, to some extent.)

---

### Post by larrypg on 2012-02-22
Hello again,

Maybe I am being dense but in reading over your original post again sort of begs the question...are you trying to install a real OS inside of a virtual OS?  If that is the case than I do not know the answer although I am not sure it is possible.  If it is not then...you just create a file with virtualbox.  It will ask you how large you want it and if it is dynamic.  You then install the iso into it.  There is no partitioning or running from a livecd.  If it is the later then maybe I can help if it is the former than not.

---

### Post by AnrDaemon on 2012-02-22
If you mean the "Mac and windows" part, these are two separate hardware platforms.
I'm using MacBook laptop with OS X Lion for most of simulation testing and as a shell console to servers, since it's not really suits for normal office work. Or coding, to say that. It's just terrible at anything but browsing internets and being a host for virtual machines.
But I do have identical setup of VMs on my desktop running Windows.

Regarding "you just"... Well, you certainly MAY just let it be. I'm not that kind of person, and I tend to get under the hood deeper to understand the reasoning behind decisions other people made, when writing how-to's and that kind...
For our little example, dynamic virtual drive best used in situation of one large partition, then it linearly grow up while you write data to it, without much of inner fragmentation. But when you partition it like Ubuntu does, creating a big first partiton and a small swap at the end, you create a fragmentation (or better said - cross-placement?), which is not good for classic rotary drive.

---

### Post by cariboo on 2012-02-22
There has been a problem with partitioning, I used the alternate install iso, as I got the same crash just after the release of alpha 2.

---

### Post by AnrDaemon on 2012-02-22
Thanks for the hint. Found the daily ISO downloads. Gonna give 'em a try after a nap.

---

### Post by AnrDaemon on 2012-02-22
Another quick question, may be offtopic, but...
How to properly partition the disk and where to assign the boot loader to be installed for UEFI boot?
I was trying (EFI/Swap/ext4) with loader either in the sda itself, or in sda1 (EFI partition) to no avail. It booting to the EFI fallback shell after installation.
Any clues?

---

### Post by larrypg on 2012-02-22
This is just because I am curious and do not want to inflame anyone when I made my previous post because I can not see any way it was not meant to be anything other than to try and help.

I have on more than a couple of times installed the iso's to virtualbox.  I have never been even asked or given any choice of partitioning other than how big a file I want it to be.  By your comments and Cariboo97's maybe there is that option but I have never seen it.

---

### Post by cariboo on 2012-02-22
@larrypg, Manual partitioning is call **Something** on the partitioning screen.

@AnrDaemon, I've never used EFI mode, as I've got Debian installed on a PPC G4, and it works so well I just start it up when I want to listen to music, and never paid attention to how it boots. :)

---

### Post by larrypg on 2012-02-22
Hello again,

I just installed Kubuntu, Xubuntu, and Ubuntu in VirtualBox 4.1.8 again.  At no point was I given the option of "something" or any other option of just choosing the size of the virtual disk.  If I am to be of any use to either those that might want help or even testing be it for myself or to help others it would be most helpful to have the same thing showing as others see.  Any hints of what I should  do would be helpful.  So far I have not had even one oops other than if I did something dumb.  There have been no problems once I was able to install guest additions and extension pack of any kind. 

Any help on maybe getting this to break (to see what other's see) would be appreciated (just sort of kidding).

---

### Post by cariboo on 2012-02-22
Have a look at the screenshot this is for the 32-bit version, but that shouldn't make any difference, see the Something else choice?

---

### Post by effenberg0x0 on 2012-02-22
@OP
I'm using Ubuntu PP as a Host for Windows 7 32/64-Bit, Ubuntu (OO,PP) plus Lubuntu, Xubuntu, Kubuntu and other Linux distro's guests. I have never had a problem installing any OS on VMWare or VirtualBox (despite the eventual need to recompile Kernel modules). I actually use both VirtualBox and VMWare guests as my main work desktop. These VMs run non-stop for days.

I'm not sure how EFI goes (as I don' use it). But, AFAIK, you shouldn't be having any problems. 

A pertinent question would be: Does it work perfectly in Ubuntu Oneiric Ocelot? Because, if so, you might have a new and unknown / unreported VirtualBox bug in your hands (which should be explored further, probably by VirtualBox people).

Regards,
Effenberg

---

### Post by AnrDaemon on 2012-02-23
I don't use Oneiric. Lucid and Hardy are working fine in VM.
I would give Oneiric a try, if my tests with fresh daily PP ISO's fail again.

---

### Post by effenberg0x0 on 2012-02-23
> **AnrDaemon said:**
> I don't use Oneiric. Lucid and Hardy are working fine in VM.
I would give Oneiric a try, if my tests with fresh daily PP ISO's fail again.

Ok, and if you are able to collect some error message from logs, it could help: I believe you are facing a bug that needs dev attention, but maybe we're overlooking something easily fixable.

And regarding VirtualBox options: Could you give us an overview of what you have set at Settings / System / *? Options such as the emulated chipset, NX/PAE, number of CPUs, EFI, IO APIC, Nested Paging, etc do cause some weird behaviors sometimes.   

Regards,
Effenberg

---

### Post by AnrDaemon on 2012-02-24
Indeed. I'll start taking proper notes once I get some dust cleared up.

As it appeared, I don't have enough free space on my windows host >.>
Have to dig through some fraps and purge/recode, hehe...

---

