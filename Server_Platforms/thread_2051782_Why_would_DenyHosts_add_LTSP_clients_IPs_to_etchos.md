---
title: "Why would DenyHosts add LTSP clients IPs to /etc/hosts.deny?"
date: 2012-09-02
forum: Server Platforms
---

### Post by mightyiam on 2012-09-02
I've this issue with my LTSP setup, where I've DenyHosts set up to protect the server because it is also internet facing (the ssh port) and the IP of the client (there's currently only one client) on the LAN keeps getting written in /etc/hosts.deny.

I've worked around this by adding it to /etc/hosts.allow (the whole subnet, actually) but this is not tested yet and it is only a workaround as I do want DenyHosts to work inside the LAN and this may be a bug.

Is there anything in how LTSP behaves that could cause failed authentications repeatedly thus being added by DenyHosts to /etc/hosts.deny?

This is precise 12.04 up-to-date.

Thanks
Shahar

---

### Post by zazuge on 2012-10-15
I had this issue too
I have two servers that synchronize some files throught rsync via ssh
i setup ssh to block root access and only accept root rsync
and added the ip to allow list
but some couple of i was suprised to receive a mail saying denyhost added that ip to deny list

---

