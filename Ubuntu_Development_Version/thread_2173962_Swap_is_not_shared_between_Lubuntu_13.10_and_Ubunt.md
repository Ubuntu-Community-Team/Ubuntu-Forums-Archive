---
title: "Swap is not shared between Lubuntu 13.10 and Ubuntu 10.10"
date: 2013-09-12
forum: Ubuntu Development Version
---

### Post by santosh83 on 2013-09-12
Hi all,

Yesterday I finally bit the bullet and installed Lubuntu 13.10 beta 1. Instead of wiping the whole HDD, I decided to shrink my already existing Ubuntu 10.10's partition and create a new one for Lubuntu 13.10. The installation process had some errors and problems that I'll describe in another post, but in any case it completed successfully and I tested Lubuntu and it was okay. Now my partitions are like this:

sda1 -> Old 10.10 still installed
sda2 -> Used to be 10.10's swap, now shared swap
sda3 -> Lubuntu 13.10 installed and working okay

Lubuntu 13.10 had no problem using sda2's swap space, but when I reboot into Ubuntu 10.10, it refuses to mount the partition saying:
/dev/sda2: read swap header failed: Invalid argument

A separate sudo swapon -a command also returns the same error. How can I share the sda2 swap partitions between both 10.10 and 13.10? I don't want to create another swap partition for 10.10 now, nor can I run comfortably without swap as RAM is just 1 Gb.

Many Thanks.

---

### Post by varunendra on 2013-09-12
Unless you setup an encrypted swap in one of the two OSes, find the actual UUID of your swap partition with -
```
sudo blkid
```

Note down this UUID or keep the terminal open (to copy-paste it later).

[COLOR="#FF0000"]**EDIT : **Just as a precaution, you should backup your current fstab file before editing it -[/COLOR]
```
sudo cp /etc/fstab /etc/fstab.bak
```

Open your /etc/fstab file with root access -
```
gksu gedit /etc/fstab
```

Copy the UUID of the swap partition from the output of blkid above, and paste it in the fstab file, overwriting the previous one. Proofread, save and close the file.

Then check -
```
sudo swapoff -a
sudo swapon -a
```
Is it happy now?

---

### Post by santosh83 on 2013-09-12
Hi varunendra,

Sadly I did select an encrypted home folder in Lubuntu 13.10 (just to try it out), so I guess that means swap will not be shareable between both systems?

Bit of a bother. Can't imagine why swap couldn't be shareable even if I'd an encrypted FS in one or more of the systems...

Thanks!

---

### Post by varunendra on 2013-09-12
> **santosh83 said:**
> Sadly I did select an encrypted home folder in Lubuntu 13.10 (just to try it out), so I guess that means swap will not be shareable between both systems?
No, it won't be, to protect its access from anything other than the OS that encrypted it.

> Bit of a bother. Can't imagine why swap couldn't be shareable even if I'd an encrypted FS in one or more of the systems...
Read a short and nice explanation by codemaniac [post=11978746]here.[/post]

---

### Post by santosh83 on 2013-09-12
Thanks! I solved the issue by creating another swap for 10.10. Not very clean or ideal, but I guess it'll have to do.

---

### Post by varunendra on 2013-09-12
I'm not familiar with filesystem encryption, but you may try the wiki (starting from [here]("https://help.ubuntu.com/community/EncryptedFilesystemHowto")) or search the net to see if it is possible to use the same encrypted swap by creating same user with same password in both OSes.

Just an idea, don't know how much sense it makes, if at all.

---

### Post by santosh83 on 2013-09-12
Well it seems a complex area and personally for me, more trouble than worth it. The few files I usually encrypt are done with GPG and a symmetric cipher. Thanks for the document anyway. It also seems a bit dated... it doesn't mention recent solutions like TrueCrypt and had instructions for Edgy Eft!!

---

### Post by varunendra on 2013-09-12
Yeah I noticed that. Probably the traditional method to encrypt fs natively hasn't changed since then :P

By the way, TrueCrypt isn't very recent either. ;)

---

