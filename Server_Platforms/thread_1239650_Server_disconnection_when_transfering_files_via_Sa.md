---
title: "Server disconnection when transfering files via Samba"
date: 2009-08-13
forum: Server Platforms
---

### Post by GriFF3n on 2009-08-13
When trying to transfer files from my server to my desktop, the files never get fully transfered. I have windows cmd running a ping to my server, and all is fine until i try to transfer files. Some will transfer fine, and then out of nowhere the server will stop replying. I then have to restart the server to gain access to it. A 2 GB file will transfer about halfway, and then the server will not be able to be pinged. I have static IP on the server and my desktop. Running XP x64 and Ubuntu server 32-bit 9.04. Using Samba. Any ideas?

---

### Post by jocampo on 2009-08-13
> **GriFF3n said:**
> When trying to transfer files from my server to my desktop, the files never get fully transfered. I have windows cmd running a ping to my server, and all is fine until i try to transfer files. Some will transfer fine, and then out of nowhere the server will stop replying. I then have to restart the server to gain access to it. A 2 GB file will transfer about halfway, and then the server will not be able to be pinged. I have static IP on the server and my desktop. Running XP x64 and Ubuntu server 32-bit 9.04. Using Samba. Any ideas?

Both at same network or data needs to travel across several routers? when you ping your server from the XP machine, what's the latency in ms ...

---

### Post by GriFF3n on 2009-08-13
> **jocampo said:**
> Both at same network or data needs to travel across several routers? when you ping your server from the XP machine, what's the latency in ms ...

<1 ms, I have both my desktop and server connected to the same gigabit switch, and then my switch connected to my router.

---

### Post by cariboo on 2009-08-14
I had the same problem with my server, it turned out it was a problem with the builtin network adapter. I disabled it and put in a gigabyte nic, and haven't had the problem since.

---

### Post by GriFF3n on 2009-08-14
> **cariboo907 said:**
> I had the same problem with my server, it turned out it was a problem with the builtin network adapter. I disabled it and put in a gigabyte nic, and haven't had the problem since.


Can't solve the problem that way. I have a MSI Wind nettop as my server, and there is no way to add a card. Plus it only happens when transferring data. If i leave the server alone, I can ping it all day. As soon as I try to transfer data, it losses connection.

GriFF

---

### Post by jocampo on 2009-08-14
I'm afraid is something related with your network driver, because it looks you have a fast network. That said, Samba is a powerful but complex Linux service. So, tweaking that is not easy. However, I think that, like NFS, there are some configurations that you can play with a bit and check results; for instance ... the socket options.

Take a look on this link
[http://ubuntuforums.org/showthread.php?t=938902]("http://ubuntuforums.org/showthread.php?t=938902")
... it could help, it could not, but certainly, you will learn something during the process ;-) and wit worth the try.

Let us know,

---

### Post by jocampo on 2009-08-14
Another interesting link/article that could help also: [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html")

---

### Post by GriFF3n on 2009-08-16
> **jocampo said:**
> Another interesting link/article that could help also: [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html")

Thanks for the advice jocampo, but I don't think its the socket option with SAMBA thats screwing things up. I setup an NFS export and it disconnected just like with SAMBA. Maybe a setting on the network adapter?

---

### Post by GriFF3n on 2009-08-20
Still having a problem with this setup. Tried both NFS and Samba, both disconnect out of nowhere. This is making my server pretty much useless!!!! Any ideas?

---

### Post by cariboo on 2009-08-21
I still say it may be the network adapter, mine did exactly the same as you described. I know you can't change the network adapter, but there are usb ethernet devices available, I have a couple of D-Link devices similar to [this]("http://www.dlink.com/products/?pid=133").

---

