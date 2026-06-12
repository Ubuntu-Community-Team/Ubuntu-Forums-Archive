---
title: "NIS Ubuntu Server (8.10) / Fedora Core Clients (8)"
date: 2008-11-08
forum: Server Platforms
---

### Post by mattai80 on 2008-11-08
Hello,

I'm having a bit of a problem getting Fedora Core clients to authenticate NIS accounts. When the Fedora core client boots, it shows all of the NIS accounts that I have on the server, however when we attempt to login it rejects the username and passwords. I follow the following article for setting up Ubuntu NIS Server:

[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

and I followed the following articles for configuring Fedora Core to use NIS: 

[http://www.yolinux.com/TUTORIALS/NIS.html](http://www.yolinux.com/TUTORIALS/NIS.html)

I disabled IP Tables on the clients, and the server has no explicit entries defined, so I don't think it's a matter of firewall/port issues. Any help is greatly appreciated!! 

PS-- This is technically a school lab project, so I'm not so concerned with security as it's just to demonstrate the use of network accounts authenticating to a central computer in linux. I omitted most of the security hardening in the server tutorial since it wasn't needed.

---

### Post by mattai80 on 2008-11-08
bump

---

