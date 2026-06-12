---
title: "Can only boot into Recovery Mode"
date: 2014-03-07
forum: Ubuntu Development Version
---

### Post by alan-pater on 2014-03-07
I installed Ubuntu 14.04 on a Toshiba R700 a week ago and everything was running fine until yesterday. Now it hangs when starting up and will not finish booting. I can run Recovery Mode and then resume into a regular session.

I have removed "quiet spalsh" from grub so I could see where it is hanging.

It hangs just after Adding swap and re-mounting  the root partition.

I have used recovery mode to reinstall grub and fsck the HD. Neither makes any difference.

I then tried to boot in pure text mode, but it still hangs at the same part of the boot process.

Where do I go from here?

---

### Post by mikewhatever on 2014-03-08
Don't think it has anything to do with partitions, since the recovery mode works. I'd try starting xserver from there, and check its log. Also, testing the latest daily ISO wouldn't hurt. Remember, as 14.04 is not yet stable, problems are expected. There is a subforum for it.

---

### Post by alan-pater on 2014-03-08
It does not seem to be X related as the same thing occurs with "text" added to the linux boot line. From the Recovery mode menu, I can choose Resume and the system continues into a regular Unity session. (But the Unity session is slow, the screen is dim, and the resolution is wrong.)

---

### Post by howefield on 2014-03-08
Thread moved to the "*Ubuntu +1*" forum.

---

### Post by grahammechanical on 2014-03-08
In the Recovery mode>Resume session Unity is slow because the video driver is llvmpipe. Ubuntu now uses it as a fallback video mode for graphic adapters that are not up to running 3D accelerated graphics. It is also used when we run Recovery>Resume. 

If this was me and it has been me in the past I would change video drivers. I am deeply suspicious of proprietary video drivers. I am so suspicious of proprietary video drivers that I never install Ubuntu with the Install Third Party software option ticked. The first reboot usually gets to a desktop with Nouveau.

We have been getting updates to the Linux kernel. It is possible that a newer kernel does not like the proprietary video driver or the other way around.

You can try booting into an earlier kernel from the Advanced Options for Ubuntu sub-menu.

Regards.

---

### Post by alan-pater on 2014-03-08
No propietary video driver in use, the machine has Intel HD graphics.

I've tried 3 different kernels: 3.13.0-14-generic, 3.13.0-16-generic, and 3.13.0-16-lowlatency, they all have the same issue.

---

### Post by alan-pater on 2014-03-08
> **grahammechanical said:**
> In the Recovery mode>Resume session Unity is slow because the video driver is llvmpipe. Ubuntu now uses it as a fallback video mode for graphic adapters that are not up to running 3D accelerated graphics. It is also used when we run Recovery>Resume.Is llvmpipe hard-coded into Recovery or is there someplace I can tell it to load the Intel driver?

---

### Post by grahammechanical on 2014-03-08
Recovery mode is a collection of scripts that are found at /lib/recovery-mode/ and /lib/recovery-mode/options/. The option to Resume is part of the recovery-menu shell script at /lib/recovery-mode/recovery-menu

As far as I can see there is no instruction to load any video driver. This is the relevant portion:

> if [ "$choice" = "resume" ]; then
    box_text=$(eval_gettext "You are now going to exit the recovery mode and continue the boot sequence. Please note that some graphic drivers require a full graphical boot and so will fail when resuming from recovery. If that's the case, simply reboot from the login screen and then perform a standard boot.")
    whiptail --msgbox "$box_text" 12 70
    clear
    exit
  fi


It is possible to edit these scripts but keep backups. When I was running on a btrfs file system I used a modified version of one of these scripts  (apt-snapshot) to produce extra options in recovery mode to view/delete/revert/create btrfs snapshots. But do not take that to mean that I understood what I was doing. It was a bit like Doctor Frankenstein sewing body parts together without the lightning.

In situations like the one that you are in I use Recovery>Network and Recovery>Root to update/upgrade the installation in the hopes of things being fixed and meanwhile use another Ubuntu install to keep working.

Regards.

---

### Post by alan-pater on 2014-03-08
As I can get to a full Unity desktop from Recovery > Resume I have been updating and reconfiguring from there.
From the xorg.log I see that the machine is running the Intel X server, not the llvmpipe, it just does not have the correct resolution.
I tried a mainline kernel (3.14 rc5), but no difference, it still hangs at the same spot.
Kernel boot options I have tried (without any effect): text, single, apparmour=0 ...
I have also added lines in /etc/fstab to prevent automounting of ntfs partitions, but to no effect.
And I have uninstalled some of the extra services I had setup: lxc, nginx, mysql. Again to no effect.

So, right now all I can do is boot through Recovery > Resume and suffer through the funky resolution and slow desktop.

---

### Post by alan-pater on 2014-03-08
Well, I decided to bit the bullet and reinstall. So far it is working, boots right into the GUI without any errors, Unity is fast, the resolution is correct.

I'll leave things as they are for a few days before doing any updates.

---

### Post by gbrunati on 2014-09-15
I don't know the reason why, but I will show what I did and solved the problem:


1. Start Additional Drivers Application
2. Check NVIDIA legacy binary driver version 304.117 from nvidia-304 (proprietary, tested) button.
3. Restart


and that's OK!


GBrunati

---

### Post by rrnbtter on 2014-09-16
Greetings,
You probably have a permissions problem in your home directory. This is a bit unconventional but from a root terminal do this....
sudo chown owner:owner /home/owner/*
sudo chown owner:owner /home/owner/.*

Replace owner with your own login. You should get a boot from there.

---

### Post by Elfy on 2014-09-16
If people still have issues with this in Trusty - start a new thread in the main support areas. 

Closed.

---

