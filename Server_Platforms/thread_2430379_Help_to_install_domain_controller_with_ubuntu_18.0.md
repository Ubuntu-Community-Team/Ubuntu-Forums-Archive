---
title: "Help to install domain controller with ubuntu 18.04.03 lts"
date: 2019-10-31
forum: Server Platforms
---

### Post by jramos031 on 2019-10-31
Good morning everyone, in the most attentive way I ask for help to install a domain controller in ubuntu server, one of the problems I have is that when saving the resolv.conf file it does not store the dns information, I am using SAMBA for the domain controller, and when I check the services, it shows me the following error: Job for smbd.service failed because the control process exited with error code. See "systemctl status smbd.service" and "journalctl -xe" for details.


I don't know what to do I've been looking for the solutions and I already tried them and it still causes me problems

Atte.
Juan Carlos

---

### Post by wildmanne39 on 2019-10-31
Hello and welcome to the forum.

*Thread moved to **Server Platforms a more appropriate sub-forum**.*

The reason I moved your thread is you posted it in the Resolution Centre and the strap line at the top of that sub-forum says:
> This is the place to contact a forum admin concerning problems with your forum account, to appeal moderator action, to request a thread be moved from the jail, or to file a complaint about forum harrassment or abuse.

So I moved your thread to the server sub-forum for support.

Please also note that you posted on an English only sub-forum so I translated your post for you this one time only, in the future please post in English or select one of the sub-forums from the link below to post in your own language.

[https://ubuntuforums.org/forumdisplay.php?f=183](https://ubuntuforums.org/forumdisplay.php?f=183)

Thanks

---

### Post by TheFu on 2019-10-31
resolv.conf cannot be edited.  Managing of DNS is handled in a different way and it is extremely release connected.
The Ubuntu Server Guide will explain how to setup DNS. For DNS settings with a static IP on 18.04 Server: [https://help.ubuntu.com/lts/serverguide/network-configuration.html#name-resolution](https://help.ubuntu.com/lts/serverguide/network-configuration.html#name-resolution)

Be aware, the DNS is NOT the same as Domain Controller.

I can't help with Windows stuff, sorry.   But there is probably a chapter in the Ubuntu Server Guide about that too.
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)  - perhaps in the Samba subject heading?

---

