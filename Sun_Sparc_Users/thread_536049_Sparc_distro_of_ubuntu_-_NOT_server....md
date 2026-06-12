---
title: "Sparc distro of ubuntu - NOT server..."
date: 2007-08-27
forum: Sun Sparc Users
---

### Post by marmaj on 2007-08-27
I have been searching high and low for a SPARC workstation distro of ubuntu, but I am finding none.

What I've found are the following:

ubuntu-7.04-server-sparc.iso
ubuntu-6.06.1-server-sparc.iso

both of them - as you see - servers.

I have installed them on Ultra 2 and Ultra 60 with no problems, and then installed ubuntu-desktop on top of the servers, again, with no problems.

**My question is:**  is there a workstation distro of Ubuntu available (just like for i386 and amd64) or am I stuck with the server?

I would like to have both the Ultra 2 and Ultra 60 run as lean on boot as possible, since I will be using them  as hosts for VMware workstation and/or VirtualBox.

Comments are most welcomed!

Best regards,

marmaj

---

### Post by Lord Illidan on 2007-08-27
I am not too familiar with SPARC architecture, but I suppose you can always install ubuntu-desktop from the CLI?

---

### Post by marmaj on 2007-08-27
Yes, this is what I did (see above).

But it is running on TOP of server, and I really would like to run UBUNTU WORKSTATION, and not SERVER with desktop installed on top of it.

marmaj

---

### Post by mips on 2007-08-27
Uhm, did you search at all ?

[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

---

### Post by marmaj on 2007-08-27
yes, I've searched, obviously not too successfully.

Thank you for the link.  I got the alternate distro and will try it tonight.

-mm-

---

### Post by marmaj on 2007-08-28
This exercise is a proof-of-concept for running Linux on Sparc hardware (host) with VMware Workstation and various Windows flavors as guests.

In an effort to find the best Sparc/Linux combination for VMware host, I have performed a number of various Ubuntu distros installs on two SUN Ultras &#8211; Ultra 2 and Ultra 60 with mixed results.

Here is the summary:

Hardware:

Ultra 2, 2 x 300 MHz CPUs, 2 GB RAM, 2 x 36 GB SCSI drives, Creator frame buffer video card (S-bus)
Ultra 60, 2 x 450 MHz CPUs, 2 GB RAM, 2 x 36 GB SCSI drives, Creator frame buffer video (PCI)

Each hardware platform received the same treatment in terms of various &#8216;buntu&#8217;s:

1.  ubuntu-6.06.1-server-sparc.iso with &#8220;sudo apt-get update&#8221; followed by &#8220;sudo apt-get install ubuntu-desktop&#8221; followed by the updates

2.  ubuntu-6.06.1-server-sparc.iso with &#8220;sudo apt-get update&#8221; followed by &#8220;sudo apt-get install kbuntu-desktop&#8221; followed by the updates

3.  ubuntu-6.06.1-server-sparc.iso with &#8220;sudo apt-get update&#8221; followed by &#8220;sudo apt-get install xubuntu-desktop&#8221; followed by the updates

4.  ubuntu-7.04-server-sparc.iso with &#8220;sudo apt-get update&#8221; followed by &#8220;sudo apt-get install ubuntu-desktop&#8221; followed by the updates

5.  ubuntu-7.04-server-sparc.iso with &#8220;sudo apt-get update&#8221; followed by &#8220;sudo apt-get install kubuntu-desktop&#8221; followed by the updates

6.  ubuntu-7.04-server-sparc.iso with &#8220;sudo apt-get update&#8221; followed by &#8220;sudo apt-get install xubuntu-desktop&#8221; followed by the updates

7.  ubuntu-7.04-alternate-sparc.iso with all the updates

8.  kubuntu-7.04-alternate-sparc.iso with all the updates

-  Stable seemed (1), (2) and (3), based on 6.06 server on either machine.
-  (4), (5) and (6) had a number of smaller issues with the desktops, but I think most of them were fixable.  It seemed that both Ultra 2 and Ultra 60 had similar or same problems.
-  (7) and (8) had a variety of more serious issues such as HAL not starting, many other components dying on GUI boot, etc.  All this was machine-independent.

If you look at the versions I used, you will notice absence of &#8220;ubuntu-6.06-alternate-sparc.iso&#8221; and &#8220;kubuntu-6.06-alternate-sparc.iso&#8221;.  I just could not find them anywhere, and am beginning to think that Sparc ports do not exist for 6.06.  I would appreciate if anybody could confirm or deny this, btw.

So, it seems that running 6.06.1-server-sparc is the way to go, although it rubs me the wrong way a little, since I would like to have my VMware server host OS to be as lean as possible, and server implementation is not lean&#8230;

**There are two questions that bug me:**

1.  Why are the desktops stable on 6.06 and not on 7.04?  Is this because of the different server versions, or is this because of the different desktop versions?

2.  Is it possible to install a 7.04 specific desktop on 6.06 server and vice-versa, 6.06 desktop on 7.04 server, and if yes, how would one go about it?

Any comments are welcomed and appreciated.

-mm-

---

### Post by netztier on 2007-08-28
> **marmaj said:**
> This exercise is a proof-of-concept for running Linux on Sparc hardware (host) with VMware Workstation and various Windows flavors as guests.


Ehm.. VMware on Sparc? With Windows as VM guests? This is going to be interesting to watch ... 

*pulls up an armchair* 
*grabs some beer*  Wanna see this! 

I for one haven't heard of any version of Vmware running on a SPARC - do you? As far as I know, all VMware Products are for x86 or amd64 architectures.

best regards

Marc

---

### Post by marmaj on 2007-08-28
> **netztier said:**
>  

I for one haven't heard of any version of Vmware running on a SPARC - do you? As far as I know, all VMware Products are for x86 or amd64 architectures.

*pulls up an armchair*
*grabs some beer* Wanna see this!

Marc

:popcorn: <- make sure you have one of these...lol

Well, actually it looks possible on paper.  Windows run on VMware.  VMware runs on Linux.  Linux (Ubuntu) runs on Sparc, therefore Windows and VMware should run on Sparc.  Is there a hole in this logic that you see?

I will keep you posted of the outcome.  I just ran into a few days of free time which I intend to devote largely to the project, so updates should be rolling in shortly.

Say, you don't have anything to contribute in a way of answers to the two questions which I labeled in **bold** above, by a chance, do you?

Wish me luck...

Best regards!

-mm-

---

### Post by mips on 2007-08-28
> **netztier said:**
> Ehm.. VMware on Sparc? With Windows as VM guests? This is going to be interesting to watch ... 

*pulls up an armchair* 
*grabs some beer*  Wanna see this! 

I for one haven't heard of any version of Vmware running on a SPARC - do you? As far as I know, all VMware Products are for x86 or amd64 architectures.

best regards

Marc

you forgot the popcorn :)

---

### Post by netztier on 2007-08-28
> **marmaj said:**
> 
Well, actually it looks possible on paper.  Windows run on VMware.  VMware runs on Linux.  Linux (Ubuntu) runs on Sparc, therefore Windows and VMware should run on Sparc.  Is there a hole in this logic that you see?


Yes. The flaw in the logic comes in the form of non-availability of a "VMware virtualiser" (be that VMware ESX, VMware Workstation and whatever they're called) for SPARC. To the best of my knowledge, these are not open source, so chances you can find the source to compile it yourself are thin. If you happen to find one, et us know and I'll stand corrected.

And then, VMware's products don't emulate CPUs, so your Guest OS has to be architecture-specific. This is why you need Solaris in it's x86 flavour if you want it to run in VMware on x86 or amd64. Plus, I don't think that a SPARC version can be found in a brightly coloured box at your favourite computer shop.


> **marmaj said:**
> 
1. Why are the desktops stable on 6.06 and not on 7.04? Is this because of the different server versions, or is this because of the different desktop versions?

2. Is it possible to install a 7.04 specific desktop on 6.06 server and vice-versa, 6.06 desktop on 7.04 server, and if yes, how would one go about it?



As for the *first* question - kernels and X.org versions don't evolve in perfect parallelism - and some of the desktop instability on SPARC came from X.org changing over time, and not all bugs having been fixed in time upstream. Same goes for HAL & dbus which is one of the foundations GNOME depends on (at least on ubuntu) - Break it and you break your desktop - just as I experienced it with anything younger than 6.06 and a desktop.


The *latter* might be possible, by specifying that you want the ubuntu-desktop package from another repository/version than the rest of the system. However - it might just not be too clever, what with struggling over cross-dependencies of kernel versions, X.org versions and GNOME/Metacity versions.

Can't tell you exactly how, but with some plunging into the documentation of the **apt** system, **aptitude**, **dpkg** and the likes, about using alternative repositories and how to select specific versions of certain packages, you might end up with the ubuntu-desktop package (containing quite a few hundred packages actually) from 6.06 LTS on a 7.04-based installation. Somehow I think that this might work just better that the other way round.

best regards

Marc

---

### Post by stmiller on 2007-09-03
There are source tarballs of Virtualbox available. [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

I have no idea if it would work. But I *think* Virtualbox is based on qemu code, so could be a good option on Sparc.

---

### Post by Afishionado on 2007-09-03
> **marmaj said:**
> :popcorn: <- make sure you have one of these...lol

Well, actually it looks possible on paper.  Windows run on VMware.  VMware runs on Linux.  Linux (Ubuntu) runs on Sparc, therefore Windows and VMware should run on Sparc.  Is there a hole in this logic that you see?


VMware runs on Linux **on x86**, and only x86. From the VMware FAQ:
[http://www.vmware.com/products/ws/faqs.html](http://www.vmware.com/products/ws/faqs.html)
"VMware Workstation does not run on RISC architectures, including SPARC or PowerPC."

(Similar story for a lot of closed-source Linux programs; Flash only works on x86 processors, for example.)

Look into Qemu or something similar.

---

### Post by Emerald Wolf on 2007-09-06
> **Afishionado said:**
> VMware runs on Linux **on x86**, and only x86. From the VMware FAQ:
[http://www.vmware.com/products/ws/faqs.html](http://www.vmware.com/products/ws/faqs.html)
"VMware Workstation does not run on RISC architectures, including SPARC or PowerPC."

(Similar story for a lot of closed-source Linux programs; Flash only works on x86 processors, for example.)

Look into Qemu or something similar.

Ummm...not to pick nits, but if Flash only works on x86 why can I watch YouTube on my Ultra 5 (running Solaris 10)? (I'm not being jerky, just curious now...)

Catchya on the Flip Side.....

Emerald Wolf -- IIRC Shockwave is kinda fussy....

---

### Post by mips on 2007-09-06
> **Emerald Wolf said:**
> Ummm...not to pick nits, but if Flash only works on x86 why can I watch YouTube on my Ultra 5 (running Solaris 10)? (I'm not being jerky, just curious now...)

Catchya on the Flip Side.....


I think Afishionado is mistaken that flash only works on x86.

Adobe actually has flash support for Solaris **x86 **& **SPARC**.

[http://www.adobe.com/shockwave/download/alternates/](http://www.adobe.com/shockwave/download/alternates/)
[http://www.adobe.com/products/flashplayer/productinfo/systemreqs/](http://www.adobe.com/products/flashplayer/productinfo/systemreqs/)

---

### Post by marmaj on 2007-09-14
> **netztier said:**
> Yes. The flaw in the logic comes in the form of non-availability of a "VMware virtualiser" (be that VMware ESX, VMware Workstation and whatever they're called) for SPARC. To the best of my knowledge, these are not open source, so chances you can find the source to compile it yourself are thin. If you happen to find one, et us know and I'll stand corrected.

And then, VMware's products don't emulate CPUs, so your Guest OS has to be architecture-specific. This is why you need Solaris in it's x86 flavour if you want it to run in VMware on x86 or amd64. Plus, I don't think that a SPARC version can be found in a brightly coloured box at your favourite computer shop.


You, Sire, are absolutely correct.  I have tried it, failed miserably and went back to my corner rug with my tail tucked under.

Oh, well, it was a good idea, until I tried it but I have run into: ](*,)

I have a very soft spot for UltraSparc servers, I think that the hardware architecture and engineering is superb.  The only problem is, you can't do much with them these days if you want to use them as a workstation.  I am holding my hopes for the Open Solaris project.  Maybe this will breathe some new life into this platform.  Sure would be nice...

netztier, thank you for your time and your expertise - I have learned something new!

-mm-

---

