---
title: "Home partition on separate encrypted drive"
date: 2013-02-22
forum: Security
---

### Post by ztux on 2013-02-22
I'm trying to do an encrypted install of Server 12.04 with /home on a second encrypted drive.

I can't select 'use as: physical volume for encryption' but there's no prompt for either the passphrase or keyfile (I want a keyfile, the passphrase was just a test attempt). The partition keeps saying it's not active, even after I try to activate encrypted volumes. I don't get any options to pick a filesystem or mount point either.

How do I get the second encrypted drive to activate?

---

### Post by kevdog on 2013-02-23
I can't say I've done exactly what you want to do, however are you trying to set this up manually or during the installation process.  And if I understand you correctly you want the /home partition on a separate hard drive as compared to the rest of the system.

---

### Post by ztux on 2013-02-28
Yes, the /home directory is to be on a separate physical drive.

I gave up trying to set this up during the install, I couldn't get it to work. I made the appropriate entries in crypttab and fstab, changed the default home path in default/useradd, copied my files over, rebooted, and everything works great.

Still not sure if I was doing something wrong during the install or if it's a bug.

---

### Post by kevdog on 2013-02-28
Sounds like you should write a quick tutorial on the matter.  :popcorn:

---

### Post by bodhi.zazen on 2013-03-01
You used to be able to do what you want during partitioning from the alternate CD, but you had to understand what you were doing.

You might need to do this post-install manually.

The ubuntu wiki seems outdated, try the arch wiki

[https://wiki.archlinux.org/index.php/Dm-crypt_with_LUKS](https://wiki.archlinux.org/index.php/Dm-crypt_with_LUKS)

---

### Post by ztux on 2013-03-01
How to setup a second encrypted hard drive and move your home directory to it:

Let's make a keyfile for it second drive, which I'll be calling cryptextra. 

```
sudo dd if=/dev/urandom of=/etc/keys/cryptextra bs=2048 count=1
```

Restrict access to root

```
sudo chmod 600 /etc/keys/cryptextra
```

Setup LUKS on second drive. Be absolutely sure you have the right drive! If you get it wrong there is NO undo!

```
sudo cryptsetup luksFormat /dev/sdb1 /etc/keys/cryptextra
```

Open cryptextra and make a filesystem.

```
sudo cryptsetup --key-file /etc/keys/cryptextra /dev/sdb1 cryptextra
sudo mkfs.ext4 /dev/mapper/cryptextra
```

Time to setup some config files to auto mount. First, put an appropriate entry in /etc/fstab

```
UUID=abcdef.... /mnt/cryptextra ext4 defaults 0 2
```

And /etc/crypttab. 'noearly' is optional, but you will get a prompt to skip mounting or recover manually on boot if you don't have it.

```
cryptextra UUID=123456 /etc/keys/cryptextra luks,noearly
```

Use 'blkid' to get the UUIDs above. IMPORTANT: The LUKS device UUID goes in crypttab, the UUID for the actual filesystem goes in fstab!

You should reboot at this point to make sure everything works correctly up to this point.

It's time to start moving our home directory.

```
sudo mkdir -p /mnt/cryptextra/home/user
sudo chown user:user /mnt/cryptextra/home/user
```

I had trouble with the next part. Supposedly, all you have to move is the .ecryptfs and .Private folder. That didn't work for me, I had to move the files separately of them. Copy everything in your home directory besides to two ecryptfs files somewhere safe.

```
ecryptfs-unmount-private
rsync -avP .ecryptfs .Private /mnt/cryptextra/home/user
```

Change your home directory in /etc/passwd. The file is quite simple and this should be obvious.

Log out and log back in.

If you want to permanently set the home directory for all new users you create later, edit /etc/default/useradd.

---

