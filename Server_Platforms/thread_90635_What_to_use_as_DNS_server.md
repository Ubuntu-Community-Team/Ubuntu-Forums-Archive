---
title: "What to use as DNS server?"
date: 2005-11-15
forum: Server Platforms
---

### Post by N8MAN1068 on 2005-11-15
Looking at MaraDNS, PowerDNS(pdns) and TinyDNS.

Anyone have experience with these? Or recommend another package to use?
Gotta have a gui, be able to support MX/SRV records.

Thanks

---

### Post by LordHunter317 on 2005-11-15
Chrooted Bind9 with a frontend of your choosing.

---

### Post by N8MAN1068 on 2005-11-15
what is the 'chrooted' portion?

thanks

---

### Post by jshamlet on 2005-11-15
chroot is simply "change root" - It creates an environment for the service that essentially makes it appear as though the install directory IS the root directory.

This way, if the service is hacked, the attacker can't just cd .. out to the rest of the filesystem, minimizing the exposure of a hacked service to just the directories related to that service. Most web servers are also run in this sort of an environment as well - for the same reason.

I run bind9 in a chroot'ed environment on my primary router/gateway - and have had no problems at all. There are also a ton of guides for setting it up, as it is practically "the" DNS server.

---

### Post by squirrelyosis on 2005-11-16
Bind definetly is "THE" DNS server.  How are you gonna have it running, as a primary DNS server or as a basic caching server for clients?

---

### Post by N8MAN1068 on 2005-11-16
Preferably as the primary.
I've got two different internet lines coming in on two Windows servers.
I'd like to take DNS off of the servers since they occassionally are Web facing and I don't want to risk cache snooping/poisoning or someone getting ahold of one of the servers (exchange, global catalog, pdc, etc functions).

---

### Post by squirrelyosis on 2005-11-16
Do you host websites at your office?  If you don't then bind is very easy to setup and get running.  You install bind9, add the DNS servers of your provider as forwarders, open port 53 on that box, point the clients to your new linux DNS server via DHCP.  By no means am I an expert in this, but I have set it up this way at home.  Website hosting is a different animal but definetly doable.  We run 2 linux boxes that provide the DNS for our hosting services.  All other servers run Windoze.  Also note that we use Windows DNS internally for Active Directory services.  I don't know your exact setup.

---

