---
title: "mdrun missing from 7.10 install disc"
date: 2007-12-12
forum: Server Platforms
---

### Post by rsw686 on 2007-12-12
I have been testing out scenarios utilizing software RAID. One was to reinstall the OS without disturbing the RAID. Unfortunately Ubuntu's installer is horrible at detecting existing RAID arrays. It just shows the drives with the linux raid partitions, but not the md devices.

I was able to get this to work by switching to a virtual terminal when prompted for the network hostname and running the following

modprobe raid1
modprobe dom_mod

And this is where the fun began. Ubuntu is missing mdrun, Debian has it included so I would have thought it would be on Ubuntu's install disc as well.

Instead of just running mdrun and switching back to the installer I had to use mdadm --assemble. What a pain.

If you need LVM support you need to run the following before switching back to the installer.

lvscan
vgchange -a y

Why can't the partitioner have a text line to click to scan for existing RAID devices and LVM volumes?

---

### Post by rsw686 on 2007-12-12
Alright I figured it all out. mdrun is depreciated so you must use mdadm to generate a temp config

mdadm --examine --scan > /tmp/mdadm.conf
mdadm --assemble --scan --config=/tmp/mdadm.conf

I still think there should be a scan for RAID and LVM button.

---

### Post by davidpodhola on 2008-02-09
Yes, I have also not found it there and I was very confused because I really needed it. I was unable to boot my 7.10 after I had had created /dev/md0 with "alert /dev/md0 does not exist". I have found somewhere that adding mdrun to init would help. As mdrun is no longer there, I used "mdadm --assemble --scan" and I have written it to "/usr/share/initramfs-tools/init" and I have run "sudo update-initramfs -k all -u" then. It it saying some errors during boot, but is booting after all.

---

