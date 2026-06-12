---
title: "Samba server appears as it's own domain"
date: 2012-11-14
forum: Server Platforms
---

### Post by TheMightyGirth on 2012-11-14
Hi All,

I have a fairly simple samba domain set up on a 12.04 box which seems to work fine. I can log on as a domain user, join machines to the domain, browse the network etc, etc.

I am a little puzzled however because when I browse the network from an XP machine (not sure if it happens from win 7) as well as the "domain" name and an old workgroup appearing I also get a workgroup in the name of the server

eg, if I goto;

My Network Places, Entire Network, Microsoft Windows Network

I get;
mydomain and myserver

I can then expand mydomain and it shows exactly what I would expect however when I try to expand "my server" I get nothing (no error either)

This is not a massive problem but it makes me think something is wrong somewhere and I would like to get it resolved.

does anyone have any ideas? I have attached my smb.conf for reference.

Thanks in advance for any help.

---

