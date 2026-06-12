---
title: "loop-aes on Ubuntu Feisty"
date: 2007-05-28
forum: Server Platforms
---

### Post by limited001 on 2007-05-28
As loop-aes-source does not appear in the repository and no current tutorials appear to be exist (the older tutorials do not seem to work as-given), any pointers or tutorials to use loop-aes on Ubuntu Feisty.

A tutorial will be compiled from responses, if possible.

Thanks in advance.

---

### Post by kalisto on 2007-05-31
Check this out: [http://felipe-alfaro.org/blog/2006/08/19/encrypted-home-on-ubuntu-using-cryptoloop/](http://felipe-alfaro.org/blog/2006/08/19/encrypted-home-on-ubuntu-using-cryptoloop/)

Iv been having a little trouble with unmounting the device. 

Let me know if it works for you. Turn on debugging for pan_mount in /etc/security/pam_mount.conf
Set debug option from 0 to 1.

If you also have trouble please, please PUHLEEESEEE confirm: [https://bugs.launchpad.net/ubuntu/+source/libpam-mount/+bug/117736]("https://bugs.launchpad.net/ubuntu/+source/libpam-mount/+bug/117736")

other than not unmounting properly it works great!

---

### Post by nutz on 2007-06-03
Can loop-AES be used to encrypt the entire boot disk? I run Ubuntu from an external hard drive which I take with me almost everywhere I go. I am looking for some encryption scheme that will protect the data should it ever find its way into someone else’s possession...

Something similar to what PGP whole disk encryption does...

---

