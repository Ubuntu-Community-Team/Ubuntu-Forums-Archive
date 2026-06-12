---
title: "Can't run vboxdrv setup after kernel upgrade"
date: 2009-11-02
forum: Virtualisation
---

### Post by couzin2000 on 2009-11-02
I'm fixing an issue with my friend's Vbox. Unfortunately, I do NOT have the computer with me, so info is scarce - but here's what I have.

After downloading and installing Ubuntu updates, the usual message "cannot start vbox, please run '/etc/init.d/vboxdrv setup' to fix" is seen on screen. I ask her to run it. We get the following message:

"modprobe vboxdrv failed. Please use 'dmesg' to find out why"

So we started down this path in the forum. Found and ran this:

```
dmesg | grep VirtualBox
```
and got nothing.

Found and ran THIS:
```
dmesg | grep vbox
```
Got the following:
> [ 81.371068] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 81.371073] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[ 81.371075] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[ 440.457788] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 440.457793] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[ 440.457795] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
didn't know what that meant (since I'm no expert at this).

Then found and ran this:
```
sudo modprobe -v vboxdrv
```
and got:
> insmod /lib/modules/2.6.31-14-generic/updates/dkms/vboxdrv.ko
FATAL: Error inserting vboxdrv (/lib/modules/2.6.31-14-generic/updates/dkms/vboxdrv.ko): Invalid argument

Tried running depmod to get modprobe running:
```
sudo depmod -a
```
But running
```
sudo modprobe -v vboxdrv
```
right after gave no results.

So I'm trying to figure out the kernel version. I'm also trying to figure out if the setup command from the get-go just didn't compile the whole thing. The again, it could also be she has a hard drive failure... because I also got this message while trying to re-run /etc/init.d/vboxdrv setup:
> Result Code:
NS_ERROR_FAILURE (0x80004005)
Component:
Machine
Interface:
IMachine {4d1df26d-d9c1-4c7e-b689-15e85ecf8ffc}

Any ideas, anyone?
Just throw them my way.

Anyhow, worse case is I'll just swap her hard drive and reinstall her whole PC with 9.10... but I'd like to try and avoid that, so any help is welcome.
Thanks!

---

### Post by couzin2000 on 2009-11-03
OK... never mind. Reinstalling Virtualbox directly on top seemed to work and solve the problem. I was able to access the vdi that was there.

Thanks anyway!

---

