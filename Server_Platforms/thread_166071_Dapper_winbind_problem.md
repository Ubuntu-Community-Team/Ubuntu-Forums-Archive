---
title: "Dapper winbind problem"
date: 2006-04-25
forum: Server Platforms
---

### Post by xt3 on 2006-04-25
Hi,

I have problems using winbind in Dapper Flight 6. I can't start the winbind daemon.
It always aborts with the following error message:

winbindd -i
winbindd version 3.0.22 started.
Copyright The Samba Team 2000-2004
winbindd: idmap uid range missing or invalid
winbindd: cannot continue, exiting.
Could not init idmap -- netlogon proxy only
smb_panic(): calling panic action [/usr/share/samba/panic-action 10394]
smb_panic(): action returned status 0
PANIC: Could not fetch our SID - did we join?

BACKTRACE: 6 stack frames:
 #0 winbindd(smb_panic2+0x78 ) [0x80dc7c8]
 #1 winbindd(smb_panic+0x19) [0x80dc9c5]
 #2 winbindd(init_domain_list+0x13b) [0x807ae48]
 #3 winbindd(main+0x4a4) [0x80747f0]
 #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d19ea2]
 #5 winbindd [0x80731f1]
Aborted

Even if I fix the uid and gidmap problems it quit with this message. And joining the domain doesn't solve the problem at all.
Is there a solution for this problem, because I want to use Dapper as a Samba Domain client and without winbind it doesn't work ;)

---

