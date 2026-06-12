---
title: "Can I use a scanner with a virtual machine?"
date: 2008-12-18
forum: Virtualisation
---

### Post by BetterSense on 2008-12-18
Can I virtualize XP and then just install the software that comes with the scanner and have it work? Forgive my noobularness.

This is the first time I've had hardware trouble with linux. I want to buy a film scanner and all the recent ones (Epson V500) do not have linux drivers that enable the film-scanning features. There is software called vuescan that claims to support these scanners in linux but I have heard conflicting reports. But it is superior scanning software. Could I use the windows version of vuescan in a virtual XP install?

I was considering using a virtual machine with XP. I actually have a VirtualBox XP now that I installed but had no use for, but I cannot use USB devices with it. However, it seems that the non-ose Virtualbox can use USB (I don't know what I have now, how can I check?)

---

### Post by HotShotDJ on 2008-12-18
> **BetterSense said:**
> Can I virtualize XP and then just install the software that comes with the scanner and have it work? Forgive my noobularness.If you use the full PUEL version of VirtualBox from Sun, you should be able to just install the software/drivers that came with the scanner in your virtualized XP machine and be good to go.> **BetterSense said:**
> I was considering using a virtual machine with XP. I actually have a VirtualBox XP now that I installed but had no use for, but I cannot use USB devices with it. However, it seems that the non-ose Virtualbox can use USB (I don't know what I have now, how can I check?)First, open System --> Administration --> Synaptic Package Manager.  Click on the SEARCH button and type virtualbox.  This will tell you which version you have installed.  For USB, you'll need to get the full version from Sun, which is easily accomplished by following the instructions at the following link: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

It is best not to download the application, but to add the repository to Synaptic by following the instructions given toward the bottom of that web page, entitled: Debian-based Linux distributions

Once you've done this, open Synaptic Package Manager again, click on the "Reload" button, then find and install virtualbox-2.1.  To get USB running after you've installed, follow this thread: [http://ubuntuforums.org/showthread.php?t=1003480](http://ubuntuforums.org/showthread.php?t=1003480)

---

### Post by Dedoimedo on 2008-12-18
Hello,
Indeed, OSE version has no USB support. PUEL does.
And yes, once you get XP virtualized, you can install software in it, just as you normally would. It should work. You might have problems with software that requires 3D acceleration, but otherwise, you should be fine.
Dedoimedo

---

### Post by HotShotDJ on 2008-12-18
> **Dedoimedo said:**
> You might have problems with software that requires 3D accelerationVirtualBox 2.1 has experimental 3D support for applications that use OpenGL -- they say that Direct3D will be supported in a later version.  Of course, the operative word there is "Experimental" so it may or may not work as expected.  But things are moving in the right direction.

See: [http://jeremy.visser.name/2008/12/18/virtualbox-210-does-opengl-3d-acceleration/](http://jeremy.visser.name/2008/12/18/virtualbox-210-does-opengl-3d-acceleration/)

See also: [http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog)

---

### Post by BetterSense on 2008-12-18
thanks very much everyone. I had an old virtualbox package installed; synaptic said something about gutsy. I added the repo and now I'm installing virtualbox-2.1 with synaptic.

---

