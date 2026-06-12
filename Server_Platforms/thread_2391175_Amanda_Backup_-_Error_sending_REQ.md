---
title: "Amanda Backup - Error sending REQ"
date: 2018-05-06
forum: Server Platforms
---

### Post by DerPC on 2018-05-06
Hi all.

My problem is a duplicate of this one : [https://bugzilla.redhat.com/show_bug.cgi?id=1492117](https://bugzilla.redhat.com/show_bug.cgi?id=1492117)

Although, it's on Ubuntu and Amanda 3.3.6 (latest version on Ubuntu 16.04 LTS)

Unfortunately, Ubuntu has chosen to use Linux Kernel 4.15 ( >=4.14) in Ubuntu 18.04 LTS, a kernel which renders my backup server unusable, so upgrading to 18.04 isn't an option (at least not for now) even if there's a solution available on that platform.

With that out of the way - is there any place I can download an (not much) older version of amanda? I found 3.3.5 in my cache, but that's way too old (lots of unfulfilled dependencies).

Also - Canonical - do you have a fix on the drawing table? (in case I have luck and a Canonical employee sees this :) )

Best

---

### Post by DerPC on 2018-05-12
Soo.... judging by the silence, nobody frequenting these forums is backing up their server using Amanda?

---

### Post by DerPC on 2018-05-14
Ok, for the future reference of others: 

a) this is a regression error ( this is an error that has happened before, and is being replicated again ).
b) this is a cascade error ( the problem manifests itself on one host and cascades down the line for N hosts, N being some or all remaining hosts in line ).

The problem is accessibility - if a client has a firewall (e.g. UFW) where Amanda is blocked, then Amanda will fail that host. Unfortunately (for me and everyone else that will experience this) it will also fail all other hosts down the line.

The problem manifested itself when a 16.04 LTS server was upgraded to 18.04 LTS. That server came up with UFW and blocked Amanda.

---

