---
title: "Dansguardian and iTalc"
date: 2010-08-19
forum: Ubuntu Christian Edition
---

### Post by gnarly_buttons on 2010-08-19
I'm using the dansguardian-gui and iTalc at our school.  iTalc is a program to allow me to view and control the computers in a classroom.  It runs on port 5900.  How can I configure dansguardian/tinyproxy to allow me to still use iTalc?  At the moment I cannot access the computers with iTalc.

Thanks for your help.
Scott

---

### Post by david_kt on 2010-08-20
> **gnarly_buttons said:**
> I'm using the dansguardian-gui and iTalc at our school.  iTalc is a program to allow me to view and control the computers in a classroom.  It runs on port 5900.  How can I configure dansguardian/tinyproxy to allow me to still use iTalc?  At the moment I cannot access the computers with iTalc.

Thanks for your help.
Scott

Open terminal and:

```
gksudo gedit /etc/init.d/ubuntu_ce_firewall
```

Look for "## Open port for ssh server (22), web server (80), and mail server (25)"

Copy and paste below line under it:
```
iptables -A INPUT -p tcp --dport 5900 -m state --state NEW -j ACCEPT
```

Save and close the file.

Restart firewall:
```
sudo /etc/init.d/ubuntu_ce_firewall restart
```

Try iTalc again.

DK

---

### Post by gnarly_buttons on 2010-08-27
Thanks, that worked.

---

