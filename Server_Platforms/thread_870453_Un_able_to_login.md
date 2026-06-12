---
title: "Un able to login"
date: 2008-07-25
forum: Server Platforms
---

### Post by jpkumar10 on 2008-07-25
Hi there,

 I have a spare Dell insprion 6000.It working on windows professinal, I want to use this laptop as a server. I have installed ubuntu 8.4 server addition. I forgot the user name and password.I tried to change the user name and password using cd. I am unable to login with new user name and password. Can you suggest me what to do or how to set my system user name and password.

---

### Post by Rocket2DMn on 2008-07-25
I suggest booting into the recovery mode kernel from GRUB and choosing the root terminal.  From here, run
```
ls /home
```
It should list off the home folders of the usernames on the system.  Once you see your username, you can change the password from there with
```
passwd <username>
```
When you are finished, type
```
reboot
```
and let the system load normally.

---

