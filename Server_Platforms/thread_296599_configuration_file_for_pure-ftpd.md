---
title: "configuration file for pure-ftpd"
date: 2006-11-09
forum: Server Platforms
---

### Post by grager on 2006-11-09
i installed pure-admin using synaptic; i managed to configure my ftp server and i can use it now, but i want to config some things that pure admin can't do (i.e. idle timeout), i found on google that it can be easily configured in pure-ftpd.conf but i don't have this file in /etc or /etc/pure-ftpd !! what i should do?

---

### Post by drakkan on 2006-11-10
you have to create a file in /etc/pure-ftpd/conf with yes on no for every option,

for example if you want chroot users create the file

ChrootEveryone

with the contents:

yes

thanks the debian way for this

---

### Post by grager on 2006-11-10
but i'm afraid that when i create default config file my ftp server stop working and i spended a lot of time to run it :/

---

