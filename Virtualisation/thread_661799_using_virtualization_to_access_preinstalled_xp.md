---
title: "using virtualization to access preinstalled xp"
date: 2008-01-08
forum: Virtualisation
---

### Post by Bannor on 2008-01-08
ok Total newb quesitons. 

can virtual box launch my current windows xp from linux?

if not can I install xp in virtual box and then launch the programs that are already installed from that windows?

for doing  either of these things which virtualization program should I use. 

is virtualization too complicated for someone dumb enough to ask the preceding questions?

---

### Post by lvleph on 2008-01-08
Virtual Machine can run your native xp, but there are issues with it such as:
different hardware profiles
activation issues
If you don't have xp pro I wouldn't suggest bothering. Because you won't be able to address the activation issue. After activating windows 10 times you have to call in, it takes 10 minutes for each call. If you have pro a script can be written that will switch activation. Look on the web for instructions.

---

### Post by Bannor on 2008-01-08
if I have an extra windows key lying could I install a new xp and run software from my old xp ?

---

### Post by popch on 2008-01-08
> **Bannor said:**
> can virtual box launch my current windows xp from linux?

Yes, it can, with some restrictions. The restrictions come from the fact that VirtualBox (or any other virtualisation program) simulates a given chip set for your XP, and the XP in your partition is tailored to the chip set of your real hardware pc.

The product called VirtualBox has a fine HowTo on its web site which explains step by step how to to exactly that which you ask. [http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

The 'other' product (VMWare) has a program and presumably also a HowTo on that topic, but I don't have a link as I don't use VMWare anymore.

There's also a tutorial in this subforum which should be applicable although the title's thread names Windows 98 instead of XP: [http://ubuntuforums.org/showthread.php?t=660511](http://ubuntuforums.org/showthread.php?t=660511)

> **Bannor said:**
> if not can I install xp in virtual box and then launch the programs that are already installed from that windows?

No, that will not work for the same reason that you can not move installed programs to another partition and still execute them in Windows. The culprit is the Registry, mainly, plus some coding errors in most programs.

> **Bannor said:**
> for doing  either of these things which virtualization program should I use. 

I found VirtualBox quite adequate and easier to install in Gutsy. Before that, I used VMWare Workstation (even paid money for it). 

The two free products by VMWare (VMWare server and VMWare Player) have good reputations, although there seems to be an installation issue with the Player, at the moment.

I also stopped using VMWare products because the setup procedure required you to download and 'maintain' the Kernel headers, a  C compiler and whatnot. I do not know if that's still true, and if it is, it's not all that complicated to do. I just found it slightly more cumbersome than just adding VirtualBox from the Repos.

> **Bannor said:**
> is virtualization too complicated for someone dumb enough to ask the preceding questions?

Stop fishing.

And no, it isn't, if you can follow instructions and RTFM.

---

### Post by lvleph on 2008-01-08
VirtualBox is, IMO, much nicer that VMWare, so if you can boot native with VB do it.

---

### Post by Bannor on 2008-01-09
well thanks for the help all.  after posting my question I notice that one of the stickies address specifically what I was looking to do.  Thank you moderators for recognising the post and making it a sticky.  Because the sticky was for vmware that is what I chose to use for my software (also the potential for 3d support). These instructions were much better than the the first set 

[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/](http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/)

---

### Post by Bannor on 2008-01-09
oh there is one thing that needed to be addressed.  

if you have 2 physicall disks, one windows, one linux you need to follow the instructions then go to your virtual machine and add the other disk.  It's pretty simple

if grub doesn't load properly this might be the problem you are running into.  if you need further instructions let me know

---

