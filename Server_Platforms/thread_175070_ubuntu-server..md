---
title: "ubuntu-server."
date: 2006-05-12
forum: Server Platforms
---

### Post by Zorro on 2006-05-12
I find it strange (this is an opening for someone to tell me I'm wrong).. That ubuntu-server does not come with the smp kernel as standard or atleast the option to use it from install.. :( This has forced my hand to move my server to another distro due to the lack of support for my server :( I cannot boot with the latest kernel (it wont recognise my raid card).... 

Tell me if I'm wrong please!!! :( as I'm a real ubuntu fanboy all my desktops have the ubuntu love on it, but looks like my server wont have it :(

---

### Post by Swab on 2006-05-12
Which raid controller?  I had a problem with a mylex card, but there was a solution... search around a bit.

---

### Post by Seaman on 2006-05-12
For most newer RAID-devices the current kernel in Breezy is to old. If you really want to to run Ubuntu, wait a couple of weeks for Dapper stable or use the Dapper beta (I do not think that a server install would encounter that many issues).

---

### Post by Zorro on 2006-05-12
Yeah I have searched (for the past week, but they all say something similar).. the card is a megaraid .. its a dell add on card for the poweredge servers (2400).... It works with warty the .10 kernel.. but not with the latest :(

I'm trying with debian, and after insmod'ing the megaraid module it works like a charm :( with their latest kernel :(

---

### Post by Zorro on 2006-05-12
[QUOTE=Seaman]For most newer RAID-devices the current kernel in Breezy is to old. If you really want to to run Ubuntu, wait a couple of weeks for Dapper stable or use the Dapper beta (I do not think that a server install would encounter that many issues).[/QUOTE]


Yeah, but its an 'older' raid card which should have support I would have thought :confused: 


It was working with warty, but stopped in breezy.. so I'm not sure what will happen with dapper...  :-k

---

### Post by Seaman on 2006-05-13
[QUOTE=Zorro]Yeah, but its an 'older' raid card which should have support I would have thought :confused: 


It was working with warty, but stopped in breezy.. so I'm not sure what will happen with dapper...  :-k[/QUOTE]
Okey, **that is** strange.

---

