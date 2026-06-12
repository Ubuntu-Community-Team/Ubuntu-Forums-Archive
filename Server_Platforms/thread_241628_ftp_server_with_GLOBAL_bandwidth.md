---
title: "ftp server with GLOBAL bandwidth"
date: 2006-08-22
forum: Server Platforms
---

### Post by fermulator on 2006-08-22
Hello all!

So I've been trying to investigate which might be the right ftp server for me for linux...

I've checked into:
[LIST]
[*]proftpd
[*]vsftpd
[*]pure-ftpd
[/LIST]

Unfortunately, NONE of these servers offer (yet) the ability for a "global" bandwidth setting.
i.e.  
[LIST=1]
[*]MAX UPLOAD = 100Kb/s
[*]MAX CLIENTS = NONE
[/LIST]
Therefore:  
[LIST]
[*]If there's one user, they receive full bandwidth...
[*]If there's two users, they receive half bandwidth...
[*]If there's 100 users, they receive 1Kb/s..
[*]etc.
[/LIST]

Any suggestions would be greatly appreciated.

Thank you very much!

---

### Post by fnjordy on 2006-08-24
As an alternative you could do it on the firewall, simply setup fair traffic shaping.  m0n0wall or pfSense are good for this as separate appliances, you should be able to do the same on Ubuntu with a mix of tools but not so straight forward, so it depends on how much work you want to do.

---

