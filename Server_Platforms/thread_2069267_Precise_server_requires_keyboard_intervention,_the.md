---
title: "Precise server requires keyboard intervention, then boots into old kernel"
date: 2012-10-10
forum: Server Platforms
---

### Post by dsmithhfx on 2012-10-10
Hi,

I've run into a couple of odd problems: after removing some old kernels (using Ubuntu Tweak / Janitor function), and creating a backup OS partition (cloned from an earlier backup using fsarchiver), my headless precise amd-64 server persistently stops at the grub screen, requiring me to hit the "Enter" key to finish booting, then it loads the oldest kernel still on board (3.2.0-26), even though several newer are present:
```
$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

I have been going through a couple of grub 2 guides, and applied some edits to try and fix these problems:
[http://serverfault.com/questions/243343/headless-ubuntu-server-machine-sometimes-stuck-at-grub-menu /etc/grub.d/00_header]("http://serverfault.com/questions/243343/headless-ubuntu-server-machine-sometimes-stuck-at-grub-menu /etc/grub.d/00_header")

/etc/grub.d/00_header:
---
# make_timeout ()
# {
#    cat << EOF
# if [ "\${recordfail}" = 1 ]; then
#   set timeout=${GRUB_RECORDFAIL_TIMEOUT:--1}
# else
#   set timeout=${2}
# fi
# EOF
# }

make_timeout ()
{
    echo "set timeout=0"
}
---
[https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2]("https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2")

/etc/default/grub, added lines 36 & 37 to end:
---
# 101012 disable check for other [backup] os, which presence interrupts booting:
GRUB_DISABLE_OS_PROBER=true

---
sudo grub-set-default 0
---
this apparently modified /boot/grub/grubenv:
---
# GRUB Environment Block
saved_entry=0
##########
---------------

Can anyone suggest ways to troubleshoot/fix these issues (and yes, I re-ran sudo update-grub after applying the edits)?

Luckily the server is on site, what a headache this would be if it was remote. Not too happy with grub 2, assuming that is the issue.

Thanks!

---

### Post by dsmithhfx on 2012-10-10
After floundering around reconfiguring grub files for a couple of hours, I discovered a very useful tool: Boot Repair.

The best thing Boot Repair does is make a very detailed report of the complete environment, grub variables, disks and partitions.

Right up at the top I (eventually) noticed something very odd:
```
Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of the same hard drive for core.img. core.img is at this location and looks for (,msdos2)/boot/grub on this drive.
```

(,msdos2) points to /dev/sda2, my 'backup' partition, and thats the old grub.cfg it was reading for the old kernel. Luckily I had made no edits to that grub.cfg, because individual entries were still pointing back to my production OS on sda1 ((,msdos1) as the root.

I tested this by adding a new entry to /sda2/boot/grub/grub.cfg for the latest kernel, and sure enough that is what it rebooted into.

Something somehow had overwritten my MBR. Maybe it was fsarchiver, maybe it was "Grub Customizer", which I launched, inspected and then quit without making any changes (or so I thought).

At first I tried to repair the MBR (after backing it up), using the boot-repair gui app. However this wrote a 'generic' mbr, without grub. This seemed too far removed from the original boot configuration installed by Ubuntu, and I doubted it was going to work, leaving me with the prospect of essaying any further repairs from a live cd. Not pretty.

I did not want to use the boot-repair tool to "reinstall grub", thereby nuking my existing grub (which I had already restored to *almost* default state, with a couple of important differences), so I went by this guide [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) and ran the following commands:

```
$ grub-probe -t device /boot/grub
/dev/sda1
$ sudo grub-install /dev/sda
Installation finished. No error reported.
$ sudo grub-install --recheck /dev/sda
Installation finished. No error reported.
```

Running another boot-repair "BootInfo summary" confirmed that grub was now back on the mbr, and I was able to reboot into the right kernel without keyboard.

---

