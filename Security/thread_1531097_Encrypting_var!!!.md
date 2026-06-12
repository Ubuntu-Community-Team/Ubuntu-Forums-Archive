---
title: "Encrypting /var?!?!?!"
date: 2010-07-14
forum: Security
---

### Post by Zorgoth on 2010-07-14
I've been having major problems trying to encrypt /var.  Does anyone have any reliable way to do it?

---

### Post by bodhi.zazen on 2010-07-14
> **Zorgoth said:**
> I've been having major problems trying to encrypt /var.  Does anyone have any reliable way to do it?

What problem are you having and what have you tried ?

---

### Post by Zorgoth on 2010-07-14
I've been trying to follow this link.  

[http://blog.larsstrand.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.larsstrand.org/article.php?story=EncryptedSwapAndHomeUbuntu)

I've used it before on a 32-bit system.  I am trying to make a 64-bit system with the same packages.  I install the packages, set up the encryption from a live CD (tarring and untarring var and treating it like the link treats home), and before I had encrypted tmp, swap, and var.  Now I get a computer that won't boot into GNOME and doesn't always even create cryptotmp.  /var is the problem, as I have pretty satisfactorily determined, but I can't find another way to encrypt it.

---

### Post by bodhi.zazen on 2010-07-14
Alright, so you are using LUKS, that is a start.

Is your archive (tar) encrypted data ?

You would need to post your config files for review.

Another option is to perform an installation using the Alternate CD, that will set LVM and LUKS up for you. You may of course manually specify the partitions.

---

### Post by Zorgoth on 2010-07-14
Alternate CD sounds good!  But I'm going to try one more time before reinstalling my OS again.  The tar contains no sensitive data so there is no reason to encrypt it (I think).  I extract it back after running cryptsetup and mkfs.ext4 and mounting /dev/mapper/cryptovar.

Here's my crypttab and fstab

```

# <target name>	<source device>		<key file>	<options>
cryptoswap /dev/sda7 /dev/urandom cipher=aes-cbc-essiv:sha256,size=256,hash=sha256,swap
cryptotmp /dev/sda5 /dev/urandom cipher=aes-cbc-essiv:sha256,size=256,hash=sha256,tmp
cryptovar /dev/sda6 none luks

```
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/mapper/cryptotmp       /tmp            ext2    defaults        0       2
/dev/mapper/cryptovar       /var            ext4    defaults        0       2
# swap was on /dev/sda7 during installation
/dev/mapper/cryptoswap swap swap sw 0 0

```

---

### Post by bodhi.zazen on 2010-07-14
So if I understand your set up, swap and tmp are working and you are not using LVM.

As you boot you are asked for your passwords ?

---

### Post by Zorgoth on 2010-07-14
I was on my old setup.  Now sometimes I get asked for a password when I am very lucky, but even then it doesn't tend to work.

---

### Post by Zorgoth on 2010-07-14
I think I just got it it to work.  I think I did something wrong with /etc/security/pam_mount_conf.xml.  Going to try to set up my old home directory and if that works my 20-hour ordeal is over!

---

### Post by Zorgoth on 2010-07-14
Day saved!  I am going home now.

---

