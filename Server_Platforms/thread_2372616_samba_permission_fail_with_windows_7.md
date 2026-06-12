---
title: "samba permission fail with windows 7"
date: 2017-09-27
forum: Server Platforms
---

### Post by joe6302413 on 2017-09-27
Hi,
Recently, I installed a new ubuntu server with 16.04LTS and SAMBA system.
However, I cannot login to the file with my account and password on another windows 7.
Here is my configuration in the smb.conf.
```
[lab218cloud] 
       path = /mnt/hddata/test
        read only = no
        guest ok = yes
        valid users = joe
```
I am sure I created my account with smbpasswd commend, and the authorization to the folder test is set to be joe:joe as well.
The folder lab218cloud is shown on the windows file manager under address (my server's IP).
It is pretty confident that I put my name in the windows authorization pop-up.
Can any one tell me what did I set wrong with my samba server?
My windows is under the subnet of IP .

BTW, I tested with other public computer with an IP MY.IP.*.*  And it seems like I cannot even see the folders when I type \\MYIP.

---

