---
title: "Ubuntu live persistent mode + encrypt"
date: 2018-05-13
forum: Security
---

### Post by radoslav896 on 2018-05-13
Hi all,

I use: "Ubuntu v16.04 Mate 64bit" on the USB flash drive, which is divided into two partitions (1, Ubuntu ISO Live)+(2, "casper-rw" persistent mode)
Use home directory encryption...
(Because the complete installation of Ubuntu + LUKS encryption is too demanding on the USB Flash Drive)


I want to move on "Ubuntu v18.04 Mate 64bit"... (Unfortunately, there is no support for home directory encryption)
Is there any possibility how, encrypt casper-rw ? Example: (casper-rw + LUKS ?)

Thx.

---

### Post by C.S.Cameron on 2018-05-13
You should be able to encrypt home folder on a persistent flash drive from "User accounts". Have not tested with 18.04 Mate yet.

see [https://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/](https://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/)

---

### Post by radoslav896 on 2018-05-13
What?....
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1756840](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1756840)
As I have written in the new version of Ubuntu 18.04, this option is no longer available.. (Or, I'm wrong?)

PS:
I started new Ubuntu Mate 18.04 in persistent mode: [http://prntscr.com/jhbthd](http://prntscr.com/jhbthd)
I don't know default username and password...

I do not work these combinations:
root <password Empty>
ubuntu <password Empty>
mate <password Empty>
ubuntu-mate <password Empty>

---

### Post by TheFu on 2018-05-24
I didn't think empty passwords worked with encrypted HOME setups. The password is used to decrypt the HOME, correct?

---

