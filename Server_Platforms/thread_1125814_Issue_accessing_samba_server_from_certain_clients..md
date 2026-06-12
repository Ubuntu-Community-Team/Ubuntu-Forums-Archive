---
title: "Issue accessing samba server from certain clients."
date: 2009-04-14
forum: Server Platforms
---

### Post by WBuik on 2009-04-14
I am using Samba (3.2.3) on my Ubuntu 8.10 server and I am having trouble accessing to the shares from certain computer.

I have Samba set up to only use port 445 and have disabled netbios entirely.  The only open port I have on my server's firewall is TCP 445.

It seems that the client firewalls on some systems are blocking access to the server, as disabling the firewalls entirely seems to fix any access problems.  None of these client firewalls are set to block outgoing requests though.

The problem is not name resolution because typing the IP directly into the affected systems gets the same error.  These systems can ping the test server without issues.

Part of my problem is that I just don't know how the SMB over TCP protocol works.  Is the server actively trying to open any connections to the clients.  Are there other reasons why the client firewalls might be blocking it.

The effected systems run XP, Vista, and OSX.

(edit) Also, disabling netbios fixed some but not all of the effected systems. (/edit)

Thanks,
Wbuik

---

### Post by jonabyte on 2009-04-20
Not sure why a client firewall would block access, but maybe post your smb.conf file here as well to see if there is something else that might effect it?

---

