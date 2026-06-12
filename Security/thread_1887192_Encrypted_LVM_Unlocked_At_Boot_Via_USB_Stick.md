---
title: "Encrypted LVM Unlocked At Boot Via USB Stick"
date: 2011-11-26
forum: Security
---

### Post by numberman2000 on 2011-11-26
Hi There!

I need a little help with unlocking an encrypted LVM at boot using a key on a USB stick. I've done a lot of searching and found the following:

- The folks at Arch Linux have the best how-to for installing LVM on a luks encrypted partition

- What I'm looking to do has a bunch of out-dated how-to's

So -- this is what I've done and what I need help with:

My hard drive is configured as such:

/dev/sda1 /boot 256M ext2
/dev/sda2 LVM on top of luks encryption

[LIST]
[*]physical volume - /dev/sda2
[*]volume group - vgroup
[*]logical volumes
[*]root /             10G
[*]swap                4G
[*]home /home         100% Remaining space
[/LIST]

The encryption was layed-down prior to the LVM setup.

During boot, the system will ask me for a password before moving forward -- this is expected operation.

What I want to do is have a keyfile on a USB stick that is installed at boot time that the system will go to prior to asking for a password. The USB stick is a 1G vfat volume.

I've already added the passphrase that is on the USB stick to the encrypted volume and verified that I can open drive using said passphrase.

What I've found (and I'm hoping my google-fu isn't waning) is that in both the Arch and Ubuntu guides (which are the most common and are both out-dated), they add a boot parameter to the kernel that looks something like this:

```
cryptkey=/dev/disk/by-uuid/561F-BFE3:vfat:/foo/bar/key.file
```

where the uuid is that of the USB stick.

And occasionally, they have an additional parameter:

```
cryptdevice=/dev/sda2:vgroup
```

where 'vgroup' is the name of the volume group in the lvm.

I think I'm missing something with loading the necessary modules in the first moments of boot. I need to have the modules that handle USB, CRYPT and (maybe) LVM.

Do I need to make an initramfs that has these modules?
Do I still have these kernel parameters in the grub.cnf file (I know they are setup through /etc/default/grub)?

Any help or direction pointing would be helpful.

Thank you!

---

### Post by rorrison on 2011-12-26
My findings will be posted at askubuntu.com

---

### Post by hdavid7 on 2012-10-25
Hi, could you post a link to your findings on the other form?

Kind Regards,
hdavid7

---

