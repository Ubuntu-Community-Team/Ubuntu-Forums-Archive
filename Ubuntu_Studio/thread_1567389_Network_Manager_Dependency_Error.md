---
title: "Network Manager Dependency Error"
date: 2010-09-03
forum: Ubuntu Studio
---

### Post by ruintc on 2010-09-03
I've read some previous threads regarding internet access and tried to install the network-manager-applet from the Ubuntu Image CD-ROM as suggested. 

However, the following error message came up immediately: 

"Error: Dependency is not satisfiable: libnm-glib2 (>= 0.8~rc2~git.20091229t135236.302e62d)"

I've just installed a new copy of Ubuntu Studio 10.04 and my knowledge of linux is very scarse so any help would be much appreciated.

---

### Post by Fadisker on 2010-09-04
Hi ruintc,
 I am certainly no expert, somewhat new to linux and ubuntu myself. But my take on that error message is that the library in question is newer than the one supported by the network manager applet from the install CD. Maybe if you try to install the applet from the ubuntu repository it may be an updated version that uses the library that you currently have installed.
 
 As stated above I am pretty new to this so take this as such.

---

### Post by cchhrriiss121212 on 2010-09-04
The message is saying this: In order for you to install network manager you need the package libnm-glib2 upgraded first.

This package should also be on the studio image, so just search for and install it along with any others that you are informed of by the deb installer. 

Fadisker has a good point though, this will be all done for you if you download it from the repos using synaptic, but that it assuming you have a wired connection handy.

---

### Post by ruintc on 2010-09-04
Hi Fadisker and cchhrriiss121212,

Thank you very much for your replies.

I don't have a wired connection. Only the broadband through Windows and I had to go back and forwards from one Operating System to the other.

I solved one problem by installing the network-manager files from the CD-ROM
(pool/main/network-manager). However when trying to install the network-manager-applet packages another error stopped me from installing the program: mobile-broadband-provider-info (>=20090622).

It seamed that it was getting more and more complicated just to get the applet working. After looking up on all the forums and ubuntu studio documentation couldn't find a solution for this. The documentation assumes that Network Manager is installed when everyone in this forum knows it isn't.

So I just look for the best "working" distro out there, found Linux Mint and installed Windows and Linux Mint again.

I just had to type the Broadband Service Provider's name (internet.vodafone.pt) and the pin number. It worked just fine. Of course life's not that simple and the Huawei stopped working with Windows. After some plugging and unplugging, rebooting both systems, etc. it's all working alright.

Anyway, I loved Ubunto Studio (worked with Open Suse before, with no luck with the broadband connection either) but for beginners who want internet access, Linux Mint is apparently an excellent choice

---

