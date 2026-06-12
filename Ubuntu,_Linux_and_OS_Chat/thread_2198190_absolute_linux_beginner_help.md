---
title: "absolute linux beginner help"
date: 2014-01-07
forum: Ubuntu, Linux and OS Chat
---

### Post by syed.zeshan14 on 2014-01-07
okay so im a absolute beginner who wants to switch from windows to linux !
reason for switching - windows os is expensive (cant afford it right now ),windows os is easily susceptible to getting infected,slows down as i install many applications and as time passess windows slows down.
my laptop configuration - dell vostro 2520 4 gb ddr3,2nd gen intel core i3 clocked at 2328 mhz ,500 hdd..
my needs- AUTOCAD (computer aided engineering drawing),normal browsing,normal video playing and audio , very minimal to no gaming,android normal flashing (adb,flashtool etc)
im into civil engineering field so basically i would be working with engineering softwares like autocad,rivet,designing softwares etc
i know of running linux on a virtual machine on windows. but is it possible to run windows on a virtual machine on linux ?? if yes then can i install any applications on it ? if yes then there any performance related issues ?
i have gone through wine but it doesnt support all windows softwares especially CAD softwares.
i have gone through ubuntu and linux mint websites and they both look cool. 
i want suggestions for selecting linux distro satisfying my needs (sorry i cannot download all and test it one by one because im on a limited bandwidth).
the UI is not my concern, only performance,support and wine-compability is my concern.
i wish to install 64 bit linux on my laptop and i need help in choosing one and a link for the suggested linux distro (download,installation,usage).
the last time i tried to installing ubuntu 12.04 lts,i messed up my laptop and all my disk drives got formatted and i dont want to repeat it again.
any suggestion/help is highly appreciated and i apologise if any of my questions has been already answered.
thank you !

---

### Post by Impavidus on 2014-01-07
CAD can indeed be problematic. Few decent CAD programs run on Linux (or so I am told) and the Windows ones don't run in wine. You can use a virtual machine. 4GB memory isn't very much for virtual machines, but should be doable. In priciple any Windows program should run, although using usb devices etc. may not work. Of course, performance will be worse than on a real Windows install (only 1 CPU core available, only part of the memory, things like that) and for a virtual machine you still need an expensive Windows licence.

---

### Post by Bucky Ball on 2014-01-07
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by syed.zeshan14 on 2014-01-07
thanks for the reply.
I can upgrade the ram so that virtual machine works well ! 
and can I dual boot Windows and linux ? (the Dell cc guy told me not to do so )
and do answer about the other part ( choosing linux distro ) also .
and ya one more question is why is it that major softwares like AutoCAD,photoshop etc designed only for Windows ?
is Microsoft dominant in making them develop softwares only for their os or is it because many people use Windows os ?

---

### Post by lykwydchykyn on 2014-01-07
> **syed.zeshan14 said:**
> okay so im a absolute beginner who wants to switch from windows to linux !
reason for switching - windows os is expensive (cant afford it right now ),windows os is easily susceptible to getting infected,slows down as i install many applications and as time passess windows slows down.
my laptop configuration - dell vostro 2520 4 gb ddr3,2nd gen intel core i3 clocked at 2328 mhz ,500 hdd..
my needs- AUTOCAD (computer aided engineering drawing),normal browsing,normal video playing and audio , very minimal to no gaming,android normal flashing (adb,flashtool etc)
im into civil engineering field so basically i would be working with engineering softwares like autocad,rivet,designing softwares etc


You seem to be mired in a lot of Windows-only software, and the only reasons you give for switching are negatives about Windows.  Not to be cynical, but this usually doesn't play out so well.

Forget WINE; in my experience, it works with (1)Old versions of MS Office, (2) Old versions of Adobe CS, and (3) a bunch of games.  Outside of that, it produces more frustration than functional results.

You have several virtual machine options: VirtualBox, VMWare, Xen and KVM (which is built into the kernel itself).  They vary in performance and ease-of-use, but all of them will give you a performance hit.  You can't run two operating systems and virtualize hardware without incurring a performance cost.

You can dual boot, but IME you're going to end up staying in one OS or the other.  If most of your work is being done in Windows, are you going to reboot into Linux just to browse the web?

Not trying to talk you out of it, but just think these things through; is there are reason -- other than "not using Windows" -- that you really want to use Linux?

---

### Post by The Cog on 2014-01-07
You can dual boot Windows and Linux. I can't think why the Dell guy said not to. You may have difficulty with drivers and Linux - try a live CD before committing to installing on the hard disk.

You may not need more RAM to run windows inside a VM. I occasionally run 2 or 3 copies of windows inside VMs on my laptop with 4G RAM. But maybe CAD programs need more than the stuff I run. Still, more than 4G RAM is not an absolute requirement. A windows licence is though.

For a Linux distro, Ubuntu or one of the variants (Xubuntu, Lubuntu, Kubuntu) should be fine. My personal choice is Xubuntu. The variants have different look/feel but the same OS underneath.

Yes, Microsoft has for years been doing everything it can, both legal and illegal to leverage its dominant position to suppress other OSs.

---

### Post by Bucky Ball on 2014-01-07
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by syed.zeshan14 on 2014-01-07
> **lykwydchykyn said:**
> You seem to be mired in a lot of Windows-only software, and the only reasons you give for switching are negatives about Windows.  Not to be cynical, but this usually doesn't play out so well.

Forget WINE; in my experience, it works with (1)Old versions of MS Office, (2) Old versions of Adobe CS, and (3) a bunch of games.  Outside of that, it produces more frustration than functional results.

You have several virtual machine options: VirtualBox, VMWare, Xen and KVM (which is built into the kernel itself).  They vary in performance and ease-of-use, but all of them will give you a performance hit.  You can't run two operating systems and virtualize hardware without incurring a performance cost.

You can dual boot, but IME you're going to end up staying in one OS or the other.  If most of your work is being done in Windows, are you going to reboot into Linux just to browse the web?

Not trying to talk you out of it, but just think these things through; is there are reason -- other than "not using Windows" -- that you really want to use Linux?
1)i dont have a valid windows license so dont want to use a pira*ed one .
2)windows runs slow even on my bro's original licenced windows.
3)windows crashes a lot and needs a anti virus to protect it
these are the issues im facing and what if they co incide to be negatives about windows ?
also i have a life beyond computers and i use computers mainly for the professional softwares not for wasting my time 'browsing the web'!
there is some something called 'CONSCIENCE' also and the only reason for me to stay on windows is the professional softwares.
your are being PLAIN JUDGEMENTAL in your thoughts and i think learning ETHICS is more important than learning anything else !
if you cant help me,at-the-least dont spam my thread !!

---

### Post by syed.zeshan14 on 2014-01-07
> **The Cog said:**
> You can dual boot Windows and Linux. I can't think why the Dell guy said not to. You may have difficulty with drivers and Linux - try a live CD before committing to installing on the hard disk.

You may not need more RAM to run windows inside a VM. I occasionally run 2 or 3 copies of windows inside VMs on my laptop with 4G RAM. But maybe CAD programs need more than the stuff I run. Still, more than 4G RAM is not an absolute requirement. A windows licence is though.

For a Linux distro, Ubuntu or one of the variants (Xubuntu, Lubuntu, Kubuntu) should be fine. My personal choice is Xubuntu. The variants have different look/feel but the same OS underneath.

Yes, Microsoft has for years been doing everything it can, both legal and illegal to leverage its dominant position to suppress other OSs.
thanks for the reply. i will try with ubuntu

---

### Post by Bucky Ball on 2014-01-07
*Thread closed.*

From the very beginning of the ***CoC***, which you read on joining:

> ... we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with respect. 

lykwydchykyn wasn't spamming the thread, they were giving you good advice. 

If you use mostly Windows software, especially things like CAD, Windows might suit you better than Linux. Please read my link in post #7.

---

### Post by The Cog on 2014-01-07
lykwydchykyn was not "spamming" your thread. 
Actually, I pretty-much agree with him on every point except for the performance hit using a VM, which I think for many programs will be small enough to not be noticeable.

---

### Post by syed.zeshan14 on 2014-01-07
> **Bucky Ball said:**
> *Thread closed.*

From the forum ***Code of Conduct***:



From the very beginning of the ***CoC***, which you read on joining:



lykwydchykyn wasn't spamming the thread, they were giving you good advice. 

If you use mostly Windows software, especially things like CAD, Windows might suit you better than Linux. Please read my link in post #7.
i meant i didnt want to use a pirated windows copy

---

