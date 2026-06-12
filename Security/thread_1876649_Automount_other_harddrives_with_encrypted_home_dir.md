---
title: "Automount other harddrives with encrypted home directory"
date: 2011-11-06
forum: Security
---

### Post by SadaraX on 2011-11-06
UPDATE: This problem has been fixed.

SOLUTION: OpSecShellshock pointed out that I should just try auto-mounting things somewhere else than my /home/user directory. I did this (in /media/Data, etc. ), and then created symbolic links to there for my home. (Link from /media/Data to /home/user/Data).

I don't know how this will effect when I start encrypting specific directories on the Data drive, but since most of those are not needed for booting or Desktop-Startup, this should not be a problem.

ORIGINAL PROBLEM:

I am having a problem with auto-mounting data harddrives while using an encrypted home directory on another partition/drive.

I just installed Kubuntu 11.10 on my system, and for the first time used the "encrypt the home directory" feature. (Default settings. No changes made by me.) The Operating system is installed on /dev/sda1. My home is in /home/bob. 

After the install process, I edited my /etc/fstab to automatically mount my other data drives (into folders in my home directory for convenience), such as /dev/sda3. Example from my /etc/fstab:

```
/dev/sda3 /home/bob/Sata  ext4  auto,defaults 0 0
```

However Kubuntu will auto-mount on boot-up OR after I login through KDM! 

I really need to find a way to make Kubuntu/Ubuntu mount the drives IMMEDIATELY, either on start-up (since these are not files which need be secured), or IMMEDIATELY after I login through KDM but before KDE starts to load my user profile. I use symbolic links for various configuration files used by KDE, and if the drive is not ready (mounted) before KDE starts to load my user profile after login, most of my preferences are broken.

Some of my preference files are linked from this data drive into my home directory. (For example, my .bashrc and .vimrc). 

```
$ ls -la

lrwxrwxrwx  1 bob bob   40 2011-10-18 21:24 .bashrc -> /home/bob/Sata/linux/conf/.bashrc
lrwxrwxrwx  1 bob bob   28 2011-10-17 19:43 documents -> /home/bob/Sata/Documents

```

Here is what my /etc/fstab looks like:

```
proc /proc proc nodev,noexec,nosuid 0 0
UUID=<long number for root partition> / ext4 errors=remount-ro 0 1
/dev/mapper/cryptswap1 none swap sw 0 0
# /dev/sda2 is swap
/dev/sda3 /home/bob/Sata  ext4  auto,defaults 0 0

```

That is all.

After I login and run the 'mount' command with no arguments, here is the output:
```

....
/dev/sda3 on /home/bob/Sata type ext4 (rw,commit=600)
....
/home/bob/.Private on /home/bob type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=<long number>, ecryptfs_fnek_sig=<long number>)

```


Even though mount claims /dev/sda3 is mounted, there is nothing actually there (and therefore none of the symbolic links are resolving correctly.) It only *actually* mounts after I manually run the mount command with all arguments 'mount -t ext4 /dev/....'.

Any suggestions for getting my non-secure drives to auto-mount on startup or IMMEDIATELY after I login through KDM (but before KDE loads my user profile)?

UPDATE: Added more fstab and mount command info.

---

### Post by OpSecShellshock on 2011-11-06
It seems to me that if the home directory is encrypted, and at the same time where the mount points are located, you're going to run into trouble in that your mount points will be indecipherable until after your session has begun (and your home has been decrypted). I'd be more worried if this actually could be worked around.

Do you run into the same problem if you switch your mount point for the other drives to /mount/drivename? Not suggesting this as the permanent fix, but just to isolate where the problem is occurring.

---

### Post by ztux on 2011-11-08
If these HDDs are connected during boot and encrypted using LUKS, you need to make keyfiles for them and entries in /etc/crypttab

---

