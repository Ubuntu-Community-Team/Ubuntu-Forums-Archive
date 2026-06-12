---
title: "Remote Server Questions"
date: 2007-02-03
forum: Server Platforms
---

### Post by ReckmanR on 2007-02-03
I want to place my linux box at another location with ethernet so it doesn't eat all my bandwidth. Couple of questions, How can i either set a stable IP, or Can I get the box to Email the Ip on boot? Is there any I can do to make the default remote desktop a little more secure, In windows i know i can set it to only accept connections from a certain IP, anything like this for linux that could help with this? (i tried FreeNx but couldn't configure it)

I'm running Ubuntu 6.10 ATM, but i'm probably gunna switch to the server edition before i move it. I'm somewhat new to linux been using it for 5 months. I'm gunna be running, a Gnutilla Client, CS server, and Php. Thanks in advance

---

### Post by kidders on 2007-02-03
> **ReckmanR said:**
> How can i either set a stable IP, or Can I get the box to Email the Ip on boot?Whether your IP is static depends on your ISP. Domestic internet connections usually aren't. One possibility is to set yourself up with a dynamic DNS service ... there are several to choose from. :-)

If you'd prefer to have your IP mailed to you, doing so at boot-up may not be frequent enough. I suppose you could tie the mail transmission into a pre-existing DHCP-related script, to be a little safer.

> **ReckmanR said:**
> Is there any I can do to make the default remote desktop a little more secureCall me paranoid, but I would never leave anything like that remotely accessible, except on an "on demand" basis. For instance, I use a VPN to do most things on my remote Linux box, but I always turn it off when I'm not using it. Although there are lots of different ways of achieving the same effect, one option might be to write yourself a little shell script that reconfigures your firewall to admit RDP connections from your current IP, and another to block it up when you're done.

---

### Post by elst on 2007-02-03
The desktop probably isn't that useful for a Linux server - the Server edition doesn't include a graphical interface by default. You need remote desktop access for Windows servers because the admin tools there are graphical, rather than command-line based as on *NIX.

SSH remote access enables you to run pretty tight security, e.g. key-based authentication rather than just passwords. You can do IP-based access restriction for SSH and other services either with firewall rules, or by using the TCP wrappers system.

---

### Post by ReckmanR on 2007-02-04
Thanks ill try that.

---

### Post by Brazen on 2007-02-04
yeah, if you use the server edition (I highly suggest going with 6.06 Dapper), then you won't have a graphical desktop (unless you specifically install one, which would defeat the purpose of using the server edition).  You'll use ssh for remote administration.

Do you have a gnutella client in mind?  You can probably find a web based one.  I use torrentflux for a web-based torrent client, so I just connect to a web page located on my server and use the web client to download torrents to my server.  I know amule also can be used as a web client for the edonkey network.

For your IP, you'll probably want to use a dyndns service and then if you have a soho router in front of the server, most soho routers have a built in dyndns client (which you'll need to easily configure) that will update the dyndns service if the ip ever changes.

---

