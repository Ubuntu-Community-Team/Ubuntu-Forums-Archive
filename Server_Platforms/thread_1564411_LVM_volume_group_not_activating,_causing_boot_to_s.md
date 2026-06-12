---
title: "LVM volume group not activating, causing boot to stall"
date: 2010-08-30
forum: Server Platforms
---

### Post by dtfinch on 2010-08-30
I have a relatively new server (Ubuntu Server 10.04.1) with a "/backup" partition on top of LVM on top of an MD raid 1.

Everything generally works, except that it freezes during the fsck phase of bootup, with no errors. I've given it 20 minutes or so. If I press 's' to skip an unavailable mount (documented [here](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Changes%20in%20boot-time%20output%20on%20Ubuntu%20Server)), it reports that /backup could not be mounted.

There are no LVM related messages in /var/log/messages, syslog, or dmesg.

When I try to mount /backup manually, it reports that the device (/dev/vg0/store) does not exist. Apparently the volume group was never activated, though all documentation seems to claim it should happen automatically at boot. When I run "vgchange vg0 -a y", it activates the volume group with no issue, and then I can mount /backup.

/etc/lvm/lvm.conf is unchanged from the defaults. I've seen posts mentioning the existence of a /etc/udev/rules.d/85-lvm2.rules , but no such file exists on my server, and I'm not sure how I would go about creating it manually, or forcing udev to create one.

There are some open bugs describing similar problems, but surely it doesn't happen to everyone or there'd be many more:
[https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/147216](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/147216)
[https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/581214](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/581214)

I'm wondering if anyone knows of a workaround, or what I might be doing wrong.

In case it makes a difference, here are almost the exact steps I used to build the raid, setup LVM, and create /backup:```
apt-get install mdadm lvm2
mdadm --create /dev/md0 --level=raid1 --raid-devices=2 /dev/sdb1 /dev/sdc1
pvcreate /dev/md0
vgcreate -s 64M vg0 /dev/md0
lvcreate -l100%FREE -n store vg0
mkfs.ext4 -m 1 /dev/vg0/store
mkdir /backup
Added to /etc/fstab: /dev/vg0/store  /backup  ext4  defaults,noatime,barrier=1  0  0
mountall
```

---

### Post by dtfinch on 2010-08-30
My progress thus far:
[LIST]
[*]Changing /dev/vg0/store to /dev/mapper/vg0-store in fstab had no effect.
[*]Adding nobootwait to the mount options for /backup in fstab allowed booting to finish without freezing, but it still wouldn't automount once booted.
[*]Running "vgchange -ay vg0" alone from the command line after booting is sufficient for /backup to be automounted. No manual mount or mountall needed.
[*]Adding "/sbin/vgchange -ay vg0" alone to /etc/rc.local did not work. It could find the volume group at this stage of bootup, even after running vgscan. It seems /dev/md0 simply did not exist yet.
[*]Looking at dmesg output, I noticed that sdb and sdc were not detected until a full 20 seconds (exactly) after sda was. This is very suspicious, like some timeout is delaying detection by 20 seconds.
[/LIST]

My workaround for now is to add a 20 second delay to rc.local before attempting to activate the volume group, in addition to having nobootwait in the mount options:```
/bin/sleep 20
/sbin/vgscan
/sbin/vgchange -ay vg0
```

This is a very dirty solution, but it works for now. Ideally I'd like it to delay attempting to activate volume groups until /dev/md0 becomes available, and/or find what's causing the 20 second delay before it detects sdb/sdc. The server is a Dell PowerEdge R710.

---

### Post by sh1ny on 2010-08-31
Give the fsck more than 20 minutes. Or run it manually.

---

### Post by dtfinch on 2010-08-31
fsck was just the last thing on the screen, and there was zero disk activity. It was freezing in mountall, waiting for /dev/mapper/vg0-store to appear. /dev/mapper/vg0-store exists on top of /dev/md0, made up of /dev/sdb and /dev/sdc. After it detected /dev/sdb and /dev/sdc (20 seconds later), it created /dev/md0 (according to dmesg), but it never created /dev/mapper/vg0-store, despite that it's supposed to. The ugly workaround was to add nobootwait to fstab and have rc.local activate the volume group after a 20 second wait, which allows enough time for /dev/md0 to appear.

I feel that there's supposed to be some udev trigger to activate /dev/mapper/vg0-store, and that it would be defined in /etc/udev/rules.d/85-lvm2.rules, but I have no idea how to create that file manually, or why it wasn't created automatically.

---

### Post by sh1ny on 2010-08-31
When it stalls, did you try pressing "S" ?

---

### Post by dtfinch on 2010-08-31
This seems to be the proper fix:

Install watershed: (edit: this step appears unnecessary) ```
apt-get install chiark-utils-bin
```
Create /etc/udev/rules.d/85-lvm2.rules: ```
SUBSYSTEM=="block", ACTION=="add|change", RUN+="watershed sh -c '/sbin/lvm vgscan; /sbin/lvm vgchange -a y'"
```
Then update initramfs: ```
update-initramfs -u -k `uname -r`
```

It turned out there's a copy of the default 85-lvm2.rules in /lib/udev/rules.d/, but it didn't get installed automatically. Just copying it over wasn't sufficient though, because of [https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/147216](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/147216). I had to remove the 'ENV{ID_FS_TYPE}=="lvm*|LVM*"'.

---

