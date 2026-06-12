---
title: "Trouble installing via VirtualPC / VirtualBox - various errors, Intel VT enabled"
date: 2015-01-31
forum: Virtualisation
---

### Post by jmason2 on 2015-01-31
Hi all, I am new to ubuntu and working to install this on my workstation. I have both Virtual PC and Oracle VirtualBox installed. Both are  providing inconsistent error messages and are preventing me from  installing. Attempting to run **ubuntu-14.10-desktop-amd64.iso** - Specs, Error reports and processor read out posted below;

**Specs:**
Intel Xeon W530 2.8 Quad Core w/ Intel VT-x enabled
Intel X58 Chipset
20GB DDR RAM
NVIDIA Quadro 3800FX
HD 1TB @ 7200rpm
WIN 7 Pro

Bios has been updated to Dell A17 (latest version) and Chipset has been updated to latest version as well. Both virtualization options are enabled in bios.

Attempted at least 20 restarts and verified bios settings numerous times.

[SIZE=5]Errors in Oracle Virtualbox v4.3.20 -[/SIZE]
Error 1 populates then flows right in to the second message without any inputs from my end: [IMG]http://i.imgur.com/hqY0XXl.png[/IMG]
Error 2:
[IMG]http://i.imgur.com/3AjtspZ.png[/IMG]

From here, Error 2 rolls into a wonderful rainbow looking screen.
Final window:
 [IMG]http://i.imgur.com/e6E2Y7R.png[/IMG]

[SIZE=5]Error in Windows Virtual PC[/SIZE]
Error: Requests x86-64 CPU but it is running on a 64bit CPU (intel report included)
[IMG]https://i.imgur.com/DZeNkFY.jpg[/IMG]
That is as far as I get in this VM.

***[SIZE=5]Any help and or assistance is much appreciated. Thanks in advance![/SIZE]***

---

### Post by TheFu on 2015-01-31
Try xubuntu or lubuntu.  These don't require high-end GPU emulation like the stock Ubuntu does.
Also - verify that you've provided the max amount of video RAM to the guestOS. The defaults are crap.

---

### Post by jmason2 on 2015-01-31
Upgraded video ram from 12(!)mb to 50. Did not work with Ubuntu.

Tried Xubuntu -- virtual PC was a no go (same X86-64 error) however VirtualBox seems to be installing it now. The 50mb of video ram must have been a help.

Not perfect but it works so much appreciated!

---

### Post by TheFu on 2015-01-31
> max amount of video RAM 128MB.
Also - there are some simple settings to make things faster [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)  should be able to get 90% native speed for productivity applications.

---

### Post by jmason2 on 2015-02-02
Thank you!

Set 128MB (max setting) as my video ram (out of 1gig on the card) and attempted to run Ubuntu again. No luck.

Read through your guide and caught a few areas that needed to be addressed -- ie fixed drive size, chipset etc. Made the adjustments but we are still running into the same errors noted above in VirtualBox.

This is strange as Ubuntu had no issues running during the LiveCD test. Going to grab Lubuntu (Xubuntu worked) now and see what that does.

Any thing else I can try to get Ubuntu to roll? Unity 2d is purdy. Thanks!

---

### Post by TheFu on 2015-02-02
Unity wants 3D Accel hardware. 
It is not happy inside a VM, IME. I stopped trying to use it years ago for 2 reasons.
a) I don't like Unity (actually use a pure-WM myself, no DEs).
b) I've seen the most powerful host hardware brought to a crawl trying to run Unity in a VM.

BTW, no need to load a different distro over a GUI change. It is just another program. This isn't like those other OSes which warp many minds.  On Unix systems, the gui is just another program. Swap out the one being used as you like.

---

### Post by jmason2 on 2015-02-11
Appreciate your helping me get this vm running. Just installed the Guest Additions and things are running smoothly.

Thanks!

---

### Post by TheFu on 2015-02-12
If solved, please mark the thread as solved in the thread tools.

---

