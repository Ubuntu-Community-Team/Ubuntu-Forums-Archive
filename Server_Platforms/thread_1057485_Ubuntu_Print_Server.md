---
title: "Ubuntu Print Server?"
date: 2009-02-01
forum: Server Platforms
---

### Post by kevin11951 on 2009-02-01
I have an ubuntu (headless) server setup, and i need to connect a printer to it, and have it work as a print server via samba... any help?

the printer is an HP, and the os is 8.10.

---

### Post by Dr Small on 2009-02-01
I haven't got a clue about using it with Samba (I never include Samba in with my recipie), but I always just use CUPS and setup the printer from the web interface.

---

### Post by kevin11951 on 2009-02-01
> **Dr Small said:**
> I haven't got a clue about using it with Samba (I never include Samba in with my recipie), but I always just use CUPS and setup the printer from the web interface.

i did tasksel to install the cups server, but when i type in <server's ip>:631, nothing comes up, i get an error that its not there.

---

### Post by dmizer on 2009-02-01
Moved this to the servers section, where you're more likely to get help related to your problem.

Please post the contents of /etc/cups/cupsd.conf

---

