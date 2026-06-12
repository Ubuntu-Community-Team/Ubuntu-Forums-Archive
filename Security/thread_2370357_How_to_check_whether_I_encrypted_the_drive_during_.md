---
title: "How to check whether I encrypted the drive during installation?"
date: 2017-09-02
forum: Security
---

### Post by gauss4563 on 2017-09-02
Hi,

So I installed Ubuntu 16.04.3 LTS on a new drive a few days ago and don't remember whether I checked the encryption option. How can I check now whether I enabled it?

Thanks in advance!

---

### Post by SunnyDaze on 2017-09-02
If you encrypted the entire drive, you will know when you boot your system, because it will ask you for a password before it boots to Ubuntu login screen.

If you just encrypted your home folder, you can type **ecryptfs-unwrap-passphrase** into a terminal, and it will ask you for you login password (Passphrase), and then it will return the Hexadecimal encryption key.  If this doesn't work, then you didn't encrypt your home directory.

---

### Post by gauss4563 on 2017-09-02
Thanks!

So I didn't boot the entire drive. Is it possible to do it now or do I have to reinstall? Is there a difference in performance (applied now vs in installation)?
If I have to reinstall in order to do it, is it possible while dual booting? (Windows and Ubuntu are on different physical drives)

Thanks in advance

---

### Post by gauss4563 on 2017-09-02
Some links I found:
[http://thesimplecomputer.info/full-disk-encryption-with-ubuntu](http://thesimplecomputer.info/full-disk-encryption-with-ubuntu)
[https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)
[https://askubuntu.com/questions/909432/how-secure-is-an-encrypted-partition](https://askubuntu.com/questions/909432/how-secure-is-an-encrypted-partition)
[https://askubuntu.com/questions/918021/encrypted-custom-install](https://askubuntu.com/questions/918021/encrypted-custom-install)

And I don't know how many of the techniques here are applicable in Ubuntu:
[https://wiki.archlinux.org/index.php/disk_encryption](https://wiki.archlinux.org/index.php/disk_encryption)

---

