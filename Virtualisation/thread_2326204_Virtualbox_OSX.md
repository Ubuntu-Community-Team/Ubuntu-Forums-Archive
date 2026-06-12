---
title: "Virtualbox OSX"
date: 2016-05-29
forum: Virtualisation
---

### Post by andrew80 on 2016-05-29
Hi all,


Been using Linux since around 2000, Been using Ubuntu for about 3 years, I have a Virtualbox install set up with Windows XP and Windows 10 running on it for some car software I have, I have an Apple Airport Extreme also which I have to access using Windows as they only make the program for Windows and OSX.

Was playing around today and thought why don't I install, OSX as a virtual machine, Anybody got a virtual OSX running in Virtualbox?

I'm not an advanced user but know the basics.

Andrew

---

### Post by deadflowr on 2016-05-29
To note: it is illegal to virtualize OSX on any hardware except Macs.
Are you using a Mac?

---

### Post by QIII on 2016-05-29
Actually...

Even virtualizing on a Mac may violate the EULA. The "hardware" provided by VirtualBox' hardware abstraction layer is not Apple, and that matters.

---

### Post by T.J. on 2016-05-29
Not only is running OSX in a VM questionable legally as far as the EULA goes, actually doing it requires several "hacks" to the OS which can be considered illegal, depending on your jurisdiction.  OSX uses DRM to identify if it is actually running on Apple hardware.  Bypassing that can be considered a felony, even if you own a Mac.


Setting that aside, once you virtualize it, it is my understanding that you can no longer get updates from Apple servers - again because they check to see if you are genuine, and because their models all use specific hardware and drivers.  Their boards and other parts are not interchangeable as a PC is where the industry gives you a generic driver.  Some replacement parts like drives are a "no brainer" but the internal cards use specific drivers.

Pretty much everything Apple does is locked down with multiple forms of hardware or software measures, designed specifically so that Apple and only Apple has control of it.  One of my friends uses Macs, and we had to argue on the phone with tech support just to get the root password (which Apple kept) for his personal computer in order to reset his user password. This happened* after *he proved who he was.  Apple is run by a bunch of control freaks, and is *that* far gone. No, I am *not *joking or exaggerating.

If you want Mac software, you are far better off buying a Mac and then dual booting Linux with OS X.  Virtualizing it causes too many problems to solve - which can be a good thing if you LIKE solving problems.


This is my opinion, but VirtualBox itself is a substandard hypervisor solution, promoted by the copyright/patent troll, Oracle. I believe it should be dropped from Debian and Ubuntu entirely. It would in the best interests of all users, not just my admitted dislike of Oracle. It has poor drivers, which cause crashes. Xvideo and other extensions have never worked right on guests. Even the Linux kernel developers have labeled it as "tainted crap." (Their words, not mine.) Oracle withholds certain support from the FOSS version, such as newer USB devices or RDP, unless you agree to their license. 

If Ubuntu did drop VirtualBox, the time saved used to improve Virt-manager/KVM, which is a far superior solution - both technologically and legally.

---

### Post by andrew80 on 2016-05-29
That I didn't know... suppose that is end of thread then.

---

### Post by T.J. on 2016-05-29
> **andrew80 said:**
> That I didn't know... suppose that is end of thread then.

After consideration, I decided to investigate the current state of affairs and ended up with a bit of embarrassment.  My information is clearly out of date, although I can at least be forgiven for some of it, such as: [https://tech.slashdot.org/story/05/08/01/0421248/mac-os-x-intel-kernel-uses-drm](https://tech.slashdot.org/story/05/08/01/0421248/mac-os-x-intel-kernel-uses-drm). I don't excuse myself for not double-checking everything before making comment.

At one time, a hack was possibly required to install. Without those hacks, installing is *possibly* just a EULA issue and not a felony. To my knowledge, although even if VirtualBox supports it, Apple still does not sanction it.   

I should have been clearer and if you or anyone else feels I was misleading, I apologize profusely. I should have put a broad disclaimer on it, explaining it was probably dated. In the future, I will be more careful in my comments. As always when asking for advice, one should compare that with your own research to see what is current.

---

### Post by houstonbofh on 2016-05-30
Note that is is legal, and fully supported to run OSX on VMware. (On apple servers)  There are actually several businesses doing that, fully legally.  I do not know if the free version of VMware supports this (yet) nor do I know if it does some kind of checking of the hardware underneath to confirm if it is Apple.

---

### Post by MAFoElffen on 2016-06-01
Yes, been years of OSX threads on the VirtualBox forums. 

Not trying to knock VirtualBox on OSX-- But on Mac, seems the students I tudored (who had Mac's), seemed to prefer, and truely raved about "Parallels."  Just saying...

---

