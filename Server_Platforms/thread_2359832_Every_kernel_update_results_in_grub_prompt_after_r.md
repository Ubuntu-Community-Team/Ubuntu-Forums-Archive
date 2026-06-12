---
title: "Every kernel update results in grub prompt after reboot"
date: 2017-04-28
forum: Server Platforms
---

### Post by DigiAngel on 2017-04-28
Topic...never had this issue before...I can boot from grub> by specifying linux and initrd locations, but for the life of me I'm not sure why this is happening.  My /boot/grub dir looks fine and has everything when I compare to other machines...grub.cfg looks fine as near as I can tell.  Is there a way to troubleshoot this?  Thank you.

---

### Post by ajgreeny on 2017-04-28
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may suggest any appropriate grub changes that may be needed.

---

### Post by DigiAngel on 2017-04-28
Thanks...however this is ubuntu server :(

---

### Post by ajgreeny on 2017-04-28
You can still run the boot-info script from a live system if you wish.

---

### Post by DigiAngel on 2017-05-03
Thanks...however this a remote machine with only KVM and ssh access.  Currently it's running and rebooting just fine, it's only when I do a apt-get dist-upgrade and the kernel is updated to I have this issue.

---

### Post by DigiAngel on 2017-05-30
Well another month another boot to grub.  Here's the entire process after apt-get dist-upgrade:
```
Fetched 123 MB in 1min 26s (1,416 kB/s)
Preconfiguring packages ...
(Reading database ... 108828 files and directories currently installed.)
Preparing to unpack .../openssh-sftp-server_1%3a7.2p2-4ubuntu2.2_amd64.deb ...
Unpacking openssh-sftp-server (1:7.2p2-4ubuntu2.2) over (1:7.2p2-4ubuntu2.1) ...
Preparing to unpack .../zlib1g-dev_1%3a1.2.8.dfsg-2ubuntu4.1_amd64.deb ...
Unpacking zlib1g-dev:amd64 (1:1.2.8.dfsg-2ubuntu4.1) over (1:1.2.8.dfsg-2ubuntu4) ...
Preparing to unpack .../zlib1g_1%3a1.2.8.dfsg-2ubuntu4.1_amd64.deb ...
Unpacking zlib1g:amd64 (1:1.2.8.dfsg-2ubuntu4.1) over (1:1.2.8.dfsg-2ubuntu4) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Setting up zlib1g:amd64 (1:1.2.8.dfsg-2ubuntu4.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
(Reading database ... 108828 files and directories currently installed.)
Preparing to unpack .../openssh-server_1%3a7.2p2-4ubuntu2.2_amd64.deb ...
Unpacking openssh-server (1:7.2p2-4ubuntu2.2) over (1:7.2p2-4ubuntu2.1) ...
Preparing to unpack .../openssh-client_1%3a7.2p2-4ubuntu2.2_amd64.deb ...
Unpacking openssh-client (1:7.2p2-4ubuntu2.2) over (1:7.2p2-4ubuntu2.1) ...
Preparing to unpack .../ubuntu-core-launcher_2.25_amd64.deb ...
Unpacking ubuntu-core-launcher (2.25) over (2.24.1) ...
Preparing to unpack .../archives/snapd_2.25_amd64.deb ...
Warning: Stopping snapd.service, but it can still be activated by:
  snapd.socket
Unpacking snapd (2.25) over (2.24.1) ...
Preparing to unpack .../iproute2_4.3.0-1ubuntu3.16.04.1_amd64.deb ...
Unpacking iproute2 (4.3.0-1ubuntu3.16.04.1) over (4.3.0-1ubuntu3) ...
Preparing to unpack .../logrotate_3.8.7-2ubuntu2.16.04.1_amd64.deb ...
Unpacking logrotate (3.8.7-2ubuntu2.16.04.1) over (3.8.7-2ubuntu2) ...
Preparing to unpack .../sudo_1.8.16-0ubuntu1.4_amd64.deb ...
Unpacking sudo (1.8.16-0ubuntu1.4) over (1.8.16-0ubuntu1.3) ...
Preparing to unpack .../python3-problem-report_2.20.1-0ubuntu2.6_all.deb ...
Unpacking python3-problem-report (2.20.1-0ubuntu2.6) over (2.20.1-0ubuntu2.5) ...
Preparing to unpack .../python3-apport_2.20.1-0ubuntu2.6_all.deb ...
Unpacking python3-apport (2.20.1-0ubuntu2.6) over (2.20.1-0ubuntu2.5) ...
Preparing to unpack .../apport_2.20.1-0ubuntu2.6_all.deb ...
Unpacking apport (2.20.1-0ubuntu2.6) over (2.20.1-0ubuntu2.5) ...
Preparing to unpack .../linux-firmware_1.157.10_all.deb ...
Unpacking linux-firmware (1.157.10) over (1.157.8) ...
Selecting previously unselected package linux-image-4.8.0-53-generic.
Preparing to unpack .../linux-image-4.8.0-53-generic_4.8.0-53.56~16.04.1_amd64.deb ...
Done.
Unpacking linux-image-4.8.0-53-generic (4.8.0-53.56~16.04.1) ...
Selecting previously unselected package linux-image-extra-4.8.0-53-generic.
Preparing to unpack .../linux-image-extra-4.8.0-53-generic_4.8.0-53.56~16.04.1_amd64.deb ...
Unpacking linux-image-extra-4.8.0-53-generic (4.8.0-53.56~16.04.1) ...
Preparing to unpack .../linux-generic-hwe-16.04_4.8.0.53.24_amd64.deb ...
Unpacking linux-generic-hwe-16.04 (4.8.0.53.24) over (4.8.0.52.23) ...
Preparing to unpack .../linux-image-generic-hwe-16.04_4.8.0.53.24_amd64.deb ...
Unpacking linux-image-generic-hwe-16.04 (4.8.0.53.24) over (4.8.0.52.23) ...
Selecting previously unselected package linux-headers-4.8.0-53.
Preparing to unpack .../linux-headers-4.8.0-53_4.8.0-53.56~16.04.1_all.deb ...
Unpacking linux-headers-4.8.0-53 (4.8.0-53.56~16.04.1) ...
Selecting previously unselected package linux-headers-4.8.0-53-generic.
Preparing to unpack .../linux-headers-4.8.0-53-generic_4.8.0-53.56~16.04.1_amd64.deb ...
Unpacking linux-headers-4.8.0-53-generic (4.8.0-53.56~16.04.1) ...
Preparing to unpack .../linux-headers-generic-hwe-16.04_4.8.0.53.24_amd64.deb ...
Unpacking linux-headers-generic-hwe-16.04 (4.8.0.53.24) over (4.8.0.52.23) ...
Preparing to unpack .../software-properties-common_0.96.20.7_all.deb ...
Unpacking software-properties-common (0.96.20.7) over (0.96.20.6) ...
Preparing to unpack .../python3-software-properties_0.96.20.7_all.deb ...
Unpacking python3-software-properties (0.96.20.7) over (0.96.20.6) ...
Preparing to unpack .../sosreport_3.4-1~ubuntu16.04.1_amd64.deb ...
Unpacking sosreport (3.4-1~ubuntu16.04.1) over (3.2+git276-g7da50d6-3ubuntu1) ...
Preparing to unpack .../unattended-upgrades_0.90ubuntu0.6_all.deb ...
Unpacking unattended-upgrades (0.90ubuntu0.6) over (0.90ubuntu0.3) ...
Preparing to unpack .../cloud-initramfs-copymods_0.27ubuntu1.4_all.deb ...
Unpacking cloud-initramfs-copymods (0.27ubuntu1.4) over (0.27ubuntu1.3) ...
Preparing to unpack .../cloud-initramfs-dyn-netconf_0.27ubuntu1.4_all.deb ...
Unpacking cloud-initramfs-dyn-netconf (0.27ubuntu1.4) over (0.27ubuntu1.3) ...
Preparing to unpack .../grub-legacy-ec2_0.7.9-113-g513e99e0-0ubuntu1~16.04.1_all.deb ...
Leaving 'diversion of /usr/sbin/grub-set-default to /usr/sbin/grub-set-default.real by grub-legacy-ec2'
Unpacking grub-legacy-ec2 (0.7.9-113-g513e99e0-0ubuntu1~16.04.1) over (0.7.9-90-g61eb03fe-0ubuntu1~16.04.1) ...
Preparing to unpack .../overlayroot_0.27ubuntu1.4_all.deb ...
Unpacking overlayroot (0.27ubuntu1.4) over (0.27ubuntu1.3) ...
Processing triggers for systemd (229-4ubuntu17) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Setting up openssh-client (1:7.2p2-4ubuntu2.2) ...
Setting up openssh-sftp-server (1:7.2p2-4ubuntu2.2) ...
Setting up zlib1g-dev:amd64 (1:1.2.8.dfsg-2ubuntu4.1) ...
Setting up openssh-server (1:7.2p2-4ubuntu2.2) ...
Setting up snapd (2.25) ...
Installing new version of config file /etc/apparmor.d/usr.lib.snapd.snap-confine.real ...
Setting up ubuntu-core-launcher (2.25) ...
Setting up iproute2 (4.3.0-1ubuntu3.16.04.1) ...
Setting up logrotate (3.8.7-2ubuntu2.16.04.1) ...
Setting up sudo (1.8.16-0ubuntu1.4) ...
Setting up python3-problem-report (2.20.1-0ubuntu2.6) ...
Setting up python3-apport (2.20.1-0ubuntu2.6) ...
Setting up apport (2.20.1-0ubuntu2.6) ...
Setting up linux-firmware (1.157.10) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-52-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-4.8.0-49-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
Setting up linux-image-4.8.0-53-generic (4.8.0-53.56~16.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-53-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-53-generic
Found initrd image: /boot/initrd.img-4.8.0-53-generic
Found linux image: /boot/vmlinuz-4.8.0-52-generic
Found initrd image: /boot/initrd.img-4.8.0-52-generic
Found linux image: /boot/vmlinuz-4.8.0-49-generic
Found initrd image: /boot/initrd.img-4.8.0-49-generic
done
Setting up linux-image-extra-4.8.0-53-generic (4.8.0-53.56~16.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-53-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-53-generic /boot/vmlinuz-4.8.0-53-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-53-generic
Found initrd image: /boot/initrd.img-4.8.0-53-generic
Found linux image: /boot/vmlinuz-4.8.0-52-generic
Found initrd image: /boot/initrd.img-4.8.0-52-generic
Found linux image: /boot/vmlinuz-4.8.0-49-generic
Found initrd image: /boot/initrd.img-4.8.0-49-generic
done
Setting up linux-image-generic-hwe-16.04 (4.8.0.53.24) ...
Setting up linux-headers-4.8.0-53 (4.8.0-53.56~16.04.1) ...
Setting up linux-headers-4.8.0-53-generic (4.8.0-53.56~16.04.1) ...
Setting up linux-headers-generic-hwe-16.04 (4.8.0.53.24) ...
Setting up linux-generic-hwe-16.04 (4.8.0.53.24) ...
Setting up python3-software-properties (0.96.20.7) ...
Setting up software-properties-common (0.96.20.7) ...
Setting up sosreport (3.4-1~ubuntu16.04.1) ...
Setting up unattended-upgrades (0.90ubuntu0.6) ...
Installing new version of config file /etc/init.d/unattended-upgrades ...
Replacing config file /etc/apt/apt.conf.d/50unattended-upgrades with new version
Synchronizing state of unattended-upgrades.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install enable unattended-upgrades
Setting up cloud-initramfs-copymods (0.27ubuntu1.4) ...
Setting up cloud-initramfs-dyn-netconf (0.27ubuntu1.4) ...
Setting up grub-legacy-ec2 (0.7.9-113-g513e99e0-0ubuntu1~16.04.1) ...
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-4.8.0-49-generic
Found kernel: /boot/vmlinuz-4.8.0-46-generic
Found kernel: /boot/vmlinuz-4.8.0-45-generic
Found kernel: /boot/vmlinuz-4.8.0-41-generic
Replacing config file /run/grub/menu.lst with new version
Found kernel: /boot/vmlinuz-4.8.0-53-generic
Found kernel: /boot/vmlinuz-4.8.0-52-generic
Found kernel: /boot/vmlinuz-4.8.0-49-generic
Replacing config file /run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Setting up overlayroot (0.27ubuntu1.4) ...
Processing triggers for systemd (229-4ubuntu17) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-53-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
```

after a reboot I see the grub> prompt.  Typing set gives me:
```
set shows
prefix=(hd0,gpt2)/boot/grub
root=hd0,gpt2
```

I have to type in:
```
linux (hd0,gpt2)/boot/vmlinuz-4.8.0-53 root=/dev/sda2 ro
initrd (hd0,gpt2)/boot/initrd.img-4.8.0-53
```

And then ir boots fine for that round.  Can someone explain why this is happening and what I can do?  This is a remote machine, so I can't do much besides use a KVM.  Thank you

---

### Post by DigiAngel on 2017-05-31
And bootinfo.txt:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 2048
    of the same hard drive for core.img. core.img is at this location and
    looks in partition 97 for .

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 16.04.2 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 3.3 TiB, 3598914158592 bytes, 7029129216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048         4,095         2,048 BIOS Boot partition
/dev/sda2           4,096 3,740,989,439 3,740,985,344 Data partition (Linux)
/dev/sda3   3,740,989,440 3,807,901,695    66,912,256 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1
/dev/sda2        21ca1c74-a4d8-45be-b955-7cb5af07af32   ext4
/dev/sda3        cba5aaba-4491-4bd0-8f3a-c6cebccb2f6f   swap

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)


=========================== sda2/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
# on ec2, with no console access, there is no reason for a timeout.  set to 0.
timeout         0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro

## default grub root device
## e.g. groot=(hd0)
# groot=(hd0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=console=hvc0

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=true

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 16.04.2 LTS, kernel 4.8.0-53-generic
root            (hd0)
kernel          /boot/vmlinuz-4.8.0-53-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro console=hvc0
initrd          /boot/initrd.img-4.8.0-53-generic

title           Ubuntu 16.04.2 LTS, kernel 4.8.0-53-generic (recovery mode)
root            (hd0)
kernel          /boot/vmlinuz-4.8.0-53-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro  single
initrd          /boot/initrd.img-4.8.0-53-generic

title           Ubuntu 16.04.2 LTS, kernel 4.8.0-52-generic
root            (hd0)
kernel          /boot/vmlinuz-4.8.0-52-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro console=hvc0
initrd          /boot/initrd.img-4.8.0-52-generic

title           Ubuntu 16.04.2 LTS, kernel 4.8.0-52-generic (recovery mode)
root            (hd0)
kernel          /boot/vmlinuz-4.8.0-52-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro  single
initrd          /boot/initrd.img-4.8.0-52-generic

title           Ubuntu 16.04.2 LTS, kernel 4.8.0-49-generic
root            (hd0)
kernel          /boot/vmlinuz-4.8.0-49-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro console=hvc0
initrd          /boot/initrd.img-4.8.0-49-generic

title           Ubuntu 16.04.2 LTS, kernel 4.8.0-49-generic (recovery mode)
root            (hd0)
kernel          /boot/vmlinuz-4.8.0-49-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro  single
initrd          /boot/initrd.img-4.8.0-49-generic

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  21ca1c74-a4d8-45be-b955-7cb5af07af32
else
  search --no-floppy --fs-uuid --set=root 21ca1c74-a4d8-45be-b955-7cb5af07af32
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=2
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=2
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
        set gfxpayload="${1}"
        if [ "${1}" = "keep" ]; then
                set vt_handoff=vt.handoff=7
        else
                set vt_handoff=
        fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-21ca1c74-a4d8-45be-b955-7cb5af07af32' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  21ca1c74-a4d8-45be-b955-7cb5af07af32
        else
          search --no-floppy --fs-uuid --set=root 21ca1c74-a4d8-45be-b955-7cb5af07af32
        fi
        linux   /boot/vmlinuz-4.8.0-53-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro
        initrd  /boot/initrd.img-4.8.0-53-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-21ca1c74-a4d8-45be-b955-7cb5af07af32' {
        menuentry 'Ubuntu, with Linux 4.8.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-53-generic-advanced-21ca1c74-a4d8-45be-b955-7cb5af07af32' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  21ca1c74-a4d8-45be-b955-7cb5af07af32
                else
                  search --no-floppy --fs-uuid --set=root 21ca1c74-a4d8-45be-b955-7cb5af07af32
                fi
                echo    'Loading Linux 4.8.0-53-generic ...'
                linux   /boot/vmlinuz-4.8.0-53-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.8.0-53-generic
        }
        menuentry 'Ubuntu, with Linux 4.8.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-53-generic-recovery-21ca1c74-a4d8-45be-b955-7cb5af07af32' {
                recordfail
                load_video
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  21ca1c74-a4d8-45be-b955-7cb5af07af32
                else
                  search --no-floppy --fs-uuid --set=root 21ca1c74-a4d8-45be-b955-7cb5af07af32
                fi
                echo    'Loading Linux 4.8.0-53-generic ...'
                linux   /boot/vmlinuz-4.8.0-53-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro recovery nomodeset
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.8.0-53-generic
        }
        menuentry 'Ubuntu, with Linux 4.8.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-52-generic-advanced-21ca1c74-a4d8-45be-b955-7cb5af07af32' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  21ca1c74-a4d8-45be-b955-7cb5af07af32
                else
                  search --no-floppy --fs-uuid --set=root 21ca1c74-a4d8-45be-b955-7cb5af07af32
                fi
                echo    'Loading Linux 4.8.0-52-generic ...'
                linux   /boot/vmlinuz-4.8.0-52-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.8.0-52-generic
        }
        menuentry 'Ubuntu, with Linux 4.8.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-52-generic-recovery-21ca1c74-a4d8-45be-b955-7cb5af07af32' {
                recordfail
                load_video
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  21ca1c74-a4d8-45be-b955-7cb5af07af32
                else
                  search --no-floppy --fs-uuid --set=root 21ca1c74-a4d8-45be-b955-7cb5af07af32
                fi
                echo    'Loading Linux 4.8.0-52-generic ...'
                linux   /boot/vmlinuz-4.8.0-52-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro recovery nomodeset
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.8.0-52-generic
        }
        menuentry 'Ubuntu, with Linux 4.8.0-49-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-49-generic-advanced-21ca1c74-a4d8-45be-b955-7cb5af07af32' {
                recordfail
                load_video
                gfxmode $linux_gfx_mode
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  21ca1c74-a4d8-45be-b955-7cb5af07af32
                else
                  search --no-floppy --fs-uuid --set=root 21ca1c74-a4d8-45be-b955-7cb5af07af32
                fi
                echo    'Loading Linux 4.8.0-49-generic ...'
                linux   /boot/vmlinuz-4.8.0-49-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.8.0-49-generic
        }
        menuentry 'Ubuntu, with Linux 4.8.0-49-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-49-generic-recovery-21ca1c74-a4d8-45be-b955-7cb5af07af32' {
                recordfail
                load_video
                insmod gzio
                if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
                insmod part_gpt
                insmod ext2
                set root='hd0,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  21ca1c74-a4d8-45be-b955-7cb5af07af32
                else
                  search --no-floppy --fs-uuid --set=root 21ca1c74-a4d8-45be-b955-7cb5af07af32
                fi
                echo    'Loading Linux 4.8.0-49-generic ...'
                linux   /boot/vmlinuz-4.8.0-49-generic root=UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 ro recovery nomodeset
                echo    'Loading initial ramdisk ...'
                initrd  /boot/initrd.img-4.8.0-49-generic
        }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=21ca1c74-a4d8-45be-b955-7cb5af07af32 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=cba5aaba-4491-4bd0-8f3a-c6cebccb2f6f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-BohKjytO/Tmp_Log: No such file or directory
mdadm: No arrays found in config file or automatically

```

---

### Post by oldfred on 2017-05-31
I do not know servers.

But can you boot from this line?
 configfile (hd0,2)/boot/grub/grub.cfg 

Or the links to most current kernel in /?

 set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/initrd.img
boot 


You also have a very large / (root).
Years ago there was a bug with 1 & 2TB drives where grub files or kernels located over about 500GB on drive had same issue, but they fixed that.
But maybe not with multiple TB drives?

Better to post link as then we can see full report. Forum restricts sizes of data you can post.
Part of report would be this from mine in /var/log/boot-sav/log which shows all the boot file locations on drive:

```
=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  62.600513458 = 67.216789504   boot/grub/grub.cfg                             1
  63.779720306 = 68.482953216   boot/vmlinuz-4.4.0-75-generic                  1
....

```

---

