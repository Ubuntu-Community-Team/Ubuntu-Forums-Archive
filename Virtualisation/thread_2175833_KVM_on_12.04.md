---
title: "KVM on 12.04"
date: 2013-09-21
forum: Virtualisation
---

### Post by M_Zainal_Abidin on 2013-09-21
Hi,

I try create virtual machine on my desktop. I saw error when creating vm. Here is screenshots. What it mean by that?
[http://postimg.org/image/9wcxu994n/](http://postimg.org/image/9wcxu994n/)

Hope sifu here can help me.

Thanks.

---

### Post by TheFu on 2013-09-21
I use KVM all the time for Linux VMs. It works without any real thought needed, though some settings are much, much better than others.
Loading Windows brings addition complexities - mostly related to licensing.  Unless you have a retail license, the copy you have might be locked to a specific motherboard .... I know that HP/Dell and most other hardware makers due this as part of their OEM agreement with Microsoft.

I'm positive that Win7 will load and work under KVM. I do this with my TV recording VM. I don't recall any specific settings that were required, but I've been doing virtualization since the 1990s, so I probably pick some settings without thinking.

If you aren't using an OEM license - perhaps a trial license from Microsoft or a technet license - then it should load provided the virtual hardware choices work.

Have you googled for a "Win7 under KVM guide"?  I found [this]("http://www.linux-kvm.org/page/Windows7Install") and [this]("http://ubuntuforums.org/showthread.php?t=1293199") and [this]("http://mikewilliamson.wordpress.com/2012/04/11/making-virtual-machines-with-kvm-and-virt-manager/").  Use the SATA HDD ... virtio isn't worth the hassle on Windows.  For the NIC, use an Intel PRO/1000.

Sorry, I'm not more help, but at least you know it is possible AND that it works under 12.04 x64 and 10.04 x64.

---

### Post by M_Zainal_Abidin on 2013-09-21
Yeah, i know. It's useless when create a virtual machine and cannot connect to internet. Sometimes i need to use windows but usually i will use ubuntu. I have some apps that need to run under windows. I already test apps windows run on wine but got a few error. It took me hard time and i don't want to troubleshoot small thing. Better use vm windows. But seems this error not available on google also. Need some advice from expert here.

---

### Post by 1clue on 2013-09-21
KVM works fine for Windows.

Licensing:  There's a rule of Windows that most people don't seem to get that I live by.  Even if you bought your machine with Windows and intend to actually USE windows on it, the first thing you do is download an original image from Microsoft (or go buy a licensed box from a local store if you have one) and buy a real license.

This official image from Microsoft has none of the malware preinstalled, none of the trial offers, none of the crap that sucks up CPU cycles on it.  It actually works, it's stable and it's pretty nice, if you like that sort of UI and buy into the "commercial everything" idea.

If you're using a VM, then your very best approach is to download the iso FROM MICROSOFT and then call the Microsoft guys to help you figure out the best license.  When you start mousing around the downloads at Microsoft they'll give you a number to call.  There are a bunch of different licenses for the same exact software, for just about everything Microsoft sells.  Some of them come cheap but you can only use them for development.  Some of them are home use and you get exactly one computer to put it on.  Some of them are set up for virtualization and they don't care if details of your system (like cpu type) change a few times.  Some of them are set up so you can install it a bunch of times over and over, as long as it's on one system at a time.  Some of them are educational use.  It all depends on what exact software you want a license for and what sort of use you intend to put it to.

I've done this any number of times for my work.  The phone number to Microsoft is totally stress free.  They don't sell the licenses there, they just have people familiar with the licenses available who are able to tell you which one to get.  There's a list of sites that sell genuine licenses.  If you call there, they know you are trying to follow the license agreement, or why would you call?  So tell them exactly what you want, and there may be something that fits your needs exactly.  At least you'll be a lot happier about it than if you're trying to make the wrong license fit your setup.  If you're a student, tell them.  If you're a developer, tell them.  If you're a developer who is also using some of the software for commercial use, say it.  If you're a guy tinkering around at home, then let them know.

For some reason people still seem to think that virtualization is naughty or somehow a grey area for software licenses.  It's not.  Microsoft (and every other big business) knows a lot about virtualization.  Microsoft sells their own virtualization engine.  They get it.  They know how this sort of thing works, and they have licenses ideal for typical virtualization setups.  They understand large, medium and small businesses, home offices, and one-man businesses.  They understand students, and they absolutely positively understand nerds.  They know about the clouds, public and private.  They know about Crossover Office.  They darned sure know about Linux even if they don't support it.

I don't advocate Microsoft, all I'm saying is that if you have a need for a Microsoft product and want to be legitimate about it, then don't be afraid of the help desk, ESPECIALLY before you even buy the license.

For that matter, this goes for any other commercial product too.

---

### Post by M_Zainal_Abidin on 2013-09-22
The reason i post this is to request help from sifu here. Not to ask your opinions. Please refer a link on first post.

---

### Post by TheFu on 2013-09-22
> **M_Zainal_Abidin said:**
> The reason i post this is to request help from sifu here. Not to ask your opinions. Please refer a link on first post.

I've looked at the link. Alone, it doesn't tell me anything. What have you tried? What else didn't work? What do the log files show?  Can you dump the VM setup xml file and post it?  Seeing 1 bubble warning isn't enough for a solution in this case. Sorry.

For example, have you tried different virtual network cards?

---

