---
title: "cryptsetup commands via ssh"
date: 2009-12-08
forum: Security
---

### Post by cyberio on 2009-12-08
Hi all !
I am preparing 2 computers here :
1 samba server in my office "source"
1 hosted server on a secure location "target"

The purpose is to backup "source" to "target" via a "rsync ssh" command...
but the difficult part is to have all the target backed data on a crypted partition...
The script on source will have to
1/ cryptsetup luksOpen the PV
2/ mount the crypted partition
3/ send the datas via rsync
4/ umount the crypted partition
5/ cryptsetup luksClose the PV
... all this via ssh...

so

1/ is there a way to send the passphrase when i execute "ssh cryptsetup" ?
2/ i can make a "cryptsetup luksAddKey" on the target and then send a "ssh cryptsetup -d keyfile" but if the hacker knows the keyfile... he can do the same.. im i right ?

thanks in advance for any help

---

