---
title: "Slow boot up on Ubuntu Server 18.04 LTS (alternative ISO)"
date: 2018-06-07
forum: Server Platforms
---

### Post by LHammonds on 2018-06-07
There is a 30 second delay on I do not know how to isolate to find out what is timing out.

**EDIT:** Might be related to this bug report: [getrandom hang in early boot]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=897572")

Here is how long it takes to boot a fresh 16.04 system on my VMware host:
```
# systemd-analyze time
Startup finished in 14.976s (kernel) + 7.405s (userspace) = 22.382s
```
Here is how long a fresh server on 18.04 takes to boot in the same environment:
```
# systemd-analyze time
Startup finished in 39.193s (kernel) + 14.484s (userspace) = 53.678s
graphical.target reached after 13.495s in userspace
```

The server was installed using the "alternative" ISO using LVM on a 35 GB (virtual) hard drive.

Server Info:
```
# uname -a
Linux ubuntumaster 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04 LTS
Release:        18.04
Codename:       bionic
```

```
Device     Boot  Start      End  Sectors  Size Id Type
/dev/sda1  *      2048   976895   974848  476M 83 Linux
/dev/sda2       978942 62912511 61933570 29.5G  5 Extended
/dev/sda5       978944 62912511 61933568 29.5G 8e Linux LVM
```

```
# lvscan
  ACTIVE            '/dev/LVG/root' [3.00 GiB] inherit
  ACTIVE            '/dev/LVG/usr' [4.00 GiB] inherit
  ACTIVE            '/dev/LVG/var' [3.00 GiB] inherit
  ACTIVE            '/dev/LVG/tmp' [2.00 GiB] inherit
  ACTIVE            '/dev/LVG/bak' [4.00 GiB] inherit
  ACTIVE            '/dev/LVG/srv' [2.00 GiB] inherit
  ACTIVE            '/dev/LVG/opt' [2.00 GiB] inherit
  ACTIVE            '/dev/LVG/home' [1.00 GiB] inherit
```

I did have a swap partition in the LVM but removed it and setup a file-based swap but that made no difference in the 30-second delay.  I also removed swap entirely at one point and it still made no difference.

/etc/fstab
```
/dev/mapper/LVG-root /               ext4    errors=remount-ro 0       1
/dev/mapper/LVG-bak /bak            ext4    defaults        0       2
# /boot was on /dev/sda1 during installation
UUID=3b677ff8-5cc0-4060-ae1a-a6e747b5ba59 /boot           ext2    defaults        0       2
/dev/mapper/LVG-home /home           ext4    defaults        0       2
/dev/mapper/LVG-opt /opt            ext4    defaults        0       2
/dev/mapper/LVG-srv /srv            ext4    defaults        0       2
/dev/mapper/LVG-tmp /tmp            ext4    defaults        0       2
/dev/mapper/LVG-usr /usr            ext4    defaults        0       2
/dev/mapper/LVG-var /var            ext4    defaults        0       2
/opt/swapfile1  swap    swap    defaults        0       0
```

```
# blkid
/dev/sda1: LABEL="boot" UUID="3b677ff8-5cc0-4060-ae1a-a6e747b5ba59" TYPE="ext2" PARTUUID="71358db0-01"
/dev/sda5: UUID="1NauKl-lWE2-4S5q-xItw-DNfr-drHF-ewSa6Z" TYPE="LVM2_member" PARTUUID="71358db0-05"
/dev/mapper/LVG-root: LABEL="root" UUID="741e4f1a-13d1-429d-bfe0-4cfac273d90d" TYPE="ext4"
/dev/mapper/LVG-usr: LABEL="usr" UUID="da600959-52b2-401d-a603-427fc0014ddb" TYPE="ext4"
/dev/mapper/LVG-var: LABEL="var" UUID="cfd56e89-5ddb-45db-a05d-098d9cded2c8" TYPE="ext4"
/dev/mapper/LVG-tmp: LABEL="tmp" UUID="35234e64-d459-4f86-8742-424d13cf3e41" TYPE="ext4"
/dev/mapper/LVG-bak: LABEL="bak" UUID="3a87e7e9-1b43-4507-a236-8729de2a4bcc" TYPE="ext4"
/dev/mapper/LVG-srv: LABEL="srv" UUID="cc3d6a7c-ae05-4e00-83ff-49d5e65c354f" TYPE="ext4"
/dev/mapper/LVG-opt: LABEL="opt" UUID="38cd42d9-d282-4641-bc53-f7c4b02bac7d" TYPE="ext4"
/dev/mapper/LVG-home: LABEL="home" UUID="2abf32ba-e53f-4d77-aa86-4d13dc142f78" TYPE="ext4"
```

Once systemd starts to initialize, all the processes after it take  the expected time to load.  It seems to be something before systemd.

Here is the critical bit of dmesg:

```

[    3.512089] raid6: .... xor() 6262 MB/s, rmw enabled
[    3.512679] raid6: using ssse3x2 recovery algorithm
[    3.517056] xor: measuring software checksum speed
[    3.556032]    prefetch64-sse: 11249.000 MB/sec
[    3.596018]    generic_sse:  9940.000 MB/sec
[    3.596675] xor: using function: prefetch64-sse (11249.000 MB/sec)
[    3.600724] async_tx: api initialized (async)
[    3.832043] Btrfs loaded, crc32c=crc32c-intel
[    4.007676] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   36.466604] random: crng init done
[   38.366817] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   39.549708] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.610776] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[   39.611886] systemd[1]: Detected virtualization vmware.
[   39.612286] systemd[1]: Detected architecture x86-64.

```

Here is the top part of "systemd-analyze blame" which does not show a problem:
```
          5.081s apt-daily.service
          4.516s ufw.service
          3.632s nmbd.service
          3.429s dev-mapper-LVG\x2dusr.device
          3.279s dev-mapper-LVG\x2droot.device
          2.664s lxd-containers.service
          2.438s networkd-dispatcher.service
          2.118s accounts-daemon.service
          1.975s systemd-networkd-wait-online.service
          1.924s grub-common.service
          1.535s keyboard-setup.service
          1.535s rpcbind.service
          1.407s ssh.service

```

---

### Post by LHammonds on 2018-07-21
Anyone else seeing this issue?  I still have not found a solution or workaround.

---

### Post by QIII on 2018-07-22
I'll spin up a KVM with a fresh install and see what I get.

KVM != VMWare, but maybe I'll get a clue.

---

### Post by QIII on 2018-07-22
KVM machine shows:

```
Startup finished in 3.065s (kernel) 3.620s (userspace) = 6.605s
```

That's with 2048MB mem and 2 threads on my Threadripper.

That's a fresh install.  I'll edit after I update.

Edit:

Updated, the boot time was 5.184s, so about a second faster.

Hitting "random: crng init done" at 7.882.

I didn't use logical volumes and no RAID.  Clue?

---

### Post by LHammonds on 2018-07-22
Hmm....I will have to install a test server without LVM and see if there is a difference.  If so, the issue would be with LVM or maybe LVM+VMware.  I'll report my findings.

EDIT: Still have not been able to test this...too many fires to put out currently.

---

### Post by LHammonds on 2018-07-26
I ran some tests based on how the disks are initially partitioned and the versions of Ubuntu in a patched and unpatched state (but I doubt patch status has anything to do with it)

Below are the test results configuring a default server with the original alternative ISO for Ubuntu Server 18.04 LTS.

The main difference between the installs is the option chosen during the partition section.

[SIZE=4]Guided - use entire disk (no LVM)[/SIZE]
18.04.0 LTS, 4.15.0-20 kernel - Boots in 8-11 seconds
18.04.1 LTS, 4.15.0-29 kernel - Boots in 13-16 seconds

[SIZE=4]Guided - use entire disk and setup LVM[/SIZE]
18.04.0 LTS, 4.15.0-20 kernel - Boots in 8-11 seconds
18.04.1 LTS, 4.15.0-29 kernel - Boots in 8-13 seconds

The default install creates a /dev/dm-1 swap partition.  I created a file-based swap as follows:

```

fallocate --length 1G /opt/swapfile1g
chown root:root /opt/swapfile1g
chmod 600 /opt/swapfile1g
mkswap /opt/swapfile1g
swapon /opt/swapfile1g
swapoff /dev/dm-1

```

I also edited /etc/fstab to remove the swap partition reference and add the swap file.

```

/opt/swapfile1g  none  swap  sw  0  0

```

The patched LVM server boots in 8-15 seconds. (tested this multiple times)

Now I remove the unused swap logical volume (which is not in use nor mounted).

```
lvremove /dev/ubuntu--vg/swap_1
```

And at this point, this is where the 30 second pause starts occurring during boot which seems to be the source of the problem.  Changing the default swap to a file swap....but removing the old volume/partition.

There must be another step needed to clear out the old swap reference.

**EDIT #1:** I did find a reference to the old swap partition in /etc/initramfs-tools/conf.d/resume and set it to "none" but that made no difference to the boot speed.  Still has 30 second pause.

**EDIT #2**: Ah ha!  I forgot to run "update-initramfs -u" and that fixed it once resume was set to none.

Now I will check my production servers which the partitions were configured manually with LVM to see if the same result happens.

**EDIT #3:** Negative.  Problem persists.  There was not a resume file so I created one with same ownership/permissions and set it to "RESUME=" and updated initramfs but it made no difference.  The system is still looking for the old swap partition somewhere.

**EDIT #4:** I will have to build a new server from scratch doing the same test but setting the manual partitions to see when the problem occurs if not immediately.

LHammonds

---

### Post by LHammonds on 2018-07-26
Got a bit further isolating the issue but still no solution.

I just setup a new VM and chose to partition manually with LVM.  I did not configure a swap partition during install but it did create a swap file in the root partition automatically (/swapfile).  However, without modifying anything after the initial boot, it still pauses for 30 seconds.  Here is the new server as it is sits right now:

```
# systemd-analyze time
Startup finished in 37.607s (kernel) + 6.725s (userspace) = 44.333s
```

The server was installed using the "alternative" ISO using LVM on a 30 GB (virtual) hard drive.

Server Info:
```
# uname -a
Linux ubuntu 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04 LTS
Release:        18.04
Codename:       bionic
```

fdisk -l
```
Device     Boot  Start      End  Sectors  Size Id Type
/dev/sda1  *      2048   976895   974848  476M 83 Linux
/dev/sda2       978942 62912511 61933570 29.5G  5 Extended
/dev/sda5       978944 62912511 61933568 29.5G 8e Linux LVM
```

lvscan
```
# lvscan
  ACTIVE            '/dev/LVG/root' [<1.86 GiB] inherit
  ACTIVE            '/dev/LVG/usr' [<1.86 GiB] inherit
  ACTIVE            '/dev/LVG/var' [<1.86 GiB] inherit
  ACTIVE            '/dev/LVG/tmp' [476.00 MiB] inherit
  ACTIVE            '/dev/LVG/bak' [476.00 MiB] inherit
  ACTIVE            '/dev/LVG/srv' [188.00 MiB] inherit
  ACTIVE            '/dev/LVG/opt' [188.00 MiB] inherit
  ACTIVE            '/dev/LVG/home' [188.00 MiB] inherit
```

/etc/fstab
```
/dev/mapper/LVG-root /               ext4    errors=remount-ro 0       1
/dev/mapper/LVG-bak /bak            ext4    defaults        0       2
# /boot was on /dev/sda1 during installation
UUID=0ebde70b-04f9-4a1c-86a9-3f08d971167e /boot           ext4    defaults        0       2
/dev/mapper/LVG-home /home           ext4    defaults        0       2
/dev/mapper/LVG-opt /opt            ext4    defaults        0       2
/dev/mapper/LVG-srv /srv            ext4    defaults        0       2
/dev/mapper/LVG-tmp /tmp            ext4    defaults        0       2
/dev/mapper/LVG-usr /usr            ext4    defaults        0       2
/dev/mapper/LVG-var /var            ext4    defaults        0       2
/swapfile                                 none            swap    sw              0       0
```

blkid
```
# blkid
/dev/sda1: LABEL="boot" UUID="0ebde70b-04f9-4a1c-86a9-3f08d971167e" TYPE="ext4" PARTUUID="24645aec-01"
/dev/sda5: UUID="NCOUiP-2cDA-9lqL-asdP-KU4Z-djRk-rdS0Bc" TYPE="LVM2_member" PARTUUID="24645aec-05"
/dev/mapper/LVG-root: LABEL="root" UUID="dffdf110-3a49-4b66-801c-96680e9e5ade" TYPE="ext4"
/dev/mapper/LVG-usr: LABEL="usr" UUID="3af42e83-42b0-4480-be27-95eee311a982" TYPE="ext4"
/dev/mapper/LVG-var: LABEL="var" UUID="f9b5c436-fbe2-4dad-890a-d340a5898af2" TYPE="ext4"
/dev/mapper/LVG-tmp: LABEL="tmp" UUID="439ab470-96f0-4394-9087-0ff98d8afa49" TYPE="ext4"
/dev/mapper/LVG-bak: LABEL="bak" UUID="2e779bad-1df9-4067-bdb4-492085c97965" TYPE="ext4"
/dev/mapper/LVG-srv: LABEL="srv" UUID="cd6f9314-f304-4c75-a0ae-dae719eb60a0" TYPE="ext4"
/dev/mapper/LVG-opt: LABEL="opt" UUID="4fb10d40-0bb8-4b6a-b310-3ba85e32a00c" TYPE="ext4"
/dev/mapper/LVG-home: LABEL="home" UUID="3560f09a-a7ab-4618-94a2-b2c446b4b9b3" TYPE="ext4"
```

dmsetup ls
```
# dmsetup ls
LVG-srv (253:5)
LVG-opt (253:6)
LVG-root        (253:0)
LVG-bak (253:4)
LVG-tmp (253:3)
LVG-usr (253:1)
LVG-var (253:2)
LVG-home        (253:7)

```

Here is the critical bit of dmesg:

```

[    3.016063] raid6: .... xor() 6937 MB/s, rmw enabled
[    3.016086] raid6: using ssse3x2 recovery algorithm
[    3.018726] xor: automatically using best checksumming function   avx
[    3.021359] async_tx: api initialized (async)
[    3.141198] Btrfs loaded, crc32c=crc32c-intel
[    3.306064] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   35.883923] random: crng init done
[   37.187340] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   37.757154] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.774572] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[   37.775766] systemd[1]: Detected virtualization vmware.
```

Here is the top part of "systemd-analyze blame" which does not show a problem:
```
          2.653s dev-mapper-LVG\x2dusr.device
          2.624s dev-mapper-LVG\x2droot.device
          1.778s lxd-containers.service
          1.536s networkd-dispatcher.service
          1.208s systemd-networkd-wait-online.service
          1.161s snapd.service
           961ms accounts-daemon.service
           884ms keyboard-setup.service
           879ms grub-common.service
           855ms lvm2-monitor.service
           814ms lvm2-pvscan@8:5.service
           788ms ssh.service

```

---

