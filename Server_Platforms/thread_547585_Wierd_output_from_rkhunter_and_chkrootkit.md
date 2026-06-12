---
title: "Wierd output from rkhunter and chkrootkit"
date: 2007-09-10
forum: Server Platforms
---

### Post by Pugwash on 2007-09-10
Hi,

I've noticed some wierd stuff from rkhunter and chkrootkit. In /var/mail I get the follwing message from rkhunter:

```

Scanning for packet capturing applications...  [ Warning! ]
Warning! Found packet capturing application. Please check the logfile.
Scanning for hidden files...  [ Warning! ]
-----------------------------------------------------------------

Found warnings:
[07:38:24] Checking for packet capturing applications... Warning
[07:38:25] Warning! Process /sbin/dhclient3 (3847) listening 
```

In rkhunter.log I get this

```
[07:38:24] Checking for packet capturing applications... Warning
[07:38:25] Warning! Process /sbin/dhclient3 (3847) listening 
```

I also get this from chkrootkit:

```
 Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[3847]) 
```

I'm a bit worried here, is this normal?

---

### Post by dreadlord_chris on 2007-09-10
Those are normal - that's the DHCP client... I'm assuming your computer has a dynamic IP right?

---

### Post by Pugwash on 2007-09-11
> **dreadlord_chris said:**
> Those are normal - that's the DHCP client... I'm assuming your computer has a dynamic IP right?

That's a relief, thanks. Yes, I'm using DHCP to connect to my router.

---

