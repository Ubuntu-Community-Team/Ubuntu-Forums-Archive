---
title: "Unlocking LUKS partitions with keyfile on memory card/stick"
date: 2007-09-20
forum: Server Platforms
---

### Post by kaptengu on 2007-09-20
I have encrypted my home-partition. On startup I am prompted for the LUKS password to unlock the encrypted partition. To avoid this I desided to add a cryptfile on keyslot 1. I now want to store this keyfile on a SD-card or USB-stick.

The problem is that these are mounted after the encrypted disks and the keyfile can therefore not be accessed. Is it possible to mount my SD-card at a very early stage in the boot process?

---

### Post by kaptengu on 2007-10-05
I found a solution to my problem here:
[http://www.debianhelp.org/node/6797](http://www.debianhelp.org/node/6797)

> Another question: is there a way to use a USB pendrive to store the
> information needed to LUKS to decrypt the partitions? (so that I
> wouldn't have to fill in any password, just plug the USB pendrive)

Yes, there is. For any partition *except* the root partition, you need
to make the following changes:

- add the key to the luks-Partitions using cryptsetup luksAddKey
- make an entry for your stick in your fstab, e.g. /media/key
- copy the keyfile to the stick, e.g. to /media/key/keyfile
- change your crypttab to use the keyfile, e.g.
usr-crypt /dev/hda7 /media/key/keyfile luks
- change CRYPTDISKS_MOUNT in /etc/defaults/cryptsetup to include your
USB stick, e.g. CRYPTDISKS_MOUNT="/media/key"
- rebuild your initrd using update-initramfs -u

---

### Post by AusIV4 on 2008-02-17
I want to thank you for posting this information. I realize this is an old post, but it is the only thing that helped me find what I was looking for.

The information is slightly outdated. Rather than editing /etc/default/cryptsetup, the file in gutsy is /etc/defaults/cryptdisks.

An addition I'd like to make:

My crypttab looks like this:```
home    /dev/sda3   /media/key/keyfile    luks
home    /dev/sda3    none    luks
```
Since LUKS lets you entire either the keyfile or a password, you can have it look for the key-file first, and if it doesn't find it, it will then prompt you for the password. If it finds the keyfile, it skips the next line since the file is already mounted.

This way if you lose the usb key or don't have it handy, you can still boot your computer without jumping through too many hoops.

---

### Post by asforme on 2008-02-26
I'm still having trouble with this.  I add my keyscript as per the instructions, but boot still fails and drops me to a command prompt.  When I check the sbin directory I find the keyscript was never copied into initramfs.  However in that command prompt I am able to manually mount my usb drive and use the keyfile to mount my encrypted root partition.  Type exit and everything is just fine.

I have a keyscript in sbin that mounts my usb drive cat's the keyfile then unmounts.

I added the ,keyscript=/sbin/keyscript option after luks in /etc/crytptab.

And last thing before I rebooted I ran update-initramfs -u.

It seems like update-initramfs is not seeing that I need my keyscript copied over.  Am I missing something?

---

### Post by nightfrost on 2008-05-06
> **asforme said:**
> I'm still having trouble with this.  I add my keyscript as per the instructions, but boot still fails and drops me to a command prompt.  When I check the sbin directory I find the keyscript was never copied into initramfs.  However in that command prompt I am able to manually mount my usb drive and use the keyfile to mount my encrypted root partition.  Type exit and everything is just fine.

I have a keyscript in sbin that mounts my usb drive cat's the keyfile then unmounts.

I added the ,keyscript=/sbin/keyscript option after luks in /etc/crytptab.

And last thing before I rebooted I ran update-initramfs -u.

It seems like update-initramfs is not seeing that I need my keyscript copied over.  Am I missing something?

Did you ever get this working? Are you using Hardy?
I have the same problem, and before seeing the last post of this thread I already posted a new thread here: [http://ubuntuforums.org/showthread.php?t=783910](http://ubuntuforums.org/showthread.php?t=783910)

---

