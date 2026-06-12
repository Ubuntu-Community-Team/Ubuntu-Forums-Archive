---
title: "can't login 8.04 server"
date: 2009-02-17
forum: Server Platforms
---

### Post by oskkars on 2009-02-17
Hi!
I was played with samba and possible something is broken, cause in terminal after **correct login and password** server display server name tty1 and **go back to login**.
I choose recovery mode in grub menu after that I tried to use passwd but here is the answer: "**Aborted**"
Whats going on?

---

### Post by oskkars on 2009-02-17
This help:

- Reboot and choose the "recovery mode" from the boot selection menu
- Choose "drop into root shell" from the recovery menu
- Execute the command: dpkg --purge libpam-smbpass

---

