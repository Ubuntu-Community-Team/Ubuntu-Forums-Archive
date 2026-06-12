---
title: "[SOLVED] SSH configuration"
date: 2007-10-10
forum: Server Platforms
---

### Post by piercleo on 2007-10-10
Hello all,

I am trying to setup a ssh connection in order to access my home CPU from my laptop when I am away. I am having a little problem setting up the security of the SSH connection, in particular the Public Key Authentication. I am following this Howto: [https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30](https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30)

When I type ssh-copy-id -i ~/.ssh/id_dsa.pub root@fileserver01 in a console, I am being asked the root password. I type it in but i get a "permission denied" message.

Maybe i am not typing the proper password ? Which one should I type.

Basically what I am trying to do is to have a secure ssh connection between my two CPU's both way around.

Best regards,

Piercleo

---

### Post by stimpack on 2007-10-10
```
ssh-copy-id -i ~/.ssh/id_dsa.pub yourusername@yourhomeIP
```

Username is the account name you usually log on with at home and the same password.

---

### Post by piercleo on 2007-10-10
TY Stim, worked like a charm...i was putting root@theipadress !

---

