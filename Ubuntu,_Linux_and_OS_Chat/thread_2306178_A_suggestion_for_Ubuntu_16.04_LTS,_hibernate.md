---
title: "A suggestion for Ubuntu 16.04 LTS, hibernate"
date: 2015-12-12
forum: Ubuntu, Linux and OS Chat
---

### Post by xuancong84 on 2015-12-12
It is a shame for Ubuntu that in Windows or MacOS, you can perform hibernate by just clicking one button, but in Ubuntu, you have to do the following:
Part 1 - make swap file
```
cat /proc/meminfo
## Note memory size. Graphics card may eat a chunk of main RAM
## We will need swapfile the size of N to 2*N of RAM
sudo swapoff -a
sudo dd if=/dev/zero of=/swapfile bs=1024 count=8M	;## 2*N of RAM, swap size=count*bs
sudo chmod 600 /swapfile && sudo mkswap /swapfile && sudo swapon /swapfile
sudo -b gedit /etc/fstab
# Remove ALL old swap partitions
# Add: /swapfile   none   swap   sw   0   0
free -m
swapon
```
Part 2 - use swap file for hibernation
```
mount | grep " / "    ;# Note your /dev/... on /
sudo blkid -g
sudo blkid    ;## get / -> /dev/... -> partition UUID -> resume=UUID=
sudo filefrag -v /swapfile | grep "First block:"	;## get First block -> resume_offset
# for grub2:
sudo filefrag -v /swapfile	;## get first "physical" number -> resume_offset
echo "resume=UUID=cdXX--X18 resume_offset=66050" | sudo tee /etc/initramfs-tools/conf.d/resume
sudo -b gedit /boot/grub/menu.lst
# kopt=root=UUID=... ro resume=UUID=cdXX--X18 resume_offset=66050 
# for grub2:
sudo -b gedit /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="... resume=UUID=cdXX--X18 resume_offset=66050"
sudo update-grub -y
# Answer "use maintainer version" if it asks
sudo update-initramfs -u
```
I realize that hibernate is quite useful for PC when you need to standby for long time. It is also quite useful for servers, when you need to shutdown due to server room power maintenance. And I hope in Ubuntu 16.04 LTS and later, the hibernate function can be better supported using just an image file instead of a swap partition. And users do not need to go through the above complications to do so.

Thanks!

---

### Post by ian-weisser on 2015-12-13
One-click hibernate is already in Ubuntu...for hardware that reliably supports it.
Ubuntu's Power Manager tests for that hardware support, and only offers hibernate if the hardware responds properly.
See [https://help.ubuntu.com/stable/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/stable/ubuntu-help/power-hibernate.html) for more information.

It is possible for users to enable hibernate on hardware that failed the Power Manager test...but do so at your own risk. It may work, it may not.

If hibernate were completely unimplemented, four months before release is much too late to begin working on such a feature that requires much testing and QA.

---

### Post by QIII on 2015-12-13
When Ubuntu (or any LInux distro) is being initially installed and the swap partition is made large enough to capture the entire state of the RAM, that is if the size of the Swap partition is equal to or greater than the amount of RAM, hibernation (suspend to disk) works fine.  I suggest 1.1x to 1.25x RAM for this purpose.

A Swap partition too small to capture the entire state of RAM will cause hibernation to work improperly.

So the "fix" is to create a Swap partition greater than the size of the RAM at installation time.  Unlike Windows, hibernation does not dynamically resize the amount of disk space required to hibernate.  It's not a shame.  It's by purposeful design.  It's keeping control of the operations on your machine rather than letting it decide for you what you want.

---

### Post by buzzingrobot on 2015-12-13
The hibernated image needs to go someplace. Re-purposing the swap partition is efficient, and avoids devoting a portion of the disk exclusively to retaining that data. The alternative, then, would be for an installer, after it judged the hardware capable of supporting hibernation, to create that separate hibernation partition.

---

### Post by xuancong84 on 2015-12-13
FYI, currently, hibernation does not work even with a large enough swap partition. The error message says, "Failed to unload some modules: nvidia". Apparently, the feature has not been implemented properly because it requires to unload modules which should not be the case. It should just take a snapshot of everything: memory (graphics memory is mapped to memory), all device state, CPU state, etc. After resuming, some devices like network (wifi) will be reset as previous connections are broken. Thus, it should affect some network applications that has went halfway. But all local applications should resume fine.
Btw, I never use a swap partition because our machines have very big memory, and once some programs run out of memory, swapping will cause the machine to run extremely slow, the whole machine will essentially get stuck. It would be better to kill a few  most memory intensive programs.
Anyway, it is just my hope. A suggestion!

---

### Post by QIII on 2015-12-14
Shouldn't it?  Should it maintain the state of everything?  Even modules that taint the kernel?  Maybe.  Maybe not.

I don't see hundreds of posts by users of laptops/notebooks complaining about non-functional hibernation, which would be the case if currently supported releases demonstrated this behavior.

You can change swappiness.  You can have a swap partition without your machine automatically using it without your consent.  If you can run everything without a swap partition now, it is patently clear that swap is not needed during normal operations.  But it is most certainly needed for hibernation.

Maintain the state of graphics memory?  Why?

I suppose I could install another instance of the development version and see (right now I run without swap because I don't hibernate my desktops and my laptop, which hibernates fine, runs Fedora), but I'm not going to since this has worked on supported versions for years.

Understand, I'm not being contrary.  I'm saying that this is something that does, in fact, work.  You may have something going on that should be dealt with, but hibernation is not a universal issue.

---

