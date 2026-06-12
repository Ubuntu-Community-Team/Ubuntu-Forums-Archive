---
title: "Confused - is cryptswap1 mounted or not?"
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cryptotheslow on 2012-03-20
Every time I boot I get the:
"The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present"
Continue to wait; or Press S to skip mounting or M for manual recovery

message on the splash screen for a time but which ultimately disappears as the login screen appears.

I think my failure to grasp how encrypted swap is actually facilitated me has me stumped.

mount doesn't appear to show it as mounted:

```
crypto@ubulaptop1204:~$ sudo mount -l
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/home/crypto/.Private on /home/crypto type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=fa0511987a9d60dd,ecryptfs_fnek_sig=70a90eae5e42d6b7)
gvfs-fuse-daemon on /home/crypto/.cache/gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=crypto)


crypto@ubulaptop1204:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=2a625a50-413c-44f3-a3e6-3375b15af78e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=b43187e0-1f18-4d29-ae6e-398b0717deb0 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
# ubuserver share mount
crypto@ubuserver:/home/crypto/desktopbackups/2ndDrive/shared /home/crypto/ubuserver_shared fuse.sshfs noauto,user,allow_other 0 0


crypto@ubulaptop1204:~$ sudo blkid | grep swap
/dev/mapper/cryptswap1: UUID="863b4f01-500d-4508-8efd-b166bfa2545c" TYPE="swap"
```

GParted shows sda6 as unknown filesystem and not mounted.
Disk Utility shows "Unknown" in the graphical display but Partition Type: Linux swap (0x82)

System Monitor however shows 2.5GiB of swap available (the expected size).

I can understand the disk utilities not making sense of the filesystem as it is encrypted and I can understand sda6 not being mounted directly as it (I think) gets mounted using mapper.

I guess what I am asking - 
Is this expected behaviour?
If it is, is there some way to suppress that error and wait time during boot?
How can swap be mounted at boot time anyway before a password has been entered to unwrap a key or somesuch?

Any links to info on how this actually works (or is meant to work) greatly received as my searching success seems to have hit an all time low today :(

Thanks

---

### Post by jb5 on 2012-03-21
I had a similar problem with failure to automatically mount swap on boot.
What do the following produce?```
free -m
sudo blkid
cat /etc/crypttab
```
Here's mine (now working normally)```
$sudo blkid
/dev/sda1: UUID="b0fdcc67-791c-47c2-a80f-08de8a2640bc" TYPE="ext4" 
/dev/sda5: UUID="2b4c5c28-182c-4d71-9d81-628f6b97b9a5" TYPE="ext4" 
/dev/sda7: UUID="1d3d355d-75df-4945-8ff6-2568bd76f6aa" TYPE="ext4" 
/dev/sda8: LABEL="msoft" UUID="558806D3677F1EEF" TYPE="ntfs" 
/dev/sdb1: LABEL="MUSIC" UUID="c09d9254-8cde-4083-b176-2d492aa79e38" TYPE="ext4" 
/dev/sdb2: LABEL="ss_music" UUID="53C75BE52C02667D" TYPE="ntfs" 
/dev/sdc1: LABEL="disk2" UUID="0543ed88-359d-4f88-b58d-03846279031d" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="ac201f28-7a22-4a81-a39e-a92421ba0ff8" TYPE="swap" 


$free -m
             total       used       free     shared    buffers     cached
Mem:          3953       3792        161          0        252       1595
-/+ buffers/cache:       1944       2008
Swap:         8581          0       8581

cat /etc/crypttab
# <target name>	<source device>		<key file>	<options>
cryptswap1 /dev/sda6 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

```

---

### Post by cryptotheslow on 2012-03-21
Thanks jb5

```

crypto@ubulaptop1204:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3857       2653       1204          0        164       1609
-/+ buffers/cache:        878       2979
Swap:         2519          0       2519


crypto@ubulaptop1204:~$ sudo blkid
[sudo] password for crypto: 
/dev/sda1: LABEL="RECOVERY" UUID="14C5-F177" TYPE="vfat" 
/dev/sda2: LABEL="OS" UUID="34DCCA43DCC9FF5C" TYPE="ntfs" 
/dev/sda3: LABEL="DATA" UUID="2494547294544906" TYPE="ntfs" 
/dev/sda5: UUID="2a625a50-413c-44f3-a3e6-3375b15af78e" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="863b4f01-500d-4508-8efd-b166bfa2545c" TYPE="swap" 


crypto@ubulaptop1204:~$ cat /etc/crypttab
# <target name>    <source device>        <key file>    <options>
cryptswap1 /dev/sda6 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
```


Looks fine - yet on this boot I got the warning message and the wait. Maybe it's just mapper being a bit slow to get setup :confused:

---

### Post by wojox on 2012-03-21
What happens if you edit fstab and call it by UUID instead.

```
# swap was on /dev/sda6 during installation
UUID=b43187e0-1f18-4d29-ae6e-398b0717deb0 none    swap sw      0       0

```

Comment out the /dev/mapper.

---

### Post by cryptotheslow on 2012-03-21
Wouldn't that just result in sda6 being mounted as unencrypted swap?

Or is that the point? To see if sda6 is the holdup rather than mapper?

***edit***

OK tried that. No message now on boot up and it boots up faster. However something is not quite right:
```

crypto@ubulaptop1204:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3857       1096       2761          0         62        490
-/+ buffers/cache:        542       3315
Swap:            0          0          0


crypto@ubulaptop1204:~$ sudo blkid
[sudo] password for crypto: 
/dev/sda1: LABEL="RECOVERY" UUID="14C5-F177" TYPE="vfat" 
/dev/sda2: LABEL="OS" UUID="34DCCA43DCC9FF5C" TYPE="ntfs" 
/dev/sda3: LABEL="DATA" UUID="2494547294544906" TYPE="ntfs" 
/dev/sda5: UUID="2a625a50-413c-44f3-a3e6-3375b15af78e" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="ea389f5f-2755-46c7-be39-71d4d55319b3" TYPE="swap" 


crypto@ubulaptop1204:~$ cat /etc/crypttab
# <target name>    <source device>        <key file>    <options>
cryptswap1 /dev/sda6 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

```

So mapper has still grabbed sda6 for cryptswap1 - however appears not to be functioning correctly as I have zero swap available.

---

### Post by wojox on 2012-03-21
LOL, well I guess living with the message on boot is better than no swap. :p

You are able to revert back accordingly?

---

### Post by cryptotheslow on 2012-03-21
Yep - reverting back is just moving a # - I'll cope thanks :)

Rather than revert however, I think I'll go the route of disabling swap altogether - it never gets used on this machine anyway.

I'm planning to clean install again when we get to full release - so I'll come back to it then if it still happens.

Thanks for the help :)

---

### Post by jb5 on 2012-03-22
cryptswap listed by UUID in fstab is what got me into trouble!!

I am *NOT* an expert, but here is what I did to get swap working normally.

```
sudo swapoff -a
sudo mkswap /dev/sda6
sudo swapon /dev/sda6
sudo ecryptfs-setup-swap
```

Although, from your post (#3), your files / OP look OK. 
Not sure what else to suggest, sorry.

---

