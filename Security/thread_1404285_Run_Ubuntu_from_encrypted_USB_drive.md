---
title: "Run Ubuntu from encrypted USB drive?"
date: 2010-02-11
forum: Security
---

### Post by ulg on 2010-02-11
I've been running Ubuntu from a USB drive. Now i need to work with sensitive data online and stored on the USB drive. Is it possible to run Ubuntu from an encrypted USB drive? If so, how would i do it?

If it's not possible, do you have any suggestions.

Thanks

---

### Post by snowpine on 2010-02-11
You can use the Ubuntu Alternate Install CD. It has an option to create an Encrypted LVM install (everything is encrypted except for /boot).

When you get to the last step of the installer, click Advanced Options and make sure GRUB is installed to the USB stick (so you don't mess up the MBR on your internal hard drive).

Hope that's clear, ask if you have questions.

---

### Post by DZ* on 2010-02-11
You can add an encrypted account to your existing USB installation.

```
sudo apt-get install ecryptfs-utils
sudo adduser --encrypt-home LoginNameXXX
```

edit:you may also want to encrypt or disable swap and encrypt or
put into RAM /tmp

---

### Post by ulg on 2010-02-11
> **snowpine said:**
> You can use the Ubuntu Alternate Install CD. It has an option to create an Encrypted LVM install (everything is encrypted except for /boot).

When you get to the last step of the installer, click Advanced Options and make sure GRUB is installed to the USB stick (so you don't mess up the MBR on your internal hard drive).

Hope that's clear, ask if you have questions.

Don't know how to do this. I downloaded the CD desktop image from the *For your desktop* page and created a CD. I loaded the install CD onto my windows laptop and got to the *prepare disk space *page, chose *specify partitions manually *and got an error *No root file system is defined. *I'd appreciate some help, I'm new to this. Thanks.

---

### Post by jflaker on 2010-02-11
I'll make life easy on you...

Download TrueCrypt ([http://www.truecrypt.org](http://www.truecrypt.org)) and you can create a volume container (volume file) which you mount with TrueCrypt...store your data in this container and you don't need to worry about encrypting the whole system.

Alternatively, you can use TrueCrypt to encrypt your whole drive, either boot drive or USB drive....or both if you really insist on full encryption of EVERYTHING....both are rather simple to do.

---

