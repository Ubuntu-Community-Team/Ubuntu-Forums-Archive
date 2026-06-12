---
title: "Help setting up Fedora in VBox"
date: 2011-04-10
forum: Virtualisation
---

### Post by amcknight2718 on 2011-04-10
Hi, I'm new to virtualization and am attempting to set up a Fedora vm in virtualbox for practice. I'm running Ubuntu 10.10 which is dual-booted with windows 7 on my laptop.

So, I downloaded the .iso and have it running in vbox, but i'm not sure whether it is installed on the disk or is just booting from the image. 

I opened the icon on its desktop to "install to hard disk." Now, I'm not that great with partitioning anyways, so i'm not exactly sure what I'm doing. For now, I'm selecting the option to just create a new partition and leave everything else as is. But, when I review the changes, it tells me that it's going to "format the pre-existing device at /dev/sda - partition table (MSDOS)."

I assumed that it would just install the Fedora OS inside the vm hard disk folder that vbox created for me. Am I wrong in that assumption? Should I just never install Fedora and always boot it from the iso? Any other advice you'd like to share?

---

### Post by CharlesA on 2011-04-10
You are correct, it'll install it to the virtual hard drive. No real reason to always boot from a livecd.

Just remember to remove the ISO after the install is complete to prevent the VM from trying to boot from it.

---

### Post by UltraZone on 2011-04-15
I had problems setting up this very same setup but here's the tiny trick to accomplish a successful installation, such that the guest OS is installed with a bonafide username/password (not liveuser).

You launch the installer in the liveuser home folder, go through the whole process, selecting all default settings (you can tinker with it but, will work out of the box with all defaults), make sure you select "replace existing OS" (or something to that effect), allow finishing the installation.  Next within Fedora, restart.  Next there will be the services shutdown list, next will come the VirtualBox boot splash screen: press F12 at this point.  Select Hard drive from list (type in 1).  Continue with username/password setup.  

Now in the future if you need to restart within Fedora, you gotta go through this F12 then 1 process, unless you open up Dolphin, then right lick on the mounted Fedora Live CD and unmount it.  Restart within Fedora, next time it boots, it will not boot from the live cd, but from the newly installed OS on the harddrive (virtual harddrive).

---

