---
title: "CUPS Made SSH and Samba Die."
date: 2009-02-06
forum: Server Platforms
---

### Post by kevin11951 on 2009-02-06
I Installed CUPS onto my server so that I could use it as a wireless print server.  When I installed it though, it made it so that I can't login via ssh, or access my samba shares, in fact, I can't login to the physical server either!

I tried reformatting the server - twice - and ever time it is working perfectly, until I install CUPS.

EDIT:  Webmin still works, so I can run commands, and do stuff even though im locked out.

---

### Post by kevin11951 on 2009-02-06
no help? at all?

I will probably reinstall ubuntu anyway, i just dont want the CUPS hell again...

---

### Post by cariboo on 2009-02-07
If you install from the repositoriess, you shouldn't have any conflicts between cups, ssh and samba. The only thing that could possibly create a problem is to manually configure cupsd.conf for remote access.

I find it easier just to use elinks to access the cups server and setup every thing from there. You can even setup remote access from the cups web interface.

If something doesn't work the way you expect it to. it is always easier to repair the problem then it is to reinstall. If cups is a problem, completely remove it using the purge option with either apt-get or aptitude and start over.

Jim

---

### Post by kevin11951 on 2009-02-07
> **cariboo907 said:**
> If you install from the repositoriess, you shouldn't have any conflicts between cups, ssh and samba. The only thing that could possibly create a problem is to manually configure cupsd.conf for remote access.

I find it easier just to use elinks to access the cups server and setup every thing from there. You can even setup remote access from the cups web interface.

If something doesn't work the way you expect it to. it is always easier to repair the problem then it is to reinstall. If cups is a problem, completely remove it using the purge option with either apt-get or aptitude and start over.

Jim

everything was from the repos, and the only change i made to the config file was adding "Allow @LOCAL" to all the locations.

---

### Post by kevin11951 on 2009-02-07
> **cariboo907 said:**
> If you install from the repositoriess, you shouldn't have any conflicts between cups, ssh and samba. The only thing that could possibly create a problem is to manually configure cupsd.conf for remote access.

I find it easier just to use elinks to access the cups server and setup every thing from there. You can even setup remote access from the cups web interface.

If something doesn't work the way you expect it to. it is always easier to repair the problem then it is to reinstall. If cups is a problem, completely remove it using the purge option with either apt-get or aptitude and start over.

Jim

Thank you for the elinks suggestion, i reinstalled ubuntu (it was dead) and used elinks to access my cups web interface over ssh. now everything works!  :p

---

