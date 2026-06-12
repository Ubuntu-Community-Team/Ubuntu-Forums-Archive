---
title: "Keyboard problem with Ubuntu Server 10.10 on Vmware 7.1.1 build-282343"
date: 2010-10-11
forum: Virtualisation
---

### Post by sarah22 on 2010-10-11
Arrow keys are not functioning properly. If I press down, it enters. The others are nothing. Numpad arrows are working perfectly.

Any idea how to fix this?

---

### Post by sarah22 on 2010-10-11
oh I found out that 10.04 server has this problem also. Now, anyone has a fix for this?

---

### Post by misterdai on 2010-11-07
Did you ever have any luck with this.  I'm having the same problem with Ubuntu Server 10.10 as a guest OS on Windows 7 using VMWare player.  My arrow keys are useless, which makes text editing or selecting options in a menu impossible :(

---

### Post by gen0 on 2010-11-08
I'm getting this too - Ubuntu 10.04 Server and VmWare Workstation 7.1.2 :(

---

### Post by gjdunga on 2010-12-26
Well, I think it's because the keyboard is set incorrectly.. 

This is what i did to switch 

sudo dpkg-reconfigure console-setup

Now while you do this, you have to be creative, because well the up and down arrows don't work..  I pressed the letter A then A again, untill i got to the apic standard I think it was called, and then tabbed over to ok, and chose usa and latin for the other things, and rebooted.. Viola I got my server back!  

Hope this helps.. 

Gabriel

---

### Post by misterdai on 2010-12-31
Hi all,

I found the perfect fix for this issue.  Don't let VMWare Player (or other VMWare product) do the fast install for you.  When I went through the installation manually, the keyboard worked correctly.

Hopefully they'll fix this in future versions ;)

---

