---
title: "Encrypting boot/disk"
date: 2015-03-31
forum: Security
---

### Post by ryan151 on 2015-03-31
Hi, I want to make Ubuntu ask me for password when booted up. (At the boot screen)  Also how to encrypt my ubuntu partition. (maybe)

I am dual booting Windows 8 and Ubuntu 14.04 and when I boot up I need a extra layer of security.

I know when you are installing Ubuntu you can choose to have your full disk encrypted, but since I have 2 OS's it didn't allow me too.

I have tried adding a password prompt to the grub boot *_(this method: [http://www.howtogeek.com/102009/how-to-password-protect-ubuntus-boot-loader/](http://www.howtogeek.com/102009/how-to-password-protect-ubuntus-boot-loader/))_* loader but when i typed in the password it said access denied so i pretty much had to reinstall ubuntu :(

Any ideas?

Thanks!

---

### Post by sudodus on 2015-04-01
You can install Ubuntu into a USB pendrive (and use the whole pendrive for 'Encrypted disk').

If the computer is new and has USB 3, you can use a fast USB 3 pendrive and get a rather responsive Ubuntu system. A fast  USB 3 pendrive helps in a USB 2 port too, because the flash hardware is often limiting the speed.

See this link [Pendrive speed test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

### Post by ryan151 on 2015-04-01
Thanks that helped a lot.

---

### Post by sudodus on 2015-04-01
Please continue testing for a while, and you are welcome with more questions.

When you feel that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

---

### Post by konrad6 on 2015-04-02
If you have an SSD you could use hardware encryption to encrypt every single bit on the drive. Otherwise a BIOS power-on password prevents accessing the hard drive unless it's physically removed.

---

