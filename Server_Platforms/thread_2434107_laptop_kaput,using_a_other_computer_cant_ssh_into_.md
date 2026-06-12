---
title: "laptop kaput,using a other computer cant ssh into my roock pi 4 server annimore"
date: 2019-12-30
forum: Server Platforms
---

### Post by bertm2 on 2019-12-30
so the question is :
if you lose your ssh keys and cant log in thru ssh, but you can log on directly. how do you restore openssh properly so it will acsept new keys?  must i uninstall open ssh and install it again or is there a better way
i hope somebody can help
greetings bert

---

### Post by wildmanne39 on 2019-12-30
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

### Post by darkod on 2019-12-31
No, you don't need to reinstall openssh.

If you have direct access to the machine all you need to do is allow password authentication in /etc/ssh/sshd_config (be careful, there is also file called ssh_config in that folder, but the one that controls the server part is sshd_config).

Restart the sshd service after making changes in that file.

Having password authentication will allow you to login over ssh using username and password, and it will also allow you to copy new key to the server using ssh-copy-id. After that you can disable password auth again if that is what you want.

Have you checked whether it allows you login with username right now? Maybe it's not disabled.

---

