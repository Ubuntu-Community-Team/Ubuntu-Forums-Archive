---
title: "how to install &quot;DirectX&quot; in win xp on Vbox"
date: 2008-11-08
forum: Virtualisation
---

### Post by medya on 2008-11-08
I have succefully installed windows xp as guest on my ubuntu by Virtual Box 2 .

I installed my nokia driver , but when I run Nokia Lifeblog
it says 

> Lifeblog is unable to initialise because of a DirectX error. Make sure you have installed the latest version of DirectX, and the latest drivers for your graphics card. If this does not solve the problem, Lifeblog will not run with your current graphics card.

I installed DirectX 10 , but it doesnt work .

what should I do ?

---

### Post by FrostyFlames on 2008-11-08
1) DirectX 10 can not be installed on Windows XP, the latest is DirectX 9.0c
2) Latest DX 9 can be downloaded from here: [http://www.microsoft.com/downloads/details.aspx?FamilyID=886acb56-c91a-4a8e-8bb8-9f20f1244a8e&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=886acb56-c91a-4a8e-8bb8-9f20f1244a8e&DisplayLang=en)
3) Install the guest additions.

---

### Post by stinger30au on 2008-11-08
if you install service pack 3 on xp it wil give you all you need anyways


remember, xp in virtual box will give you direct draw, but *NOT* direct 3d

---

### Post by medya on 2008-11-08
when I install directx 9 it pretends it gets installed (in 2 seconds which is impossible) but when I run nokia lifeblog it gives me the msg which I qouted above.

---

### Post by Pom2122 on 2008-11-08
From a moderator on the virtualbox forums:
> VB does not support DirectX capabilities. Even though DX is installed and it says some funtions/features are available, they aren't supported by the VB graphics card. It does not have 3D options, so anything that you try with DirectX won't work.

---

### Post by medya on 2008-11-08
so should I install another virtual machine software ? 
VMware or something ?

---

### Post by HotShotDJ on 2008-11-08
> **medya said:**
> so should I install another virtual machine software ? 
VMware or something ?3D, for reasons that I don't pretend to understand, is very difficult in a virtualized environment. VMWare has experimental support for Direct3D -- but beware, the operative word there is experimental:
[QUOTE="http://www.vmware.com/support/ws55/doc/ws_vidsound_d3d.html"]Caution: Features with experimental support are not intended to be enabled on production systems. Enabling 3-D acceleration may cause the host or guest to crash, causing you to lose data, even if 3-D applications are not active.[/QUOTE]

---

### Post by Shaythong on 2008-11-08
> **HotShotDJ said:**
> 3D, for reasons that I don't pretend to understand, is very difficult in a virtualized environment. VMWare has experimental support for Direct3D -- but beware, the operative word there is experimental:

VMWare Workstation 6.5 has non-experimental DirectX but is still very buggy and not fully working yet.

---

### Post by Vadi on 2008-11-09
I'll second the very buggy and non-functioning part given my experience. It's a dualboot for that unfortunately.

---

### Post by medya on 2008-11-09
can I migiriate from vbox to VMWare Workstation 6.5 ?

---

### Post by HotShotDJ on 2008-11-09
> **medya said:**
> can I migiriate from vbox to VMWare Workstation 6.5 ?I did a quick google search for you ( [http://www.google.com/search?q=migrate+virtualbox+machine+to+VMWare](http://www.google.com/search?q=migrate+virtualbox+machine+to+VMWare) ) and found this: [http://dossy.org/2008/05/migrating-from-virtualbox-to-vmware](http://dossy.org/2008/05/migrating-from-virtualbox-to-vmware)

I've never tried it myself, but hopefully that will get you off to a good start.  As far as Direct3D -- I only recommend that you do this if you have a high tolerance for breakage.  As several other people have mentioned, the DirectX implementation in VMWare is still very buggy.  Use at your own risk.

---

### Post by medya on 2008-11-19
VMware really sucks,
it is so slow, it is buggy, it is ugly , it is so memory/cpu/disk consuming .
it is not Free , and my windows stopped working on it , (it wont start after 2-3 restart) -I reinstalled windows many times and the same thing happend-


I hate VMware , Vbox is great , their only problem is not having a DirectX support in vbox I hope they solve it soon so I kick that vmware *** forver :(

---

### Post by darco on 2008-11-19
> **medya said:**
> VMware really sucks,
it is so slow, it is buggy, it is ugly , it is so memory/cpu/disk consuming .
it is not Free , and my windows stopped working on it , (it wont start after 2-3 restart) -I reinstalled windows many times and the same thing happend-


I hate VMware , Vbox is great , their only problem is not having a DirectX support in vbox I hope they solve it soon so I kick that vmware *** forver :(

6.5 Works perfect for me...I am running Vista SP2, Win7 and Xp Pro w/o any issues at all. Unity is awesome, VMware tools works, full screen is easy as pie,Bridge or NAT, USB2 no prob. 
Great app

darco

---

