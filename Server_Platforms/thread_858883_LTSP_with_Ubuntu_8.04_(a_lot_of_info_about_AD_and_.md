---
title: "LTSP with Ubuntu 8.04 (a lot of info about AD and q about FAT clients)"
date: 2008-07-14
forum: Server Platforms
---

### Post by sopsaare on 2008-07-14
Hi everyone!

I'm new to this forum but I have been around with Ubuntu for a while allrdy.

I have been developing LTSP environment for one school. They have existing Active Directory domain and I have been in a lot of fuss with it. 

First of all, it is pretty straight forwards to make a simple LTSP environment with AD domain authentication. Just install "likewise-open" to server side and join your server to AD domain. Then make in both (the servers and the clients) ssh_config's last line with GASSAPI delegated credentials to "yes". And surprise, U have working AD domain authentication with a possibility to pull of some group memberships from AD domain. For example I added group called "domain^admins" to sudoers and it really gave me a permission to use sudo with all Domain Administrators. 

The biggest problem was the usb storage (not solved yet because of other issues). The user who wants to use fuse needs to be part of the fuse group. That can be worked around making fuse available for anyone. But then we run to another problem. The path where USB storage is mounted will be /media/%USER. But in fact the path is /media/(usergroup where the user belongs). And in default the AD domain users dont belong to any usergroup. 

Partial workaround for this bug is to make the clients fat, when they will not be using the FUSE. But here I run to another problem. My fat clients can't connect to external network. I havent done anything special, just used this "how to" [https://help.ubuntu.com/community/UbuntuLTSP/LTSPFatClients](https://help.ubuntu.com/community/UbuntuLTSP/LTSPFatClients)

Is there anything I need to be doing besides this or have I encountered an error somewhere?

---

