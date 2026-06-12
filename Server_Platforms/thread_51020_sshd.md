---
title: "sshd"
date: 2005-07-22
forum: Server Platforms
---

### Post by [pl]ice on 2005-07-22
hi, i'm learning how to use sshd, for begining where is the config file, where i can change the introduction? eg:
  Desktop$ nc localhost 22
SSH-2.0-OpenSSH_3.9p1 Debian-1ubuntu2

bit silly to introduce itself... :)

thanks.
and yes, i'll read the man...

---

### Post by LordHunter317 on 2005-07-22
It's /etc/ssh/sshd_config, but my memory says you cant' change the version string, nor should you, nor do you care.

---

### Post by souki on 2005-07-22
you cannot remove this version string, maybe you can modify it from the source but you cannot remove it : it's part of the protocol and the client needs it

---

