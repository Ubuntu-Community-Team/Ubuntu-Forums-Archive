---
title: "Port 32775 Open"
date: 2006-10-25
forum: Server Platforms
---

### Post by TerryHowe on 2006-10-25
I run nmap and have port 32775 open, what do I need to do to close it?

```

root@m715:~#  nmap -sU 192.168.2.98

Starting Nmap 4.03 ( http://www.insecure.org/nmap/ ) at 2006-10-25 19:51 MDT
Interesting ports on 192.168.2.98:
(The 1479 ports scanned but not shown below are in state: closed)
PORT      STATE         SERVICE
53/udp    open|filtered domain
68/udp    open|filtered dhcpc
32775/udp open|filtered sometimes-rpc14

```

I was hoping not to run a firewall, this is Dapper for a web/mail/DNS server.

---

### Post by TerryHowe on 2006-10-26
lsof tells me that the port was opened by named, so it was the DNS server.  That should be fine for me, I was concerned it was NFS or something.

---

