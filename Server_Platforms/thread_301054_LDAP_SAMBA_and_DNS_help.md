---
title: "LDAP SAMBA and DNS help"
date: 2006-11-16
forum: Server Platforms
---

### Post by DRicher33 on 2006-11-16
Hi everyone,

I'm still working on getting used to linux coming from an MS universe.  I have Edgy running great and I've worked hard on getting LDAP and Samba up and running for my small 5 computer network.

I have read manuals, gone through several tutorials, broken and fixed a variety of things and now I'm at a stage that I can't get past without help.

From a windows XP box I try to log into my new domain I get a can't find DNS errors on the client.

I've tried my best to set up bind9 but I really don't know where to even start to know if it is ldap, dns, samba etc.  The client can ping the linux box by ip and by hostname via the hosts file.

Can someone give me a hand?  Tell me what to post as far as config files and I'll do it.

THANKS!!

---

### Post by DRicher33 on 2006-11-17
Update--more info so someone can give me a hand:

I have set up slapd, ldap, and samba as best I can and this is where I am stuck:

Trying to connect my windows xp pro to join the samba domain.  If I stay as a workgroup in samba I can access shares.  However if I try to join a domain I get Access Denied errors from windows xp.

I tried changing the smb.conf from security=users, to domain, to share and none of those work.

Any ideas?

---

