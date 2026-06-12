---
title: "LIST cmd in PASV mode timeout"
date: 2008-10-09
forum: Server Platforms
---

### Post by rkleemann on 2008-10-09
Hi,

I'm running vsftpd with force SSL.

I'm testing via FileZilla. It connects, authenticates, issues the PASV command, and then the LIST fails...

I'm guessing this must be related to the PASV address? The server is behind a firewall and has a 192.168.1.201 address.

But even if I set the pasv address to be the public IP it still hangs.

Thanks for any help
Ricardo

---

### Post by lykwydchykyn on 2008-10-09
PASV mode uses a range of high ports for data transfer, which you set in your vsftpd config file.  You have to make sure these ports are open on the firewall.  

Check the pasv_max_port and pasv_min_port parameters in the config file, and open the ports in that range.

---

### Post by rkleemann on 2008-10-09
> **lykwydchykyn said:**
> PASV mode uses a range of high ports for data transfer, which you set in your vsftpd config file.  You have to make sure these ports are open on the firewall.  

Check the pasv_max_port and pasv_min_port parameters in the config file, and open the ports in that range.

Thanks!

Is it bad to disable PASV mode instead?

---

### Post by lykwydchykyn on 2008-10-09
PASV works better for clients behind firewalls.  It lets the client do all the requesting, so that the server is not trying to initiate connections back to the client.  Most decent firewalls would block that kind of behavior.

---

