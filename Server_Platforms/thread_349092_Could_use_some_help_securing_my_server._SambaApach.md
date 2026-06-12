---
title: "Could use some help securing my server. Samba/Apache"
date: 2007-01-29
forum: Server Platforms
---

### Post by derrick1985 on 2007-01-29
Hi,

I just set up a small business/personal server using Ubuntu Edgy Eft on an older 1ghz, 768MB of ram. I have configured my samba shares sucessfully now I would just like to secure it. I want to only be able to access the shares via a local intranet. I have all my computers connected through a router, and would like to secure it both hardware and software. I'm also unsure of how to set a  static IP and not use DHCP. 

The other thing I have is a apache server with postgresql/perl installed to use sql-ledger. I would like also to only be able to access the server via local intranet. I could use some advice on how to update sql-ledger to the latest version and inject my old postgresql database into my new one. I had PCLinuxOS as my main system before and I saved the old database and need to restore it on my new system. How would I go about doing this?

Thanks for any help

Derrick

---

### Post by MrHorus on 2007-01-30
If all your local connections are coming from a single subnet such as 192.168.10.x then you can configure IP tables to only allow incoming web/MySQL connections from that range and drop everything that comes from any other addresses.

---

### Post by derrick1985 on 2007-01-30
> **MrHorus said:**
> If all your local connections are coming from a single subnet such as 192.168.10.x then you can configure IP tables to only allow incoming web/MySQL connections from that range and drop everything that comes from any other addresses.

Ok then, how can I get a crash course in configuring IPtables?

---

### Post by PurplePenguin on 2007-02-08
[Here you go.]("http://www.ubuntuforums.org/showthread.php?t=159661")

---

### Post by derrick1985 on 2007-02-08
> **PurplePenguin said:**
> [Here you go.]("http://www.ubuntuforums.org/showthread.php?t=159661")

Eeek, this stuff scares me. Any nice web gui I could do this with?

---

