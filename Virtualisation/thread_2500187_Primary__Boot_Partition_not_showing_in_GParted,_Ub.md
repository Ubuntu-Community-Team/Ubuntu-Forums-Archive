---
title: "Primary / Boot Partition not showing in GParted, Ubuntu 24.04 VirtualBox"
date: 2024-08-25
forum: Virtualisation
---

### Post by jpk95 on 2024-08-25
Hi All,


I'm a beginner to VirtualBox and Ubuntu and I've been stuck on this problem all day, wondering if anyone can help.

I've installed and opened a new Ubuntu VM on my Windows 11 laptop, and have encountered what I think is a common problem of the "actual" disk space not being as much as the "virtual" disk space that I had specified during installation. I had set the disk space to about 90GB and I'm seeing a system volume of about 2GB.

I've looked at a few tutorials, all of which describe using GParted to resize the primary partition to include the currently unallocated disk space. The issue which I have is that when I open GParted no partitions show at all apart from the unallocated disk space. The partition containing the Ubuntu system folders is not there and so I can't resize it. See image below.


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294139&stc=1[/IMG]

I have managed to create a new partition table and a new partition (I just used the default ext4 for this?) but this shows in devices as a separate volume from the boot/system volume.

I need to install some software to the system folders and therefore have to increase the actual disk space of the system partition/volume, does anyone know how I can do this, or suggest why this partition is not showing in GParted?


Thanks!
John

---

### Post by &amp;KyT$0P# on 2024-08-25
> **jpk95 said:**
> I'm seeing a system volume of about 2GB.

Where are you seeing this?

> when I open GParted no partitions show at all apart from the unallocated disk space.

How did you install Ubuntu?

Please post the output from running these commands in Terminal from the installed Ubuntu system -
```
lsblk -o +PTTYPE,FSTYPE
findmnt | cat
```

---

### Post by jpk95 on 2024-08-26
Hi halogen2, thanks for the quick response,

So a small mistake in my first description, I'm seeing 104GB virtual and 2MB actual space in the storage settings of VirtualBox:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294142&stc=1[/IMG]

And 2GB system volume size here in "Other Locations":

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294143&stc=1[/IMG]

But seeing the full virtualdisk size in Disks:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294144&stc=1[/IMG]



I used the Ubuntu 24.04 LTS ISO image from the Ubuntu website and created a New VM with this image. That's all I did in terms of install.


Responses to the terminal commands:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294145&stc=1[/IMG]

```
ubuntu@ubuntu:~$ findmnt | cat
TARGET                                            SOURCE                    FSTYPE          OPTIONS
/                                                 /cow                      overlay         rw,relatime,lowerdir=/minimal.standard.live.squashfs:/minimal.standard.squashfs:/minimal.squashfs,upperdir=/cow/upper,workdir=/cow/work,uuid=on,xino=off,nouserxattr
&#9500;&#9472;/sys                                            sysfs                     sysfs           rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/kernel/security                          securityfs                securityfs      rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/fs/cgroup                                cgroup2                   cgroup2         rw,nosuid,nodev,noexec,relatime,nsdelegate,memory_recursiveprot
&#9474; &#9500;&#9472;/sys/fs/pstore                                pstore                    pstore          rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/fs/bpf                                   bpf                       bpf             rw,nosuid,nodev,noexec,relatime,mode=700
&#9474; &#9500;&#9472;/sys/kernel/tracing                           tracefs                   tracefs         rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/kernel/debug                             debugfs                   debugfs         rw,nosuid,nodev,noexec,relatime
&#9474; &#9500;&#9472;/sys/fs/fuse/connections                      fusectl                   fusectl         rw,nosuid,nodev,noexec,relatime
&#9474; &#9492;&#9472;/sys/kernel/config                            configfs                  configfs        rw,nosuid,nodev,noexec,relatime
&#9500;&#9472;/proc                                           proc                      proc            rw,nosuid,nodev,noexec,relatime
&#9474; &#9492;&#9472;/proc/sys/fs/binfmt_misc                      systemd-1                 autofs          rw,relatime,fd=32,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=2683
&#9474;   &#9492;&#9472;/proc/sys/fs/binfmt_misc                    binfmt_misc               binfmt_misc     rw,nosuid,nodev,noexec,relatime
&#9500;&#9472;/dev                                            udev                      devtmpfs        rw,nosuid,relatime,size=1964864k,nr_inodes=491216,mode=755,inode64
&#9474; &#9500;&#9472;/dev/pts                                      devpts                    devpts          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
&#9474; &#9500;&#9472;/dev/shm                                      tmpfs                     tmpfs           rw,nosuid,nodev,inode64
&#9474; &#9500;&#9472;/dev/hugepages                                hugetlbfs                 hugetlbfs       rw,nosuid,nodev,relatime,pagesize=2M
&#9474; &#9492;&#9472;/dev/mqueue                                   mqueue                    mqueue          rw,nosuid,nodev,noexec,relatime
&#9500;&#9472;/run                                            tmpfs                     tmpfs           rw,nosuid,nodev,noexec,relatime,size=401016k,mode=755,inode64
&#9474; &#9500;&#9472;/run/lock                                     tmpfs                     tmpfs           rw,nosuid,nodev,noexec,relatime,size=5120k,inode64
&#9474; &#9500;&#9472;/run/user/1000                                tmpfs                     tmpfs           rw,nosuid,nodev,relatime,size=401012k,nr_inodes=100253,mode=700,uid=1000,gid=1000,inode64
&#9474; &#9474; &#9500;&#9472;/run/user/1000/gvfs                         gvfsd-fuse                fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1000
&#9474; &#9474; &#9492;&#9472;/run/user/1000/doc                          portal                    fuse.portal     rw,nosuid,nodev,relatime,user_id=1000,group_id=1000
&#9474; &#9492;&#9472;/run/snapd/ns                                 tmpfs[/snapd/ns]          tmpfs           rw,nosuid,nodev,noexec,relatime,size=401016k,mode=755,inode64
&#9474;   &#9500;&#9472;/run/snapd/ns/firefox.mnt                   nsfs[mnt:[4026532452]]    nsfs            rw
&#9474;   &#9500;&#9472;/run/snapd/ns/firmware-updater.mnt          nsfs[mnt:[4026532513]]    nsfs            rw
&#9474;   &#9500;&#9472;/run/snapd/ns/snap-store.mnt                nsfs[mnt:[4026532514]]    nsfs            rw
&#9474;   &#9500;&#9472;/run/snapd/ns/snapd-desktop-integration.mnt nsfs[mnt:[4026532515]]    nsfs            rw
&#9474;   &#9492;&#9472;/run/snapd/ns/thunderbird.mnt               nsfs[mnt:[4026532519]]    nsfs            rw
&#9500;&#9472;/cdrom                                          /dev/sr0                  iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8
&#9500;&#9472;/rofs                                           /dev/loop0                squashfs        ro,noatime,errors=continue,threads=single
&#9500;&#9472;/tmp                                            tmpfs                     tmpfs           rw,nosuid,nodev,relatime,inode64
&#9500;&#9472;/snap/bare/5                                    /dev/loop3                squashfs        ro,nodev,relatime,errors=continue,threads=single
&#9500;&#9472;/snap/firefox/4173                              /dev/loop5                squashfs        ro,nodev,relatime,errors=continue,threads=single
&#9500;&#9472;/snap/firmware-updater/127                      /dev/loop7                squashfs        ro,nodev,relatime,errors=continue,threads=single
&#9500;&#9472;/snap/core22/1380                               /dev/loop4                squashfs        ro,nodev,relatime,errors=continue,threads=single
&#9500;&#9472;/snap/gnome-42-2204/176                         /dev/loop6                squashfs        ro,nodev,relatime,errors=continue,threads=single
&#9500;&#9472;/snap/snap-store/1124                           /dev/loop11               squashfs        ro,nodev,relatime,errors=continue,threads=single
&#9500;&#9472;/snap/snapd-desktop-integration/157             /dev/loop10               squashfs        ro,nodev,relatime,errors=continue,threads=single
&#9500;&#9472;/snap/ubuntu-desktop-bootstrap/171              /dev/loop12               squashfs        ro,nodev,relatime,errors=continue,threads=single
&#9500;&#9472;/snap/thunderbird/470                           /dev/loop13               squashfs        ro,nodev,relatime,errors=continue,threads=single
&#9500;&#9472;/snap/snapd/21465                               /dev/loop9                squashfs        ro,nodev,relatime,errors=continue,threads=single
&#9500;&#9472;/snap/gtk-common-themes/1535                    /dev/loop8                squashfs        ro,nodev,relatime,errors=continue,threads=single
&#9492;&#9472;/var/snap/firefox/common/host-hunspell          /cow[/usr/share/hunspell] overlay         ro,noexec,noatime,lowerdir=/minimal.standard.live.squashfs:/minimal.standard.squashfs:/minimal.squashfs,upperdir=/cow/upper,workdir=/cow/work,uuid=on,xino=off,nouserxattr

```

---

### Post by &amp;KyT$0P# on 2024-08-26
That looks like the "Try Ubuntu" live CD environment and looks like Ubuntu was never actually installed.

---

### Post by jpk95 on 2024-08-26
Sorted! I had been clicking "Try Ubuntu" rather than installing as I had seen this in tutorials, but the full install was needed. Rookie Error.

Thanks very much

---

