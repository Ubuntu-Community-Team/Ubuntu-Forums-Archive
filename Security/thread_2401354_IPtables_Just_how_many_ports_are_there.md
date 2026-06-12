---
title: "IPtables: Just how many ports are there?"
date: 2018-09-17
forum: Security
---

### Post by webmiester on 2018-09-17
Hi everyone,

I've been working on building a firewall with a captive portal.  Ive been working of PFsense, and with ubuntu IPtables.  Ive also been reading on Mikrotik...

Here is the thing.  The captive portals seem to block off port 80 which I think the browsers use.  However, android apps seem to use other ports and so even if the device hasnt passed throught the captive portal yet, they can already access the internet.  I want to close all the other ports, so it make me wonder, just how many ports do we have?

---

### Post by The Cog on 2018-09-17
Port numbers for both TCP and UDP go from 0 to 65535 though I don't think 0 actually gets used.

---

### Post by webmiester on 2018-09-17
Thanks.  That's quite a lot of numbers

---

### Post by SeijiSensei on 2018-09-17
Look at the file /etc/services.  It lists all the registered services that use ports.  

```

tcpmux          1/tcp                           # TCP port service multiplexer
echo            7/tcp
echo            7/udp
discard         9/tcp           sink null
discard         9/udp           sink null
systat          11/tcp          users

[...]

```

Only root-owned processes can listen on ports < 1024.  Ordinary users can run programs that listen on ports from 1024-65535.  So HTTP runs on port 80, but something like OpenVPN uses 1194.

---

