---
title: "SSH gateway computers best practice"
date: 2008-11-13
forum: Server Platforms
---

### Post by Causer1984 on 2008-11-13
Hello everyone.

My scenario is that my company has many desktop *nixes behind a firewall and users screaming for an ssh-gateway. Authentication for this gateway is done by winbind (we are a Windows house.)

Not really a problem, but was wondering if anyone had any good design tips for this ssh-gateway that I'm setting up. Authentication and everything works well, but I'm a little troubled about what to do with homespace (which is on multiple MS 2003 servers.) Ideally, I would samba mount that as the homespace, but pam_mount doesn't like having homespaces on different samba servers (or not the last time I checked anyway.) Another option would be to completely disable a homespace, but then how would keys work for when users ssh into their macs?

Any tips appreciated.

---

### Post by Causer1984 on 2008-11-17
bump :)

---

