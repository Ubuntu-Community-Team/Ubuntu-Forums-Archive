---
title: "Turn Off Encrypted LVM"
date: 2012-03-15
forum: Security
---

### Post by Haneef Mubarak on 2012-03-15
I have a headless server, and I would like to turn off Encrypted LVM (aka no password on startup) or possibly just turn off the password. Essentially, I need to be able to start the system without having to give a password.

---

### Post by Haneef Mubarak on 2012-03-16
Does no one honestly have any idea on how to do this?

---

### Post by uRock on 2012-03-16
If you are wishing to remove the security of having to decrypt on boot up, then maybe a reinstall without encryption is in order. Afterall, what use is encryption if someone can boot into and see the filesystem without a password?

---

### Post by mrmacedonian on 2012-12-18
Haneef,

I am having this issue as well. I installed Ubuntu 12.10 on a media PC to use w/ Unity as well as XBMC, so not headless like your situation.

While this is just a media station as well as a good SFTP server when friends/family need files, I would like to be able to reboot it remotely and this LVM encryption is getting in the way.

Unfortunately I do not have a solution yet, so I am posting mostly to inquire if you've found a method to disable the encryption on the volume without the need for a reinstall. I finally got all the accounts/groups/permissions correct to enable easy secure sftp access and this will be a pain to reconfigure if a reinstall is needed >_<

I appreciate any guidance or solution you may have, thanks!

---

