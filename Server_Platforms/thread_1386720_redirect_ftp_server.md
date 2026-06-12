---
title: "redirect ftp server"
date: 2010-01-21
forum: Server Platforms
---

### Post by blackcloud on 2010-01-21
how i can redirect ftp server from ip 192.168.0.5 to 192.168.0.1 cause my router on ip 192.168.0.1 so with that i can open it from outside my ip public.
thanks before.

---

### Post by a9k3d on 2010-01-21
What you should search for is "port forwarding" on your router. Make sure you forward ports 20 and 21.

---

### Post by blackcloud on 2010-01-21
i has open port 21 on my router but i need redirect from ip 192.168.0.5 to 192.168.0.1.
on my router iam not install ftp just on client but i has open port 21 and iam using arno iptables.

---

### Post by volkswagner on 2010-01-21
from inside your LAN open your browser to [canyouseeme.org]("http://www.canyouseeme.org/").

It will show your external ip address an you can check the port to see if it is open.

You will also have to do exactly as a9k3d says, "forward the port via your routers settings".  This way when you enter your external ip address as seen from the above web address, the router can forward the request to the correct PC.

On my Linksys router, port forwarding is located in the applications and gaming tab, ie: applications meaning FTP, SSH, etc.

---

