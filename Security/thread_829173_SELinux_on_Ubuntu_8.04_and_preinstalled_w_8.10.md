---
title: "SELinux on Ubuntu 8.04 and preinstalled w/ 8.10?"
date: 2008-06-14
forum: Security
---

### Post by iheartubuntu on 2008-06-14
On another forum Im in people are concerned about government back doors like how the NSA is tapped into MS Vista systems. Security is a big reason why many people head over to linux.

I can now see Hardy Heron has SELinux in the synaptic manager (not installed), but word is that in the next release, 8.10 (Intrepid Ibex), Ubuntu has SELinux built into the OS and makes it impossible to uninstall.

Can anyone please comment on this? This would be a real disappointment if Ubuntu caved into the wishes of any government.

[https://wiki.ubuntu.com/SELinux](https://wiki.ubuntu.com/SELinux)

[https://wiki.ubuntu.com/HardySELinux](https://wiki.ubuntu.com/HardySELinux)

---

### Post by prshah on 2008-06-14
> **shirteesdotnet said:**
> 

I can now see Hardy Heron has SELinux in the synaptic manager (not installed), but word is that in the next release, 8.10 (Intrepid Ibex), Ubuntu has SELinux built into the OS and makes it impossible to uninstall.

Can anyone please comment on this? This would be a real disappointment if Ubuntu caved into the wishes of any government.



From what I understand, SELinux is a replacement for AppArmour, and can easily be disabled and replaced with AppArmour by uninstalling.

It's for a more fine-grained control over devices and permissions; how do backdoor concerns come in here?

---

### Post by LeoSolaris on 2008-06-14
While I love a great conspiracy as much as the next guy, and yes the NSA did help build SELinux, It is open source. If the US government built a hidden back door into SELinux, it would eventually be discovered. There are too many extremely paranoid computer programmers (usually called hackers but they should be called crackers) (if you don't know, look it up) out there who scan source code, and check it's security. The NSA built it for it's own use, then released it back to the community. 

In the end, if you do not trust it, don't use it. Stay with the long term release till you find a replacement for Ubuntu. BSD has some top notch security, it's harder to break into than Linux from what I have heard.

Leo

---

### Post by iheartubuntu on 2008-06-14
Well what do I know! Im not a hacker, cracker, etc Im trying to learn all this security stuff!

---

### Post by tubbygweilo on 2008-06-15
Following on from Leo's thoughts;
DHS spend time and money hunting down suspect code in open source projects.
> Open source code, much like its commercial counterpart, tends to contain one security exposure for every 1,000 lines of code, according to a program launched by the Department of Homeland Security to review and tighten up open source code's security.

Popular open source projects, such as Samba, the PHP, Perl, and Tcl dynamic languages used to bind together elements of Web sites, and Amanda, the popular open source backup and recovery software running on half a million servers, were all found to have dozens or hundreds of security exposures and quality defects. 
[Coverity]("http://www.informationweek.com/news/security/showArticle.jhtml?articleID=205600229") Helping I hope so, installing back doors? I think not.

---

### Post by Chayak on 2008-06-15
Ah paranoia... Security is a process.  Total security is a fantasy.  They don't need to put in backdoors to get into your system.  I'm pretty sure any organization that has the best and brightest people that you'll never know about can find security holes in just about anything.

What you do when you harden your system is reduce the number of people capable of cracking it.  There will always be someone out there who is capable of enumerating your system, finding what's there and then discovering an exploit and writing code to take advantage of it.

The exploit can be anything from a malformed packet, a heap spray, or a classic buffer overflow where they establish a connection and send a string of characters to fill up the buffer and then send something along the lines of \xeb\x03\x59\xeb\x05\xe8\xf8\xff\xff\xff\x4f\x49\x49\x49\x49\x49 which is known as shellcode and translates directly into processor opcodes (ie assembly language) these lines get pushed into the stack and an instruction sent to move the execution point into the area of memory before the shellcode normally into what's called a 'nop sled' which doesn't do anything (it stands for 'no operation') but after it gets past the nops then the shellcode will begin executing.  What it does is up to the person who programmed it.

There are people who get into *banks* and they spend a lot of money on security.

All gloom and doom?  Not exactly...  To your benefit is that the people capable of getting into your system normally work for the government, or are security researchers.  They have bigger fish to fry or are on the clock to make money.  Those on the dark side capable of it honestly don't care about your piddly system.  They want big companies and big money.

The lesson to take out of this is to reasonably harden your system with a firewall and be smart with what you download and execute.

If you want to be very secure (for a home user) then what you need to do is install something like VMware and create a virtual machine with a shapshot to surf the web and do things online in.  After your done revert to the snapshot and everything is clean.  Use your physical host for things you need to keep.  It's easy enough to download in a VM and then drag it over to your actual machine.  AntiVirus is a scam as most of the new stuff isn't picked up so just make sure you download from trusted sites or examine the source code.

---

### Post by iheartubuntu on 2008-06-16
Well, one thing I was concerned about regarding security (and Id consider myself an average computer user, but doing some photoshop and html too) was how simple it is to crack XP's logon password. I saw some video on the web how people burned a livecd to bypass the XP logon. Nifty stuff, yet I read a few weeks ago in the forums here (dont remember where) how people can just do a few lines in the terminal to bypass a linux password.

I have people I work with I dont trust and for all I know they have keyloggers on all the other computers in the business. I wouldnt put it passed them. No that I have linux I feel secure again, but once they get into linux themselves and start messing around, or just doing some random searches on google... they are going to (sooner or later) find how how to type a few things in the terminal and once again they can get back into my system.

What can I do?

---

### Post by tubbygweilo on 2008-06-16
You could try a boot password placed the Bios in conjunction with turning off you machine when you leave your desk. These ideas may well help to protect you kit from physical access by those who may well wish to cause you grief. It may help to stop people trying to access your system via an Ubuntu LiveCD or indeed any other LiveCD.

---

### Post by Nepherte on 2008-06-16
When someone has physical access to your computer, linux isn't secure either. By default, you can boot into recovery mode which leaves you with root access without needing a password. Recovering a password isn't hard either with a live cd.

---

### Post by Frak on 2008-06-16
> **Nepherte said:**
> Recovering a password isn't hard either with a live cd.

1D41C853AF58D3A7AE54990CE29417D8

There's the hash.

---

### Post by Chayak on 2008-06-16
> **shirteesdotnet said:**
> Well, one thing I was concerned about regarding security (and Id consider myself an average computer user, but doing some photoshop and html too) was how simple it is to crack XP's logon password. I saw some video on the web how people burned a livecd to bypass the XP logon. Nifty stuff, yet I read a few weeks ago in the forums here (dont remember where) how people can just do a few lines in the terminal to bypass a linux password.

I have people I work with I dont trust and for all I know they have keyloggers on all the other computers in the business. I wouldnt put it passed them. No that I have linux I feel secure again, but once they get into linux themselves and start messing around, or just doing some random searches on google... they are going to (sooner or later) find how how to type a few things in the terminal and once again they can get back into my system.

What can I do?

Use the alt install CD stick a blank usb flash drive in and install an encrypted partition onto the hard drive and put the /boot onto the usb flash drive.  This assuming the computer you're installing on will boot from usb.  Use a strong passphrase and check the computer for hardware keyloggers before you boot it and you should be decently safe

I have the same type of setup on my laptop.  I of course have backups of the usb boot stick.

---

### Post by darthchaosofrspw on 2008-09-25
> **shirteesdotnet said:**
> On another forum Im in people are concerned about government back doors like how the NSA is tapped into MS Vista systems. Security is a big reason why many people head over to linux.

Would this forum by any chance be the Prison Planet Forum? :D

---

### Post by redgsturbo on 2008-09-25
VMWare isn't that secure.  Xen is more secure... vmware completely bypasses the kernel network hooks and thus can't be controlled with iptables/etc.. (so I'm told, I've never personally verified this).

Default openbsd is more secure than ubuntu desktop, but then default openbsd isn't remotely as usable as ubuntu desktop... fully hardened linux or bsd are for all purposes equal in security.  add a graphical desktop on top of either and you forfeit *some* security, but still not the swiss cheese that MS products or MacOSX is

Secondly, the majority of security problems don't stem from mad ninja-skilled stack or heap exploits, or code injection at all... they come from social engineering and people putting their too often required to be changed and too complex to remember passwords on their desks, not following security policies, etc.  The better solution is to use smartcards or tokens and not allow access at all without them.  encrypt home directories independently based on these keys and data at rest is protected.  use randomized address spaces, stack canary's, SELinux for segregation, etc etc, and data in execution is protected.  Use encrypted email, ssl/tls, ipsec, etc and data in transit is protected.  Keep everything open source so it is independently verifiably secure (even if you don't know how to verify security, just the fact that its open to the worlds scrutiny is reasonably convincing that it has been reviewed). thats about the best you can do right now.

---

### Post by zdux0012 on 2008-10-25
I will move to another distro because of SE-Linux. Will encourage friends and family to do the same. 
Ubuntu you've done a great job getting people to move over to linux. However this is where it ends.

You can call me a "conspiracy theorist" if it makes your world view a little easier to digest.

---

### Post by cariboo on 2008-10-26
So are you moving to another distribution because of a rumour that SELinux will be installed by default in the next release of Ubuntu, or you moving away because Apparmor will be the default security solution for the forseeable future?. 

One other thing to think about is this:

> Founded in late 2004, Canonical Ltd is a company headquartered in Europe with over 200 employees working in 23 countries (and counting). Canonical is the commercial sponsor of Ubuntu project.

The above is one of the best reasons to stay with Ubuntu. It is not based in the US.

Jim

---

### Post by zdux0012 on 2008-11-18
You could just answer the question.

---

### Post by damatta on 2008-11-18
Same concern here. Before people start bashing me, I'm not saying it does contain backdoors or something similar.
There are many other "courtesies" from the NSA to the linux world but this one really got me thinking...

---

### Post by bodhi.zazen on 2008-11-18
> **zdux0012 said:**
> You could just answer the question.

As far as I know, there are no plans to change from apparmour to selinux in Ubuntu.

With your level of concern (dare I say paranoia) there is only 1 solution, LFS.

---

