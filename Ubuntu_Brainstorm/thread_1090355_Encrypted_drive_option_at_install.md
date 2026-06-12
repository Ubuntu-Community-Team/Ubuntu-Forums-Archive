---
title: "Encrypted drive option at install"
date: 2009-03-08
forum: Ubuntu Brainstorm
---

### Post by Brinstar on 2009-03-08
Not sure how complicated/practical this is (i'm guessing very), but would be good to have some option where the installer encrypts the disk.

---

### Post by qamelian on 2009-03-08
This feature already exists on the alternate install cd.

---

### Post by Brinstar on 2009-03-09
> **qamelian said:**
> This feature already exists on the alternate install cd.

thanks for the tip

---

### Post by gnomeuser on 2009-03-09
> **qamelian said:**
> This feature already exists on the alternate install cd.

We really should offer it on the primary install media somehow. The private encrypted folder approach is seriously flawed, to access the data all I have to do is boot the machine into single user mode.

---

### Post by qamelian on 2009-03-09
> **gnomeuser said:**
> We really should offer it on the primary install media somehow. The private encrypted folder approach is seriously flawed, to access the data all I have to do is boot the machine into single user mode.

I agree. I was just pointing out that there is already a way of getting that feature if you really wanted it.

---

### Post by FiberOptix on 2009-03-16
I would love to see this. I'm not an (OS) developer myself so please forgive any of the following comments if they seem naive:

I was picturing a framework for doing full disk encryption on a hard drive that's post-install, using the same methods as alternate install but taking care of the details of backing things up and then restoring, etc. I had to do this manually over the weekend and it's a pain (in fact it felt like DIY surgery) and I could never really restore it right, despite a post on the forums.

---

### Post by smartboyathome on 2009-03-16
> **FiberOptix said:**
> I would love to see this. I'm not an (OS) developer myself so please forgive any of the following comments if they seem naive:

I was picturing a framework for doing full disk encryption on a hard drive that's post-install, using the same methods as alternate install but taking care of the details of backing things up and then restoring, etc. I had to do this manually over the weekend and it's a pain (in fact it felt like DIY surgery) and I could never really restore it right, despite a post on the forums.

Why not do it how the [Arch Linux wiki]("http://wiki.archlinux.org/index.php/System_Encryption_with_LUKS_for_dm-crypt") does it? I did it on top of LVM, and I didn't have any problems with it. Perhaps it can be adapted for Ubuntu.

---

### Post by AnotherDave on 2009-04-19
There is the alternate disk for encryption at install, but what about post-install? Your disk starts to fill, you buy another drive, now how do you get it to work with your system?

Encryption is very important, yet poorly documented in Ubuntu.

---

### Post by smartboyathome on 2009-04-20
> **AnotherDave said:**
> There is the alternate disk for encryption at install, but what about post-install? Your disk starts to fill, you buy another drive, now how do you get it to work with your system?

Well, if you used LVM, it is as easy as plugging in the new drive, and then resizing the partition to have it span both disks.

> **AnotherDave said:**
> Encryption is very important, yet poorly documented in Ubuntu.

I agree. I use Arch, and it is much better documented than on Ubuntu.

---

