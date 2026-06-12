---
title: "Ubuntu Server 20.04 cannot boot, Missing linux kernel"
date: 2022-03-03
forum: Server Platforms
---

### Post by dylanchr3500 on 2022-03-03
Good Day Community,

I have a pressing issue with one of my VPS servers, and the hosting provider is seemingly unwilling to assist with a lack of Feedback for 4 Days now.
I ran an apt update and upgrade on the server and the /boot partition was full, I then removed the incorrect version files from the boot directory, subsequently the server is now in a boot loop, with no options in the Grub menu.

I can boot the server with a 18.04 iso into rescue mode only or grub rescue, but after scouring the internet i cannot find concrete way of restoring the boot of this system. 

Can anybody on this forum kindly assist?

Best Regards,
Dylan

---

### Post by LHammonds on 2022-03-04
If it is a 20.04 server, you might want to boot with a 20.04 iso.  Not 100% having a different version will matter but I'd still want my recovery system to be at least the same version or higher that what I'm trying to fix.

The main thing to do in this scenario first is to clear up room on /boot by removing the old kernels...I assume you have dozens built up....or your /boot was way too small to begin with.

I have not done something like this in ages (around Ubuntu 10.04) so I don't have verified commands that will work for you but I'll see what I can google that fits this scenario.

[Ubuntu Help - Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")
[HowToGeek - How to repair grub2 when Ubuntu won't boot]("https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/")
I used [SystemRescueCD]("https://www.system-rescue.org/") as part of my restore procedure because it has fsarchiver on it which I use to backup/restore partitions.

LHammonds

---

### Post by kevdog on 2022-03-04
I think you could theoretically boot from CD/USB any linux distribution and mount the /boot partition and then remove the kernels that way.  I dont think it would necessarily have to be Ubuntu specific -- at least as a first step.

---

### Post by LHammonds on 2022-03-05
> **kevdog said:**
> I think you could theoretically boot from CD/USB any linux distribution and mount the /boot partition and then remove the kernels that way.  I dont think it would necessarily have to be Ubuntu specific -- at least as a first step.
No, it does not have to be Ubuntu or the specific version to remove but based on his post, he removed the wrong thing so rebuilding or re-downloading new kernels, it "might" be helpful to use the same version...again, I'm not well versed in this procedure.

---

### Post by MAFoElffen on 2022-03-07
Remember that "removing" is not deleting files. It means removing the installation of packages from the installed 'system.'

I believe that in talking about this (as it relates to booting from a LiveCD, a required step was missed... Using (booting from) the same or newer Ubuntu LiveCD, "*mount and chroot into the installed system,*" to remove old kernels and install the current kernel...

Once chrooted into the system, you can do what you need to repair the system, by using it's own apt system to remove/uninstall, or install what you need to.

If you need instructions to do that from an Ubuntu LiveCD, refer to post #3 of the Graphics Resolution sticky in my Signature Line. Those instructions are for standard installs. If your installed system has mdadm, LVM, ZFS, or LUKS... Mention that, and I can give you amended instructions for mounting and chroot'ing into those systems.

---

