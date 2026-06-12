---
title: "Can't open LUKS drive after upgrade to 18.04"
date: 2018-07-18
forum: Security
---

### Post by bradhaack on 2018-07-18
I just updated from xubuntu 16.xx LTS to 18.04 LTS.   New install of cryptsetup.  
Maxtor USB drive that I have previously encrypted and have been using under 16.xx LTS
In 'disks' I can unlock the drive, but can't mount it.
It also fails to mount with Thunar
On command line: 
dt1:sudo cryptsetup luksAddKey /dev/sdb /root/keyfile
results in "IO error while encrypting ke*****."

sudo cryptsetup  luksOpen /dev/sdb Maxtor   results in: 
"Cannot use device /dev/sdb which is in use (already mapped or mounted)."

sudo cryptsetup  luksClose /dev/sdb 
Device sdb not found

Any help appreciated.
```

sudo cryptsetup --debug luksAddKey /dev/sdb /root/keyfile
# cryptsetup 2.0.2 processing "cryptsetup --debug luksAddKey /dev/sdb /root/keyfile"
# Running command luksAddKey.
# Locking memory.
# Installing SIGINT/SIGTERM handler.
# Unblocking interruption on signal.
# Allocating context for crypt device /dev/sdb.
# Trying to open and read device /dev/sdb with direct-io.
# Initialising device-mapper backend library.
# Trying to load any crypt type from device /dev/sdb.
# Crypto backend (gcrypt 1.8.1) initialized in cryptsetup library version 2.0.2.
# Detected kernel Linux 4.15.0-23-generic x86_64.
# PBKDF pbkdf2, hash sha256, time_ms 2000 (iterations 0), max_memory_kb 0, parallel_threads 0.
# Reading LUKS header of size 1024 from device /dev/sdb
# Key length 32, device size 195813072 sectors, header size 2050 sectors.
# PBKDF pbkdf2, hash sha256, time_ms 2000 (iterations 0), max_memory_kb 0, parallel_threads 0.
# Interactive passphrase entry requested.
Enter any existing passphrase: 
# Checking volume passphrase [ke***** -1] using passphrase.
# Trying to open key slot 0 [ACTIVE].
# Reading key slot 0 area.
# Using userspace crypto wrapper to access ke***** area.
Key slot 0 unlocked.
# File descriptor passphrase entry requested.
# Adding new ke*****, existing passphrase provided,new passphrase provided.
# Selected ke***** 2.
# Trying to open key slot 0 [ACTIVE].
# Reading key slot 0 area.
# Using userspace crypto wrapper to access ke***** area.
Key slot 0 unlocked.
# Calculating data for key slot 2
# Running pbkdf2(sha256) benchmark.
# PBKDF benchmark: memory cost = 0, iterations = 1310720, threads = 0 (took 25 ms)
# PBKDF benchmark: memory cost = 0, iterations = 1275639, threads = 0 (took 411 ms)
# PBKDF benchmark: memory cost = 0, iterations = 1272543, threads = 0 (took 824 ms)
# Benchmark returns pbkdf2(sha256) 1272543 iterations, 0 memory, 0 threads (for 256-bits key).
# Key slot 2 use 2545086 password iterations.
# Using hash sha1 for AF in key slot 2, 4000 stripes
# Updating key slot 2 [0x41000] area.
# Using userspace crypto wrapper to access ke***** area.
IO error while encrypting ke*****.
# Releasing crypt device /dev/sdb context.
# Releasing device-mapper backend.
# Unlocking memory.
Comsudo cryptsetup --debug luksAddKey /dev/sdb /root/keyfile
# cryptsetup 2.0.2 processing "cryptsetup --debug luksAddKey /dev/sdb /root/keyfile"
# Running command luksAddKey.
# Locking memory.
# Installing SIGINT/SIGTERM handler.
# Unblocking interruption on signal.
# Allocating context for crypt device /dev/sdb.
# Trying to open and read device /dev/sdb with direct-io.
# Initialising device-mapper backend library.
# Trying to load any crypt type from device /dev/sdb.
# Crypto backend (gcrypt 1.8.1) initialized in cryptsetup library version 2.0.2.
# Detected kernel Linux 4.15.0-23-generic x86_64.
# PBKDF pbkdf2, hash sha256, time_ms 2000 (iterations 0), max_memory_kb 0, parallel_threads 0.
# Reading LUKS header of size 1024 from device /dev/sdb
# Key length 32, device size 195813072 sectors, header size 2050 sectors.
# PBKDF pbkdf2, hash sha256, time_ms 2000 (iterations 0), max_memory_kb 0, parallel_threads 0.
# Interactive passphrase entry requested.
Enter any existing passphrase: 
# Checking volume passphrase [ke***** -1] using passphrase.
# Trying to open key slot 0 [ACTIVE].
# Reading key slot 0 area.
# Using userspace crypto wrapper to access ke***** area.
Key slot 0 unlocked.
# File descriptor passphrase entry requested.
# Adding new ke*****, existing passphrase provided,new passphrase provided.
# Selected ke***** 2.
# Trying to open key slot 0 [ACTIVE].
# Reading key slot 0 area.
# Using userspace crypto wrapper to access ke***** area.
Key slot 0 unlocked.
# Calculating data for key slot 2
# Running pbkdf2(sha256) benchmark.
# PBKDF benchmark: memory cost = 0, iterations = 1310720, threads = 0 (took 25 ms)
# PBKDF benchmark: memory cost = 0, iterations = 1275639, threads = 0 (took 411 ms)
# PBKDF benchmark: memory cost = 0, iterations = 1272543, threads = 0 (took 824 ms)
# Benchmark returns pbkdf2(sha256) 1272543 iterations, 0 memory, 0 threads (for 256-bits key).
# Key slot 2 use 2545086 password iterations.
# Using hash sha1 for AF in key slot 2, 4000 stripes
# Updating key slot 2 [0x41000] area.
# Using userspace crypto wrapper to access ke***** area.
IO error while encrypting ke*****.
# Releasing crypt device /dev/sdb context.
# Releasing device-mapper backend.
# Unlocking memory.
Command failed with code -1 (wrong or missing parameters).
mand failed with code -1 (wrong or missing parameters).

```

---

### Post by haplorrhine on 2018-07-20
My USB key never mounted properly, but I liked the [Archlinux wiki.]("https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption#Cryptsetup_usage")

---

### Post by TheFu on 2018-07-28
LUKS is usually on the partition, not the whole disk.  Could you be missing the partition number?
Also, when doing a luksOpen, the name of the LUKS encrypted area needs to be provided.

The cryptsetup manpage:
```

       open --type luks <device> <name>
       luksOpen <device> <name> (old syntax)

              Opens  the  LUKS  device  <device>  and sets up a mapping <name>
              after successful verification of the  supplied  passphrase.   If
              the  passphrase  is  not  supplied  via  --key-file, the command
              prompts for it interactively.

              The <device> parameter can be also specified by LUKS UUID in the
              format  UUID=<uuid>,  which  uses  the symlinks in /dev/disk/by-
              uuid.

              <options> can be [--key-file, --keyfile-offset,  --keyfile-size,
              --readonly,   --test-passphrase,   --allow-discards,   --header,
              --key-slot, --master-key-file].
``` 
**lsblk** should show how lvm and luks and partitions are layered.

There are *status* and *repair* options too.

---

### Post by bradhaack on 2018-07-28
There is 1 partition on the disk.
I don't know what is different, but I can mount it now.
I was succeeding in getting it open with:
cryptsetup --debug luksOpen /dev/sdb dm-2 
but mounting failed with a 'can't read superblock' error.   Not that went away I can mount it.
Now, 
cryptsetup --debug luksAddKey /dev/sdb /root/keyfile
still fails with 'code -1 (wrong or missing parameters).'
I'm not sure I need this?

---

### Post by TheFu on 2018-07-28
If sdb is the whole disk, then it is highly, highly, highly likely that sdb1 is the partition. More importantly, that is probably what you should be pointing at 98% of the time.

But if you actually posted the **lsblk** output, we'd know for certain.  It would be bad if you were in the 2%.

The error being displayed - _wrong or missing parameters_ - could easily be due to this problem.

---

### Post by bradhaack on 2018-07-29
```
:lsblk

NAME            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda               8:0    0 232.9G  0 disk  
&#9500;&#9472;sda1            8:1    0  39.2M  0 part  
&#9500;&#9472;sda2            8:2    0  14.2G  0 part  
&#9500;&#9472;sda3            8:3    0  37.5G  0 part  
&#9500;&#9472;sda4            8:4    0     1K  0 part  
&#9500;&#9472;sda5            8:5    0   9.8G  0 part  
&#9500;&#9472;sda6            8:6    0 132.6G  0 part  /home
&#9500;&#9472;sda7            8:7    0   500M  0 part  
&#9500;&#9472;sda8            8:8    0  15.5G  0 part  
&#9474; &#9500;&#9472;fedora-root 253:0    0  13.5G  0 lvm   
&#9474; &#9492;&#9472;fedora-swap 253:1    0     2G  0 lvm   
&#9492;&#9472;sda9            8:9    0  22.8G  0 part  /
sdb               8:16   0  93.4G  0 disk  
&#9492;&#9472;dm-2          253:2    0  93.4G  0 crypt 
sr0              11:0    1  1024M  0 rom
``` 
[added quote tags]

---

### Post by TheFu on 2018-07-29
Thanks.  You are definitely running a non-standard setup. Without that information, we would have made all sorts of wrong assumptions. I'm not convinced dm-2 is really available.  Is it unencrypted?

Please edit the post #6 and wrap the output in "code tags" - **Go Adv** # will do that.  This makes things line up. Too hard to read otherwise.
Also, when booted into the OS you want, please run** df -hT**, also with code tags.
A luksDump would be helpful too.

Update:
Stepping back, I'm confused. That isn't very unusual. Happens all the time. ;)

Was there a reason for adding another key to an already encrypted area?   
Could the beginning of the disk have wiped by accident?  Did a **cryptsetup repair** work?  
Is there data inside sdb-crypt?  Is there a file system inside?  

If I were setting up an encrypted data volume on a disk, I would follow these steps for a drive without anything I cared on it.
[LIST=1]
[*]Create a new partition table, usually GPT
[*]Create 1 partition - lots of reasons, but mainly so I and others don't forget the disk actually has data. It also prevents accidental grub installs from wiping the LUKS header. Same for RAID.
[*]cryptsetup create onto  /dev/sdZ1 (passphrase + yubikey for access)
[*]Add a hugely long 65+ character passphrase randomly generated by my password manager for recovery if something terrible happens to my yubikey (I use a mix of yukikey and passphrase to unlock my encrypted storage)
[*]cryptsetup open the volume
[*]create a new fs (ext4) inside the encrypted volume (or setup LVM with PE, VG, LVs)  I like LVM.
[*]mount the LVs/partitions somewhere and populate it with data
[*]Use the storage until done
[*]umount the LV/partition
[*]cryptsetup close the encrypted area
[/LIST]
I didn't look up the exact commands for anything, but those are the steps.  
I'd create a script to run all the mount/umount commands for easier access to open/close the storage.

You probably did all those things.  I'll pull down 18.04.1 today and see if I can reproduce the issue with my setup. It is 16.04 currently.  I'll use a live-boot (not ready to install 18.04 anywhere yet).
```
$ lsblk 
NAME                          MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 55.9G  0 disk  
&#9500;&#9472;sda2                          8:2    0  488M  0 part  /boot
&#9500;&#9472;sda3                          8:3    0 54.9G  0 part  
&#9474; &#9492;&#9472;sda3_crypt                253:0    0 54.9G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root   253:1    0   51G  0 lvm   /
&#9474;   &#9492;&#9472;ubuntu--vg-swap_1 253:2    0  3.9G  0 lvm   [SWAP]
&#9492;&#9472;sda1                          8:1    0  512M  0 part  /boot/efi
```

---

### Post by bradhaack on 2018-07-29
This morning, I can't mount it.   Using file manager, I get this message:
```
Error mounting /dev/dm-2 at /media/brad/Maxtor1: can't read superblock on /dev/mapper/dm-2.
```

Mounting from cmd line:
```
dt1:sudo mount -t ext4 /dev/mapper/dm-2 /media/Maxtor/
mount: /media/Maxtor: can't read superblock on /dev/mapper/dm-2.
```

From dmesg:
```

[ 4053.487331] sd 4:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4053.487344] sd 4:0:0:0: [sdb] tag#0 Sense Key : Illegal Request [current] 
[ 4053.487347] sd 4:0:0:0: [sdb] tag#0 Add. Sense: Invalid command operation code
[ 4053.487351] sd 4:0:0:0: [sdb] tag#0 CDB: Synchronize Cache(10) 35 00 00 00 00 00 00 00 00 00
[ 4053.487356] print_req_error: critical target error, dev sdb, sector 0
[ 4053.487399] JBD2: recovery failed
[ 4053.487402] EXT4-fs (dm-2): error loading journal
```

```
dt1:df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.9G     0  2.9G   0% /dev
tmpfs          tmpfs     588M  1.2M  587M   1% /run
/dev/sda9      ext4       23G  7.8G   14G  37% /
tmpfs          tmpfs     2.9G   65M  2.9G   3% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.9G     0  2.9G   0% /sys/fs/cgroup
/dev/sda6      ext4      131G  103G   22G  83% /home
tmpfs          tmpfs     588M   28K  588M   1% /run/user/1000
```

---

### Post by TheFu on 2018-07-29
code tags, please.  quote tags are NOT the same. Thanks for trying.
I updated my prior post significantly, but you'd already seen it and replied.

---

