---
title: "Noob needing advice on setting up home vpn server"
date: 2010-12-21
forum: Server Platforms
---

### Post by maranhao on 2010-12-21
Hey all,

I'm a biochemist by trade and have no background in computing or networking. I need advice on setting up a home vpn server. My girlfriend lives in Switzerland and I need a way to have her VPN to my house so that she can use Netflix.

Would it work if I got a nettop computer and installed Ubuntu server on it. Then got DynDNS service and setup up a hostname. On the nettop I install the DNS updater (ddclient) to update the private IP address of my hostname with that of my router. Then all I have to do is setup the OpenVPN? This is the part that is fuzzy for me.

Any help would be appreciated.

Thanks,
Maranhao

---

### Post by doogy2004 on 2010-12-21
I use OpenVPN-AS, it is simple to setup and use.  [http://openvpn.net/index.php/access-server/overview.html](http://openvpn.net/index.php/access-server/overview.html)

---

### Post by maranhao on 2010-12-22
Thanks for the help. One question though. So everything up to the OpenVPN was correct?

-Maranhao

---

### Post by brettg on 2010-12-22
You can also use ssh & ppp to create a VPN

[http://tuxnetworks.blogspot.com/search?q=ppp](http://tuxnetworks.blogspot.com/search?q=ppp)

---

### Post by Frodaddy on 2010-12-23
I'm in the UK and wanted Netflix as well. So I booted up a linode server ([www.linode.com](www.linode.com)) and followed this guide:
[http://library.linode.com/networking/openvpn/ubuntu-10.04-lucid](http://library.linode.com/networking/openvpn/ubuntu-10.04-lucid)

Very straightforward. Albeit I have about 5-10 other people on the VPN.

---

### Post by doogy2004 on 2010-12-29
> **maranhao said:**
> Thanks for the help. One question though. So everything up to the OpenVPN was correct?

-Maranhao

For the most part, Access Server is much easier to deploy and manage since it has a web gui.  It is free to use for up to 2 concurrent connections.

---

