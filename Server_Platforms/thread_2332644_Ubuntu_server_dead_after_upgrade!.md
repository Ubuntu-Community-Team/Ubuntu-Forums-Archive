---
title: "Ubuntu server dead after upgrade!"
date: 2016-08-02
forum: Server Platforms
---

### Post by orangetype on 2016-08-02
Please help, after upgrading to the latest Ubuntu server via the **do-release-upgrade** command the following happens at boot and I cannot get around it:

**Env:** Vmware server virtualized box

```

Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done. 
Begin: Running /scripts/local-premount ... done.
Begin: Will now check root file system ... fsck from util-linux 2.27.1 
[/sbin/fsck.ext4 (1) -- /dev/sda1] fsck.ext4 -a -C0 /dev/sda1
dev/sda1: recovering journal
fsck.ext4: symbol lookup error: fsck.ext4: undefined symbol: ext2fs_close_free 
fsck exited with status code 127
one.
Failure: File system check of the root filesystem failed
The root filesystem on /dev/sda1 requires a manual fsck
[ 8.6354961 hidraw: raw HID events driver (C) Jiri Kosina
[ 8.640970] usbcore: registered new interface driver usbhid
[ 8.642084] usbhid: USB HID core driver

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash) 
Enter 'help' for a list of built-in commands.

(initramfs) fsck /dev/sda1
fsck from util-linux 2.27.1 
e2fsck 1.42.13 (17-May-2015)
/dev/sda1: recovering journal
fsck.ext4: symbol lookup error: fsck.ext4: undefined symbol: ext2fs_close_free

```

---

### Post by orangetype on 2016-08-02
Does anyone know what to do? This is pretty urgent.

I was able to run **fsck -f -y /dev/sda1** but it outputs the following:

```

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 242535/602312 files (0.4% non-contiguous), 6492572/24117248 blocks
fsck.ext4: symbol lookup error: fsck.ext4: undefined symbol: ext2fs_close_free

```

---

### Post by darkod on 2016-08-02
Did you try to run fsck from live cd? Mount the iso as virtual cd in vmware and try that. You can even use 14.04 iso if you think 16.04 fsck is broken.

It might be a bug of some kind, but since you are in a hurry I would try both 16.04 and 14.04 desktop iso mounted as virtual cd. Boot it into live mode and run the 'sudo fsck /dev/sda1'.

---

### Post by orangetype on 2016-08-02
> **darkod said:**
> Did you try to run fsck from live cd? Mount the iso as virtual cd in vmware and try that. You can even use 14.04 iso if you think 16.04 fsck is broken.

It might be a bug of some kind, but since you are in a hurry I would try both 16.04 and 14.04 desktop iso mounted as virtual cd. Boot it into live mode and run the 'sudo fsck /dev/sda1'.
I ran fsck /dev/sda1 on both the 16.04 live cd and 14.04 live cd, and while they both completed without error I still cannot boot the machine.

---

### Post by darkod on 2016-08-02
1. Is the error on boot still the same as it was the first time after the upgrade?

2. Can you open the root shell? In the vmware VM console try to "catch" it while it shows the grub menu and select the recovery mode entry. That should open a small menu and one of the options should be "drop to root shell". That should open a read-only shell of the OS. Try to check if you can open it...

If you can, you could try checking the logs for more details of why it can't boot exactly...

If you can't open recovery mode too, you can use the live cd again and open the logs on sda1 to take a look.

I assume you don't have a snapshot of before the upgrade, otherwise you would have reverted to it already...

---

### Post by orangetype on 2016-08-02
OK something interesting: the Linux kernel 4 recovery mode does not work, but the previous version 3.4 (think) generic does let me in.

But now that I'm in which log should I look at? I am in /var/log and there are a lot of files, not entirely sure where I should be looking.

---

### Post by darkod on 2016-08-03
The main log file is syslog. I think there is a boot log too, so you can take a look. And also in dmesg.
Post and google any error messages you find, to give you more clues.

---

### Post by orangetype on 2016-08-03
Darkod, first: thanks a lot for your help. Here's where I'm at:

I was able to get into the server by booting the older kernel, which makes me think it's a kernel issue. I'm in the process of setting up a new server to migrate all the data over.

I've looked through the syslog but can't identify any errors, even the one in the original post doesn't appear. At this point I'm ready to give up on trying to restore this server.

---

### Post by darkod on 2016-08-03
What you can try is removing the latest kernel and then installing it again... I haven't actually tried that before (only removing kernels), but it should be something like:
```
sudo apt-get purge linux-image-4.4.0-xx-generic   (replace the xx with the exact kernel number that you have as latest)
sudo apt-get install linux-image-4.4.0-xx-generic
```

Something like that should reinstall the kernel, in case something got corrupted during the upgrade.

---

