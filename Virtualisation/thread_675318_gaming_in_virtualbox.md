---
title: "gaming in virtualbox"
date: 2008-01-22
forum: Virtualisation
---

### Post by billgoldberg on 2008-01-22
I installed xp in virtualbox and installed command and conquer 2 yuri's revenge on it.

It installed fine but when I play it it just gives me a black screen and does nothing. I gave xp 500mb ram memory. In wine it would atleast start before giving an error.

Anyone know why it doesn't work? (I tried al the compatibility settings).

Is it because i'm using virtualbox ose?

---

### Post by Dual Cortex on 2008-01-22
Gaming doesn't really work in virtual machines, as the video driver the virtual machine uses does not really support much 3D acceleration. You're better off playing through Wine, if the game is supported.
 
EDIT:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4242](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4242)
Actually, this game works fine under Wine.

---

### Post by billgoldberg on 2008-01-22
C&C RA2 YR is an old game with need for 3d (I think/hope).

In wine it would install but the game would then give an internal error.

---

### Post by billgoldberg on 2008-01-22
If anyone knows how to get it working in wine, tell me.

I can't install xp on the harddrive because it won't recognize my sata harddrive.

---

### Post by Frem on 2008-01-22
Try the instructions/advice given here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4242]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4242")

---

### Post by kellemes on 2008-01-22
> **billgoldberg said:**
> If anyone knows how to get it working in wine, tell me.

I can't install xp on the harddrive because it won't recognize my sata harddrive.


Seriously?

---

### Post by Dual Cortex on 2008-01-22
This was actually a common problem with old installation CDs. Common solution is copying the SATA drivers to a floppy disc, and providing the drivers while the XP setup is loading.

---

### Post by billgoldberg on 2008-01-24
> **Dual Cortex said:**
> Gaming doesn't really work in virtual machines, as the video driver the virtual machine uses does not really support much 3D acceleration. You're better off playing through Wine, if the game is supported.
 
EDIT:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4242](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4242)
Actually, this game works fine under Wine.

Thank, I visited that page before but for some reason I missed the "how-to" and was under the impression everything would work after I installed the game.

To someone else:
Old windows (mine is the first generation sp2) xp cd-roms don't support sata drives. Since I have no floppy drive I would have to slipstream xp. Like thats ever going to happen, haha.

---

### Post by theRightNee on 2008-01-24
Actually, if you are using Windows for more than just gaming, you may consider setting up 3D acceleration for VMWare. 
Note: this only works for VMware Player or VMware Workstation (VMWare Fusion as well, but I do not think you have that)

[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html)

you may not want to enable the vmmouse bit...I have run into an issue where the mouse does not show (makes life terribly difficult)

i recommend the following steps, to get the most out of your free virtualization =]
1. Install VMWare Server
2. Set up your Vitual XP, and install VMWare Tools (instructions are on VMWare's website)
3. Uninstall Server, then installk VMWare Player
4. edit the .vmx file as instructed (make sure the virtual machine is off)
5. Fire up the OS and see what happens =]

best of luck to you

---

