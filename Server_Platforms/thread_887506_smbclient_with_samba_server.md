---
title: "smbclient with samba server"
date: 2008-08-12
forum: Server Platforms
---

### Post by vk_rams on 2008-08-12
Hi

I have problem in sending the pop up messages in ubuntu like "net send" command in windows. 

In Ubuntu we have to use smbclient command in order to send the popup messages to a system which is connected in network. 

I have installed the samba server for running smbclient also. But i am not able to send that.

I have done the following things

1. installed samba server using "sudo apt-get install samba"
2. when using the command smbclient -M [hostname, it was giving error as connection failed

Please help on this

Thanks in advance

Regards
Vikram

---

### Post by lozd on 2008-08-12
A good samba reference can be found at [SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

Otherwise google "Mount a Windows share on Linux with Samba" for some good references.

Good luck.

---

