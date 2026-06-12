---
title: "Network printers, spooler access"
date: 2010-09-13
forum: Ubuntu Christian Edition
---

### Post by gnarly_buttons on 2010-09-13
After installing dansguardian-gui and enabling filtering, I have problems with network printing.

When I add a printer, it doesn't find any of my network printers.  Those that I added still work, except the one on a spooler.

What can I adjust with my settings to access all my printers?  (When I remove dansguardian-gui and all that came with it, I have no printing problems.)

Thanks for your help and for the software.

Scott

---

### Post by david_kt on 2010-09-13
> **gnarly_buttons said:**
> After installing dansguardian-gui and enabling filtering, I have problems with network printing.

When I add a printer, it doesn't find any of my network printers.  Those that I added still work, except the one on a spooler.

What can I adjust with my settings to access all my printers?  (When I remove dansguardian-gui and all that came with it, I have no printing problems.)

Thanks for your help and for the software.

Scott
Open terminal and:

```
gksudo gedit /etc/init.d/ubuntu_ce_firewall
```

Look for "## Open port for ssh server (22), web server (80), and mail server (25)"

Copy and paste below line under it:

```
iptables -A INPUT -p tcp --dport 631 -m state --state NEW -j ACCEPT
```

Save and close the file.

Restart firewall:

```
sudo /etc/init.d/ubuntu_ce_firewall restart
```

Try network printing again.

DK

---

