---
title: "Backup SMTP Spooler"
date: 2010-07-14
forum: Server Platforms
---

### Post by SknarTiT on 2010-07-14
Im running an Exchange server for 4 domains and would like to set up a backup smtp spooler at a second location i case of power or line failure at the main site. Just to spool incoming mail until the main site is online again.

What software should I use at the backup server?
Currently I have a Ubuntu 10.04 server running but dont know what mail software i should install.

---

### Post by mysteron on 2010-07-16
Many would say Postfix (default MTA in Ubuntu), but I recommend Sendmail as I find it easier to use than Postfix.

Just run this cmd:
```
sudo apt-get install sendmail
```

/mysteron

---

