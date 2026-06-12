---
title: "Ubuntu crashes with Virtualbox, excessive HDD I/O"
date: 2009-02-22
forum: Virtualisation
---

### Post by themusicalduck on 2009-02-22
When I try to run a virtualmachine on Ubuntu (most of the time Windows XP) after a few minutes it will usually crash Ubuntu. At first Ubuntu will start to run very choppily and the hard drive light will stay on constantly. If I can catch it before it becomes unresponsive, then I can ctrl alt backspace and it sorts it, but if I don't then I have to hard reset.

This happens most of the time I run a virtual machine, sometimes after running the machine for a few seconds or sometimes after 20 minutes or so and I am not generally doing anything too intensive on it when it happens, in fact it usually happens when I'm not using it at all at that time. Often it will work the second time I try after a hard reset, though not always. I've also found this seems to have happened once or twice while Vbox has not been running, but since it seems to be pretty certain to happen if I do run Vbox, then I'm starting there to try and work out what's happening.

I'm running Ubuntu 8.10 32 bit and Vbox 2.1.4.

---

### Post by themusicalduck on 2009-02-23
bump

---

### Post by Ng Oon-Ee on 2009-02-24
How much RAM and swap do you have? Excessive HD I/O usually indicates that your Ubuntu install is running out of Virtual memory (RAM + swap). You may also have assigned too much memory to Windows, but I think there's big warnings on VBox if you assign more than half the available RAM to a VM (I've never done it, 3 GB on this box).

---

### Post by MaindotC on 2009-02-28
Can you run VirtualBox from a terminal and see if you see anything in the terminal before it crashes?  Also can you post your hardware with links like I have in my signature?

After installing 2.1.4 I'm experiencing 90 - 100% CPU usage for running 1 vm so I'm curious as to what's going on as well.

---

### Post by MaindotC on 2009-03-06
It turns out my real issue was Flash.  Browsing nhl.tv is pretty flash-intensive and for some reason that incurrs a lot of CPU usage on my 64-bit install.  Virtualbox working fine for me now - except Fedora in a VM refuses to access USB devices...

---

