---
title: "VirtualBox, VMware, XEN, or ?"
date: 2008-05-06
forum: Virtualisation
---

### Post by chandra on 2008-05-06
Dear Folks,

I seek suggestions on which virtualization software is best supported on *buntu for running an MS Windows XP virtual machine on a current *buntu distribution:

1. VirtualBox;

2. VMware;

3. XEN; or

4. Something else.

I seek a full feature set in the guest OS, including support for USBs, and also easy upgrade of the virtual machine when the Linux kernel or *buntu distribution is upgraded.

Many thanks.

---

### Post by sekinto on 2008-05-07
Formerly I used Qemu, but I tried VirtualBox and I really love it. I would recomend VirtualBox.

---

### Post by p_quarles on 2008-05-07
Moved to Virtualization.

I use Virtualbox, and have never had any trouble with. For full functionality, you'll need to install the Guest Extras onto the Windows VM.

---

### Post by jrusso2 on 2008-05-07
I would have to say Virtual box is the best atm  Unless you want to buy vmware workstation which I really don't think is worth it

---

### Post by Ameneon on 2008-05-07
Have to concur here, granted I've only ever used VMWare and Virtualbox but I have seen nothing in VMWare that warrants me paying money for it when Virtualbox is as well performing, easy and stable to use as it is..

---

### Post by Calash on 2008-05-07
If you want to invest the money, VMEare Workstation is an amazing product.  We use it at work for a development environment (1 server, 4 workstations on a XP32 Host...soon to be XP64 to take advantage of higher memory limits) and it runs great.  Configuring it is very simple and it took no time at all to get it online and running.

At home I use Virutalbox, as it is the closest free alternative.  It has many of the same options, though on Ubuntu they can be more difficult to setup.  VMWare Server was easy to setup but did not have all the options I wanted.

So, my vote is Virtualbox for Free, VMWare Workstation for payed.

---

### Post by MemoryDump on 2008-05-07
I'm loving VirtualBox. Very easy to install and configure.

---

### Post by MNICY on 2008-05-07
Virtualbox is great.

---

### Post by vexorian on 2008-05-07
I love virtualbox, and I don't think I could have done my switch without its USB support. Even though lately now that Sun has taken over I've noticed that it for example no longer respects my gnome-panel when it is using seamless done, they also changed the name to "Sun xVM virtual box" which is ridiculous... First oOO and now virtualBox, thanks Sun... Anyways I keep it, as a matter of fact the freeware VirtualBox is much better than the costly vmware, I have not tested virtualbox OSE from the repos but it should do fine as well?

---

### Post by brentwas on 2008-05-07
i would pick any of those if i would be sure that google sketchup will run.
any experiences from your side?

---

### Post by chandra on 2008-05-10
Thanks to everyone for your replies. Based on that, I have installed and started using VirtualBox 1.6.0 packaged as 

virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb

from the Sun Download site, under the PUEL licence.

The VirtualBox experience (running Windows XP) is superior to my prior experience with VMWare for the following reasons:

1. It is free.

2. There is no hassle compiling and working around with an any-any-update<nnn>, searching for the correct gcc, and choosing how to network etc. VirtualBox simply works out of the box and is obviously a better fit to Ubuntu than VMware.

3. Mouse integration after installing the VirtualBox Guest Additions is superb. There is no need to release the mouse to move from the virtual machine to the host. This is a tremendous improvement in user experience.

4. The virtual machine seems to respond and run applications faster in VirtualBox than in VMWare, but this is subjective.

The only sticking point was with USB integration. Apparently this is a longstanding problem and there are workarounds at:

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

and at:

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

I used the latter solution and it seems to work OK for now. The only inconvenience is that the USB device is not returned to the host after disconnection by the VM as in VMWare.

All in all, a very good experience with VirtualBox.

Thank you all once more.

---

