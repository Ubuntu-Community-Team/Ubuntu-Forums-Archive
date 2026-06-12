---
title: "[SOLVED] Clone existing XP vdi from Hardy"
date: 2008-11-01
forum: Virtualisation
---

### Post by jimbob on 2008-11-01
I just finished installing virtualbox-2.0 on Intrepid and am trying to clone an existing XP vdi from my Hardy system using vboxmanage clonevdi <input file> <output file> but it tells me I need to install virtualbox-ose.

When I try to do that it wants to remove virtualbox-2.0 that I just installed.  What's up with that?

I had done this before with no problem when moving from Gutsy to Hardy.

---

### Post by HotShotDJ on 2008-11-01
> **jimbob said:**
> I just finished installing virtualbox-2.0 on Intrepid and am trying to clone an existing XP vdi from my Hardy system using vboxmanage clonevdi <input file> <output file> but it tells me I need to install virtualbox-ose.I'm a bit confused.  You should be able to simply copy the vdi on your Hardy system to your new Intrepid system (place it in ~/.VirtualBox/VDI.  Then, open Virtualbox and click on "New" -- when you get to the Virtual Hard Disk dialog, click on the "Existing" button.  Select the *.vdi file and click open.

Even easier -- just copy the entire ~/.VirtualBox directory over. Virtualbox should "just work" that way.  I just upgraded my Hardy system to Intrepid and this is how I did it.  No muss, no fuss.

This should take care of it for you -- unless I'm completely misunderstanding your problem.

---

### Post by jimbob on 2008-11-02
This does not work for me for some reason (see attachments).

This is the problem I had when going from from Gutsy to Hardy which is why I had to use the clonevdi command that seems to no longer be available.

I think the problem may be with the UUID of the copied *vdi file but I don't know how to change it.

---

### Post by jimbob on 2008-11-02
OK, got everything (including USB) working.  Here is what I had to do.

1)  Since I did the copy from root, I had to go back into ~./VirtualBox and chown and chgrp -R to myself.

2)  Added myself to the vboxusers group.

3)  Added the following line in /etc/fstab - ( get the devgid from System>Admin>Users and Groups)
 
none            /proc/bus/usb   usbfs   devgid=125,devmode=664  0   0

---

