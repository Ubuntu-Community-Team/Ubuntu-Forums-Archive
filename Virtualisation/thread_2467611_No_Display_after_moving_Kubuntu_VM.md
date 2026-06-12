---
title: "No Display after moving Kubuntu VM"
date: 2021-10-01
forum: Virtualisation
---

### Post by philld2 on 2021-10-01
This is the second time I attempted to do this.  The first time the host OS and the target OS were the same version / distribution.  This time, I was moving the VM from a Fedora host (v32 (can't update because of video card)) to the target PCLinuxOS host.  In both cases, the VM boots and I see the Kbuntu screen, it then goes blank and I next expect to see the login screen but it never appears.  The Kubuntu VM is running 20.04 (with latest updates).  The VM is running within Virtual Box 6.1 (both old and new VMs).  I have tried changing the video adapter within Virtual Box but that does not seem to have any effect - the screen is still blank after booting.  Video memory is set at 16MB and RAM is set at 3GB for the VM.  The first time it happened, I rebuild the VM machine from scratch.  I have moved machines previously without incident - in fact I moved a second machine as part of this transfer of host machines and the second booted successfully (Windows).  Not sure what else to check for the Kubuntu VM to boot successfully.

---

### Post by TheFu on 2021-10-01
I haven't used vbox in about a decade.  This is 100% a virtualization question, BTW.

No proprietary video drivers in the VM. Ensure there aren't any installed.

For desktops, in the vbox settings, set the display memory to the largest value allowed - I think that was 128MB. Disable 2D and 3D accel there, for now.

---

### Post by QIII on 2021-10-01
Moved to Virtualisation.

---

### Post by philld2 on 2021-10-02
Thanks for the suggestion TheFu.   Set the video memory up to 128MB and check that there was no acceleration enabled as suggested - alias, the problem continues - I see the Kubuntu screen and then it goes black before the login screen appears.

---

### Post by MAFoElffen on 2021-10-02
If at the grub menu, if you press <E> to edit, got down to the line starting with "linux", replace "quiet splash" with "text"... Then Press <Cntrl><X> to boot.

Does it boot the Kernel to a console?

If it does, then you could at least parse the logs to see where the problem may lie. It is early in the graphics layer, so may be related with either KMS or the VM Virt HW settings. Just initial guess until more information is provided.

Also not provided, and a curiosity... What is the difference in the VM Hosts? If the are running the same version of OS and of VBox... If they have the same CPU's, because the kernel and VBox modules may make a difference on different CPU's...

And if different VBox versions, is there a Guest Additions version mismatch?

---

### Post by philld2 on 2021-10-03
There is no grub menu presented (think I have ever seen a grub menu with Kubuntu only once when I was having a problem with the boot) is there a way to have the grub menu presented? 

Here are the particular's re the two host systems:
OLD HOST
Virtual Box - Version 6.1.26 r145957 (Qt5.14.2)

Operating System: Fedora 32
KDE Plasma Version: 5.18.5
KDE Frameworks Version: 5.75.0
Qt Version: 5.14.2
Kernel Version: 5.8.18-200.fc32.x86_64
OS Type: 64-bit
Processors: 3 × AMD Phenom(tm) II X3 720 Processor
Memory: 11.7 GiB of RAM

Fedora did not list the graphics driver but from what I can determine it is the noveau driver as the Nvidia card is old.

NEW HOST
VirtualBox - Version 6.1.26 r145957 (Qt5.6.1)

Operating System: PCLinuxOS 2021
KDE Frameworks Version: 5.86.0
Qt Version: 5.15.2
Kernel Version: 5.14.9-pclos1 (64-bit)
Graphics Platform: X11
Processors: 6 × Intel® Core™ i5-8400 CPU @ 2.80GHz
Memory: 15.5 GiB of RAM
Graphics Processor: llvmpipe

---

### Post by philld2 on 2021-10-04
Update on accessing the grub menu - after searching the web, I found that I could display the grub menu after pressing the "Shift" key when the VM was booting.  Made the change as suggested above, i.e. "text" replacing the "quiet splash".  After pressing the Cntl/X the machine began to boot and the boot messages were displayed on the screen alias however, the login screen was still black.

---

### Post by philld2 on 2021-10-04
Update

I have been able to solve the problem but its not clear as to what was causing the screen not to be displayed.

The solution was to press Shift to have the grub menu presented (see post below).  From there, I choose the Ubuntu recovery option.  From that menu, first I choose to enable the network and then to perform a "clean".  The updated a number of modules.  After that was completed, I then choose the "resume" normal mode.  The KDE login screen was presented and all appears to be working as expected.

---

### Post by TheFu on 2021-10-04
Maintenance for Ubuntu Desktop systems ... [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

Besides the other things, every few weeks, run these:
```
sudo apt autoclean
sudo apt autoremove
```

This can be very important on systems with limited storage.

---

