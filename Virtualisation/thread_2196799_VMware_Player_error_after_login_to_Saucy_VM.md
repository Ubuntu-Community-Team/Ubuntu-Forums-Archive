---
title: "VMware Player error after login to Saucy VM"
date: 2013-12-31
forum: Virtualisation
---

### Post by dsc1596 on 2013-12-31
I am running Ubuntu 14.04 64 bit on a desktop machine with AMD Radeon 6950 graphics. When I create a virtual machine in VMware running 13.10 64-bit, and go through the installation with all the default parameters, I login for the first time and I get the following:
 [IMG]http://ubuntuone.com/5bn2MVR32QzfQvHDa1Viej[/IMG]

Of course, when I disable 3d graphics acceleration in the virtual machine's settings, the error goes away. Has anyone run into a similar issue, and found a way to have 3d graphics work correctly ? I'm new to Linux somewhat, but not afraid of getting into logs and the command line if necessary.
**Edit:** Here is some output from the terminal regarding the version of the fglrx driver I currently have installed:

> jkolb@jkolb-Desktop:/media/jkolb/Behemoth$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6900 Series 
OpenGL version string: 4.2.12337 Compatibility Profile Context 13.101


Thanks!

---

### Post by brian.joe.kelley on 2014-01-01
I would grab the Ubuntu image on cd/dvd and mount in the vmware player.
Boot off of it and then mount your original installation on the vm disk file on another directory.
Disable X server from starting up upon boot by configuring X server to come up at run level 3.  Sorry,  I don't know what Ubuntu's implementation of /etc/inittab is.
I can't believe I don't see one.  But on all other unix/linux systems in the universe you have an inittab to handle how init brings up certain daemons. 
The idea is get x server and the windows emulation out of the way and see if you can run on strait text terminal without the signal 11 - which I think may be a segmentation fault (??).
You very well may have a video driver problem with your version of X server.
Also,  make sure you've installed the vmware tools.
Hope it's a place to start.

---

### Post by dsc1596 on 2014-01-01
Thanks for the post brian.joe.kelley, but I was already able to use tty1 using ctrl+alt+F1 from within the guest os as long as I entered the tty before I logged into the GUI. The error comes up whenever I login to the VM through the GUI, but the text terminal runs fine. 
However, after looking elsewhere on a vmware forum (sorry, don't have the link) I found out that this problem exists with newer versions of vmware player/vmware workstation. So, I installed version 5.0.3 and as I am writing this a new VM machine is running, and updating itself to ubuntu studio. I'll keep this open until after I do some more testing, and then mark this thread as solved if all goes well. Thanks again!

---

