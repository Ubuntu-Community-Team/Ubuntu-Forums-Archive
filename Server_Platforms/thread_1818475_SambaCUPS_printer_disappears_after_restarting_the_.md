---
title: "Samba/CUPS printer disappears after restarting the server."
date: 2011-08-04
forum: Server Platforms
---

### Post by jengerer on 2011-08-04
I'm trying to set up a shared printer server with Samba/CUPS, but it seems that when I restart the server, the printer no longer appears on the server and the /var/log/samba/log.smbd file prints:

> smbd version 3.5.8 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/08/04 20:05:50.118350,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/08/04 20:05:50.162109,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused

If I restart the smbd service shortly after start-up by running "sudo service smbd restart", the printer will show up and work properly, but upon start-up, the printer won't load properly.

I was thinking it could be because the samba daemon runs before cups, but I change their order using update-rc and I still run across this issue.

Any clue how I could fix this?

Thanks,
Jengerer

---

### Post by marcelo.sairaf on 2011-10-14
same problem here
Ubuntu 10.04.3

---

