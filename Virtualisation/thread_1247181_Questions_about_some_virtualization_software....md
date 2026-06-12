---
title: "Questions about some virtualization software..."
date: 2009-08-22
forum: Virtualisation
---

### Post by Cadeyrn on 2009-08-22
I'm looking to remove my Windows XP partition and run my Windows games through virtualization, and it looks like I have a few options, all of them hard (if possible).

My first question is about VirtualBox: With the newest version, there is now 3D hardware acceleration support and pixel shading 1.3 and vertex shading 1.1, and DirectX 9 support, right? Well, I'm wondering if it's possible to mod the program to allow more than 128MB of video RAM and mod the guest additions to let the guest OS access my video card's 2.0 shading.

Another option would be this virtualization program I heard about from searching through Google and Wikipedia, called the RTS Real-Time Hypervisor. Apparently, this product can access my hardware directly instead of through guest additions, and works fine doing so. This would be perfect for games. But I've searched all over their website and Google, and while they talk about all the features their product offers and have the news history of when they added what to their product, there are zero links to get it. I don't even know whether it's free because they seem to have no interest in people having this product. They just want to rub it in your face that they achieved something you want, but they won't let you have it.

Finally, I heard about VMWare Workstation and VMWare Fusion. Workstation is great, but it's no better than VirtualBox with games, however Fusion supports 2.0 shading, exactly what I need. Sadly, it's only for mac. Is there some Linux version I can find anywhere, and if not, is there a tarball of Fusion so I can get it into Linux?

---

### Post by Choose on 2009-08-22
These link's might help you out

[VMWare Workstation]("http://www.vmware.com/download/ws/open_source.html") & [VMware Fusion]("http://www.vmware.com/download/fusion/open_source.html")

---

### Post by Cadeyrn on 2009-08-23
Thanks, I'll see what I can do with this tarball.

Meanwhile, more help is appreciated.

EDIT: Hmm... the tarball for VMWare Fusion seems to be made for Linux, or for any UNIX-based system. The build.sh file installed something just fine, but I'm not entirely sure if it installed VMWare, and if so, I don't know where.

---

### Post by HermanAB on 2009-08-24
If you want to play fast moving games, then you need to run the game natively in order to eek out all available speed.  A few Windows games run fine on WINE (All Steam games run on WINE).  I won't bother trying to run games on a VM though - it is very likely to be disappointing.

---

### Post by Cadeyrn on 2009-08-24
I would be using WINE, except even though all the games I want to play are silver to platinum, none of them work on my computer after the needed tweaks. I don't want to go into it right now because it would take way too long to explain how damn much I looked into this problem and tried everything. WINE simply refuses to run games on this computer. I've even tried it on two differen installations of Linux.

---

### Post by HermanAB on 2009-08-25
Hmm, then it would be better to dual boot WinXP or Win2003 for the games.  Win2003 has better hardware support and better security than XP so I'd recommend Win2003 - if you can get your paws on a copy.

---

### Post by Cadeyrn on 2009-08-25
I thought Win2003 and Windows 2008 were both servers? Well, XP works fine, so I'm fine with it.

---

