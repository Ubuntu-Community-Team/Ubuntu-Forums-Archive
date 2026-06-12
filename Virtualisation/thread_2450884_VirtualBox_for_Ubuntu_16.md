---
title: "VirtualBox for Ubuntu 16"
date: 2020-09-22
forum: Virtualisation
---

### Post by failsafenow on 2020-09-22
Ok. I'm trying to get VirtualBox going on my machine. I have a Lenovo x131e Chromebook running Ubuntu 16.04 through Crouton. The kernel version is 3.8.11. I'm trying to run VirtualBox. I installed it from the Ubuntu repository, along with virtualbox-dkms. But when I run VirtualBox, it says this:

Please install the virtualbox-dkms package and the appropriate headers, most likely linux-headers-3.8.11.

I tried to install headers for 3.8.11, but:

E: Unable to locate package linux-headers-3.8.11
E: Couldn't find any package by glob 'linux-headers-3.8.11'
E: Couldn't find any package by regex 'linux-headers-3.8.11'

I was able to install linux-headers-generic, based on someone else's advice, and I did the reconfigure thing for VirtualBox and 

virtualbox-dkms, but I still get the aforementioned error:

Please install the virtualbox-dkms package and the appropriate headers, most likely linux-headers-3.8.11.

So what do I do? I want this thing to work. And hell, I'll take VirtualBox, I'll take VMWare, I'll take anything, just so I can run virtual machines. Someone please help me.

---

### Post by TheFu on 2020-09-23
You can't.
You need access the kernel modules and crouton doesn't allow that.

If you want to run VMs on a chromebook, you'll need to wipe ChromeOS, break the warranty sticker, replace the firmware and BIOS, then load an OS that you control.  Look up "Mr. Chromebox" for guides.  Different devices are easier than others. Some devices cannot do it at all.

I've run KVM as a hypervisor on 2 chromebooks.  An Acer C720 and a Toshiba CB35.  Both were limited due to only having 2GB and 4GB of RAM, but it worked.

There are other alternatives, if you have a desktop computer that can run virtual machines.  Remotely connect from the chromebook into those other systems using remote tools.  I'd use virt-manager or virt-viewer and the SPICE protocol through an encrypted ssh tunnel, if it was me. SPICE is the fastest remote X11 protocol.  I've never tried it on a chromebook running ChromeOS. It may not be possible, but there aren't any kernel modules needed, so it should work ... assuming the device isn't ARM-based.

---

