---
title: "Samba Domain Controler Issues"
date: 2006-11-28
forum: Server Platforms
---

### Post by cyris| on 2006-11-28
Hey everyone.

I followed the guide from howtoforge on setting up ubuntu as a pdc for a windows network. 

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

I also used poledit.exe to create my NTconfig.pol file for system and user policies.

However when I login to the domain my policies are not applied and i get this error in event viewer on the windows xp machine :D

"Windows cannot obtain the domain controller name for your computer network. ( The specified domain either does not exist or could not be contacted. ). Group policy processing aborted."

No idea where this error is coming from, but its probably why my policies are not being loaded.

Anyone have an idea?

Thanks.

---

### Post by cyris| on 2006-11-29
To build on my question. Could it be the fact that I haven't made any machine accounts ?

---

