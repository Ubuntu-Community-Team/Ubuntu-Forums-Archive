---
title: "Servers..."
date: 2006-09-21
forum: Server Platforms
---

### Post by Titan_Prometheus on 2006-09-21
What Server Packages Do You Recommend to a newbie who wants to run A Mail Server(POP and SMTP), A DNS Server, A Ftp Server, An IRC Server,A Firewall Server And a NTP Server?

---

### Post by spp on 2006-09-22
Packages?

Mail - Postfix
DNS - BIND
FTP - proftpd
IRC - No clue
Firewall - iptables
NTP - ntpd

I would also recommend Webmin as well as it does assist in setting up these services pretty well. I also recommend a good book in server administration because BIND can be a bit of a beast as well as IPTables.

---

### Post by A1ex on 2006-09-22
SMTP - Postfix
POP/IMAP - Dovecot
FTP - vsFTPD
IRC - Hybrid IRCD (If you want to join a network you'll need whatever ircd they use)

Firewall - Shorewall
NTP - openntpd

---

### Post by Titan_Prometheus on 2006-09-22
Thanks for the tips, but about Shorewall, and webmin, i'm looking for non-gui objects. I have just the server installed, and i'm looking to keep the package small, and light.

---

### Post by spp on 2006-09-22
Webmin is web based so no local GUI has to run :)

Just login to the server via a web browser.

SP

---

### Post by A1ex on 2006-09-22
And as far as shorewall goes, yes there is a webmin module, but you can edit the config files directly.

Also, Shorewall isn't a daemon, so there is no overhead in running it. 

It's called at boot to translate it's config files into iptables rules then it quits.

It's also much easier to use than remembering complex iptables rules.

---

### Post by Titan_Prometheus on 2006-09-25
I can't find webmin in any of the normal repo's. apt-cache search webmin, i get nothing.

---

### Post by A1ex on 2006-09-25
The Debian maintainer orphaned the package due to lack of time and so it was dropped from the repo's.

There is a .deb package available on the Webmin site that works perfectly on Dapper.

```
root@hades:# wget http://heanet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.290.deb

root@hades:# dpkg -i webmin_1.290.deb
```

---

