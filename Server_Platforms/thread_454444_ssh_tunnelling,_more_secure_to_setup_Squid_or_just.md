---
title: "ssh tunnelling, more secure to setup Squid? or just use Dynamic?"
date: 2007-05-25
forum: Server Platforms
---

### Post by PetePete on 2007-05-25
when on an insecure network and using ssh tunnelling is it more secure to setup the ssh tunnel to connect to a squid server on the ssh server, or just use the -D (dynamic) option for ssh and act as SOCKS server?

I think i read something about DNS requests being more secure with a squid configuration, but i'm not sure ...

---

### Post by ninocass on 2007-05-25
Personaly i would put all your traffic down an SSH tunnel that way your 100% sure that your traffic is encrypted.  Just set up squid on the remote machine and your laughing.  I use this just the other day to get around content filters: [http://www.nino.me.uk/?postid=63](http://www.nino.me.uk/?postid=63)

---

### Post by PetePete on 2007-05-26
thanks for the reply, thats what I've already setup (also to avoid some content filters ;) )

but you dont HAVE to have the squid proxy installed, can just use dynamic ssh tunnel and setup firefox to use socks server..... but not sure if thats less secure than the squid route.

---

### Post by ninocass on 2007-05-27
> **PetePete said:**
> thanks for the reply, thats what I've already setup (also to avoid some content filters ;) )

but you dont HAVE to have the squid proxy installed, can just use dynamic ssh tunnel and setup firefox to use socks server..... but not sure if thats less secure than the squid route.


Im not too sure either when i get a minute ill fire up ethereal (wireshark) and use both methods and see what information is being shared out :)  tho if you already have it working with squid i say stick with that :D

---

### Post by PetePete on 2007-05-28
if anyones interested I checked this out myself, and it when just using the Dynamic option in ssh and acting as SOCKS some programs (firefox) still connect to the local DNS server to retrieve IP addresses. Allowing people to see what sites  you are visiting which may raise a few alarm bells if using it to avoid content filters ;)

where as with the SQUID route sends all data/dns requests encrypted to the remote ssh server. the only thing that people could see/sniff would be your connection to your ssh server

---

