---
title: "Samba / ADS domain question"
date: 2010-02-09
forum: Server Platforms
---

### Post by danep on 2010-02-09
I've set up a Samba share to authenticate against our campus active directory server, ad.school.edu . Thus the realm name is AD.SCHOOL.EDU. However, the domain name (and workgroup parameter in smb.conf) is ADSCHOOL. This is how we colloquially refer to the network domain, and when users log in to network services they conventionally do it with a username like 'ADSCHOOL\username'. The problem is that to log in to the Samba share they must use 'AD.SCHOOL.EDU\username'. The really weird thing is that sometimes they can log in using ADSCHOOL, just not every time! Is there a setting or something that I can tweak to get ADSCHOOL\username authenticating reliably?

I know it sounds relatively minor, but it's a real nuisance to our users, and I'd really appreciate any help. Thanks!

---

### Post by danep on 2010-02-09
Ah... well, I think I may have determined part of the problem- Winbind wasn't running. I started Winbind and I haven't noticed the problem since, hopefully it stays that way.

---

