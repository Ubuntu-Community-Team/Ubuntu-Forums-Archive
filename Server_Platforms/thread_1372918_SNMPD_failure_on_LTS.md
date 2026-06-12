---
title: "SNMPD failure on LTS"
date: 2010-01-05
forum: Server Platforms
---

### Post by johestephan on 2010-01-05
Hello all,

i have a problem with snmpd on "real" amd64 machines. I mention the real, cause it really only effects physikal machines. The virtual guests arent effectet.

write(3, "Connection from UDP: [XXX.XXX.XXX"..., 43) = 43
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=2309, ...}) = 0
sendto(7, "<30>Jan  5 10:10:47 snmpd[11739]"..., 77, MSG_NOSIGNAL, NULL, 0) = 77
--- SIGFPE (Floating point exception) @ 0 (0) ---

snmpd dies with this after several minuits.

Architecture: amd64
Source: net-snmp
Version: 5.4.1~dfsg-4ubuntu4

is the effectet software.

Dont know what todo

Greetz

---

