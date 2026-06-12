---
title: "A suggestion for Ubuntu 16.04 LTS, hibernate"
date: 2015-12-13
forum: Ubuntu, Linux and OS Chat
---

### Post by xuancong84 on 2015-12-13
It is a shame for Ubuntu that in Windows or MacOS, you can perform  hibernate by just clicking one button, but in Ubuntu, you have to do the  following:
Part 1 - make swap file
```

cat /proc/meminfo
## Note memory size. Graphics card may eat a chunk of main RAM
## We will need swapfile the size of N to 2*N of RAM
sudo swapoff -a
sudo dd if=/dev/zero of=/swapfile bs=1024 count=8M    ;## 2*N of RAM, swap size=count*bs
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
sudo filefrag -v /swapfile | grep "First block:"    ;## get First block -> resume_offset
# for grub2:
sudo filefrag -v /swapfile    ;## get first "physical" number -> resume_offset
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
I realize that hibernate is quite useful for PC when you need to standby  for long time. It is also quite useful for servers, when you need to  shutdown due to server room power maintenance. And I hope in Ubuntu  16.04 LTS and later, the hibernate function can be better supported  using just an image file instead of a swap partition. And users do not  need to go through the above complications to do so.

FYI, currently, hibernation does not work even with a large enough swap  partition. The error message says, "Failed to unload some modules:  nvidia". Apparently, the feature has not been implemented properly  because it requires to unload modules which should not be the case. It  should just take a snapshot of everything: memory (graphics memory is  mapped to memory), all device state, CPU state, etc. After resuming,  some devices like network (wifi) will be reset as previous connections  are broken. Thus, it should affect some network applications that has  went halfway. But all local applications should resume fine.

Btw, I  never use a swap partition because our machines have very big memory,  and once some programs run out of memory, swapping will cause the  machine to run extremely slow, the whole machine will essentially get  stuck. It would be better to kill a few  most memory intensive programs.

Anyway, it is just my hope. A suggestion! And I welcome a discussion!

---

### Post by Bucky Ball on 2015-12-13
*Thread moved to **Ubuntu, Linux and OS Chat**.*

... and

*Thread closed.*

Please do not post duplicate threads on the same topic. There is already a [discussion you've started here]("http://ubuntuforums.org/showthread.php?t=2306178") so unsure why you started another (in a support area).

---

