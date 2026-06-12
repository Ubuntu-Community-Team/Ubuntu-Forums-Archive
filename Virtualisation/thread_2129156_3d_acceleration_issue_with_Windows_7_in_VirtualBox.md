---
title: "3d acceleration issue with Windows 7 in VirtualBox and Kodu"
date: 2013-03-25
forum: Virtualisation
---

### Post by matthewetaft on 2013-03-25
[TABLE="width: 100%, align: left"]
[TR]
[TD="width: 100%"]Hi everyone,

I'm having some trouble getting accelerated 3d graphics to work in Windows7 in VirtualBox.  Hoping someone here has been through my situation before and can lead me in the right direction.  

I'm using Ubuntu 12.04 and am running Windows 7 Professional as a  virtual machine using VirtualBox 4.2.10 and I have VBoxGuestAdditions  4.2.10 installed.  My graphics driver is Intel HD Graphics 3000.  In case this matters for this situation, my machine is 64-bit.  

Here's my story:

Trying to teach my kids computer science, and they're really exciting about being able to create video games, so I thought I'd have them try Kodu.  When I boot into Windows, Kodu works fine, but I'd rather have my kids stay in Ubuntu and just use VirtualBox (with a licensed copy of Windows 7 Professional) for the few things they need from Windows, like some of their games.  However, when I start Kodu from inside the virtualized Windows 7 Professional, I get the following error:
[INDENT] No suitable graphics card found.
 Direct3D hardware acceleration is not available or has been disabled.

 [/INDENT]

When I enable 3d acceleration in VirtualBox, that error goes away and  Kodu opens without errors but doesn't display anything, just an empty  white window with a smaller black window in the top left corner.  I  heard the initial sounds that the program makes when you start, and when  I click in the window I can hear the app responding to what I am  clicking (by the sounds it makes), but nothing is displayed.

 This same machine also has a separate Windows 7 partition I can boot  into when I start up my machine, and when I try running Kodu from there I  have no issues.

I had the impression that 3D virtualization was done in software and should work with any graphic card that supports OpenGL, so I'm not sure why the *real* version of Windows would work and the *virtualized* version wouldn't unless my graphics card is having a compatibility issue with OpenGL or there's some other obscure virtualization problem...and I'm just not sure where to trouble-shoot from here.

Please let me know if you would like some additional info or log files or anything else, just not sure where to start and don't want to post things that aren't helpful for trouble-shooting.
[/TD]
[/TR]
[/TABLE]

---

### Post by mayagrafix on 2013-03-25
I'm also running Win7 virtually on a Dell 64bit PC but with a AMD Radeon GPU. When I look inside of Virtual WIn7 at the Control Panel>>Appearance>>Display>>Advanced Options, , it says using VirtualBox Graphics Adapter. I think ur problem is with on-board Intel HD Graphics 3000.

---

### Post by matthewetaft on 2013-03-25
> **mayagrafix said:**
> I'm also running Win7 virtually on a Dell 64bit PC but with a AMD Radeon GPU. When I look inside of Virtual WIn7 at the Control Panel>>Appearance>>Display>>Advanced Options, , it says using VirtualBox Graphics Adapter. I think ur problem is with on-board Intel HD Graphics 3000.

Thanks for the reply.  I'll try looking at that when I get home.  But it works when I boot into the Windows 7 partition, which uses the same graphics card.  Do you think it's a compatibility issue with the Intel HD Graphics 3000 and the VirtualBox Graphics Adapter?  Trying doing a search online and didn't find much.

---

### Post by mayagrafix on 2013-03-25
If you have an extra graphic card lying around or one u can temporarily borrow from another PC, install it and try running Win7. If 3D becomes available then, u can be pretty much sure that its the Intel graphic chip. Or try VM on another PC with a GPU thats not Intel 3000 :)

---

### Post by Cheesemill on 2013-03-25
As well as enabling 3D acceleration in the VM options, you have to install the 3D VirtualBox graphics driver in your Windows VM.

Because this driver is still experimental this has do be done in safe mode, so hit F8 as soon as you boot your VM and select 'safe mode'.
Then go through the normal procedure for installing the VirtualBox guest additions, making sure you enable the checkbox for 3D support. Reboot your VM and you should be good to go.

---

