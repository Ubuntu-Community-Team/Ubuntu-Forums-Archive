---
title: "Starting VirtualBox kernel modules ...failed!"
date: 2016-05-09
forum: Virtualisation
---

### Post by 1cookie on 2016-05-09
Hi

I'm trying to install Virtualbox on my desktop:

Processor: AMD FX(tm)-8350 Eight-Core Processor × 8 
OS type: 64bit
Ubuntu 16.04


Here's a snapshot of my bash history:

```

35  sudo dpkg -i /home/andy/Downloads/virtualbox-5.0_5.0.20-106931~Ubuntu~xenial_amd64.deb 
36  sudo apt-get install libqt4-opengl
37  sudo apt-get -f install
38  sudo apt-get install linux-headers-generic
39  sudo /etc/init.d/vboxdrv setup
40  virtualbox
41  sudo /sbin/rcvboxdrv setup
42  dmesg | grep VirtualBox
43  sudo apt-get install linux-headers-generic build-essential
44  sudo modprobe -v vboxdrv
45  dmesg
46  sudo systemctl status vboxdrv

```

Expanding on those commands a little:

```

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```


```

$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found

```

```

$ virtualbox
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (4.4.0-22-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /sbin/rcvboxdrv setup

         You will not be able to start VMs until this problem is fixed.

```

```

$ sudo /sbin/rcvboxdrv setup
Stopping VirtualBox kernel modules ...done.
Removing old VirtualBox pci kernel module ...done.
Removing old VirtualBox netadp kernel module ...done.
Removing old VirtualBox netflt kernel module ...done.
Removing old VirtualBox kernel module ...done.
Recompiling VirtualBox kernel modules ...done.
Starting VirtualBox kernel modules ...failed!
  (modprobe vboxdrv failed. Please use 'dmesg' to find out why)

```

```

$ dmesg
[ 5845.992334] capability: warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 6004.050016] show_signal_msg: 33 callbacks suppressed
[ 6004.050022] Chrome_ChildThr[7835]: segfault at 0 ip 0000562e33366a24 sp 00007f278abfe360 error 6 in plugin-container[562e3335e000+3d000]
[ 6050.579010] Chrome_ChildThr[10708]: segfault at 0 ip 0000563aaf904a24 sp 00007f51711fe360 error 6 in plugin-container[563aaf8fc000+3d000]

```

So the '(modprobe vboxdrv failed' is problematic. A google reveals a similar story over here: 

[https://www.virtualbox.org/ticket/11577](https://www.virtualbox.org/ticket/11577)

Do you have any idea how we can overcome this hurdle. Is it a BIOS related issue?
[URL="https://www.virtualbox.org/ticket/11577"]












[/URL]

---

### Post by 1cookie on 2016-05-09
> **1cookie said:**
> 
  Is it a BIOS related issue?[URL="https://www.virtualbox.org/ticket/11577"]
[/URL]

I checked my BIOS, in CPU Configuration / SVM this is set to 'enabled'.

This secure virtual mode will let you run multiple OS (guest) on the same physical hardware with the hypervisor layer.

Despite all this it still wont launch?

---

### Post by JKyleOKC on 2016-05-10
FWIW, I'm having a similar problem here after upgrading my kernel with today's Software Updater releases. The 3.13.0-86 kernel generates a system error during boot, complaining about VBox 5.0.20; however reverting back to the 3.13.0-85 kernel that has worked properly for the past two months solved everything for me.

Apparently there's some change that makes the newest versions incompatible. There's nothing about any such problem on the vbox forums themselves; hopefully one or more gurus here will be able to track it down and come up with a fix.

---

### Post by MAFoElffen on 2016-05-10
Try this before the vboxdrv setup
```

sudo apt-get install virtualbox-dkms
sudo /etc/init.d/vboxdrv setup

```
Most of the time, the line I said to install does that setup in it's install process, but just to be sure... try it after and see if it says there is any else to do. (Better to cover it twice, than have it miss something.)

---

### Post by 1cookie on 2016-05-11
I run those commands:

```

$ sudo apt-get install virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-dkms is already the newest version (5.0.18-dfsg-2build1).
0 to upgrade, 0 to newly install, 0 to remove and 15 not to upgrade.

```
```

$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found

```

thanks in advance

---

### Post by 1cookie on 2016-05-11
This solved it for me: [http://unix.stackexchange.com/questions/282265/starting-virtualbox-kernel-modules-failed/282375#282375](http://unix.stackexchange.com/questions/282265/starting-virtualbox-kernel-modules-failed/282375#282375)

---

### Post by MAFoElffen on 2016-05-12
Note to others: User's installed package dkms,( which is a depnency of, and should have been installed by default when that package installed) virtualbox-dkms...

Congrats. Please return to this thread > Use the link in the upper right of the page "Thread Tools" > Select "Mark Thread As Solved""

---

