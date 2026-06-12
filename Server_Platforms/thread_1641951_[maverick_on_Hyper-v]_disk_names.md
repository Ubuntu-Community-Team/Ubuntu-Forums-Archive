---
title: "[maverick on Hyper-v] disk names"
date: 2010-12-09
forum: Server Platforms
---

### Post by jihostyle on 2010-12-09
Hi, I'm experimenting with Hyper-v + Ubuntu and ran into quite a few problems focused around the disk drivers(hv_storvsc I think)

The HDD's at install are /dev/sd* but if you load the hyper-v drivers after installation all drives change to /dev/hd* which I'm guessing is the root of all my problems.

At first, I tried installing with LVM which worked but I kept getting a 

```
udevd-work[115]: inotify_add_watch(6, /dev/hda5, 10) failed: No such file or directory
```

which I failed to find out it's meaning.

I also noticed LVM saying there is a duplicate PV

```
root@absolute:/home/hoya# pvdisplay
**  Found duplicate PV Qwb2C0C9NDX8H2EnzSm317KS6rmkly3f: using /dev/sda5 not /dev/hda5**
  --- Physical volume ---
  PV Name               **/dev/sda5**
  VG Name               vg
  PV Size               126.76 GiB / not usable 4.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              32449
  Free PE               0
  Allocated PE          32449
  PV UUID               Qwb2C0-C9ND-X8H2-EnzS-m317-KS6r-mkly3f
```

which I tried to correct using pvchange -u with no luck.
the PV Name says it's /dev/sda5 even though the hyper-v drivers changed that to /dev/hda5. I get a similar message from os-prober.

```
root@absolute:/home/hoya# os-prober
  Found duplicate PV Qwb2C0C9NDX8H2EnzSm317KS6rmkly3f: using /dev/sda5 not /dev/hda5
```



After struggling with the LVM configuration, I created a new VM this time without LVM.

I loaded the hyper-v drivers and everything looked great until I hit _apt-get update_ and _apt-get upgrade_.
The upgrade failed the my root partition was remounted as readonly. 

```

root@cardi:/home/hoya# apt-get upgrade
[...]
Setting up udev (162-2.1) ...
mknod: `/lib/udev/devices/ppp': Invalid argument
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
[...]
```

and something from syslog
```
Dec 10 09:44:01 cardi kernel: [  181.007078] EXT4-fs error (device hda3): ext4_free_inode: bit already cleared for inode 129497
Dec 10 09:44:01 cardi kernel: [  181.010305] Aborting journal on device hda3-8.
Dec 10 09:44:01 cardi kernel: [  181.014399] EXT4-fs (hda3): Remounting filesystem read-only
Dec 10 09:44:01 cardi kernel: [  181.017119] EXT4-fs error (device hda3) in ext4_delete_inode: IO failure
```

And this time os-prober returns

```
/dev/sda3:Ubuntu 10.10 (10.10):Ubuntu:linux
```

but this got me confused because after I loaded the hyper-v modules /dev/sda3 ==> changed to ==> /dev/hda3. 

Because fstab is configured with UUIDs I thought sd* and hd* shouldn't be a big deal but it seems like I'm missing something.

The only way I could get everything working smoothly is when I configure the VM **without** lvm and update the system **before **I load the hyper-v drivers. But this still makes me nervous because of the thought that the VM might break the next time I upgrade the kernel.

Anyone with experience on this matter?
Thanks in advance.

---

### Post by evvvk1 on 2010-12-31
Hello,
 
I'm seeing the same issues. I got "apt-get upgrade" working, sort of, with these settings
 
/etc/default/grub:
GRUB_CMDLINE_LINUX="ide0=noprobe ide1=noprobe hda=noprobe hdb=noprobe"
GRUB_DISABLE_LINUX_UUID=true
 
Then run
# update-grub
 
Also I did the upgrade in smaller parts, first udev and libudev0:
# apt-get install udev libudev0
 
Then the rest or the upgrade. Still, during upgrade I saw the EXT4-fs error. But this time during next boot the system was able to recover and boot.
 
I think the solution should be to either disable hda or sda, because these map to the same physical disc. I don't know how to do this reliably, the noprobe parameters only do this partially.
 
The other solution is to completely disable the dynamic mount by UUID features, and statically map root to /dev/sda1 or /dev/hda1. 
 
What seems to happen is that during upgrade there's some script that mounts /dev/hda1 while /dev/sda1 is already mounted. The system does not handle this dual access nicely, reports EXT4-fs errors and almost corrupts the root filesystem.
 
Regards,

---

### Post by aok on 2011-01-11
I just dealt with this exact issue.

The key seems to be to replace all instances of /dev/sda with /dev/hda in/etc/mtab (not sure if /etc/fstab needs to be touched, especially if using UUIDs).

Then when you type "mount" it should show /dev/hda1 instead of /dev/sda1.

Then 'apt-get -u install udev libudev0 libuuid1 mount'

(I'm not actually sure if you need to do all those packages or not).

Then I reboot and run the rest of the apt-get upgrade.

I'm not sure if you have to do this every time there is a udev package update, but I would suggest taking a quick vm snapshot before doing it just in case.

---

### Post by kkm! on 2011-03-27
Exclude /dev/hd[0-9] from being scanned by lvm explicitly by changing filter in /etc/lvm/lvm.conf. If you need no other exclusions, use

[FONT="Courier New"]filter = [ "r/hda[1-9]$/" ][/FONT]

That took care of the warning for me.

---

