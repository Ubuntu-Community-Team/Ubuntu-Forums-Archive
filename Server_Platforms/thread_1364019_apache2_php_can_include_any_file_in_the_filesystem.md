---
title: "apache2: php can include any file in the filesystem"
date: 2009-12-25
forum: Server Platforms
---

### Post by extruct on 2009-12-25
Hi there.
I installed ubuntu 8.04 on my home server. I set up one VirtualHost for apache that I'm currently using.

The problem is that inside php script I can include any file in my filesystem (/etc/passwd for example).

I don't think it should be like this cause its a fatal security flow.

The same applies for non virtual host (files inside /var/www)

Is this normal?
Thanks.

[EDIT]
Ok not any file, /var/log/* for example gives me access denied, /etc/shadow also, still some files can be included why so?

---

### Post by Bachstelze on 2009-12-25
> **extruct said:**
> 
[EDIT]
Ok not any file, /var/log/* for example gives me access denied, /etc/shadow also, still some files can be included why so?

Any file PHP has reading permission to can be included, because that's how it works. If you don't want that, you can chroot it, or use ACLs to deny it permission to read sensitive files.

---

### Post by craigp84 on 2009-12-25
What Bachstelze said is spot on.

An extra option to add to that would be wrap apache (or php itself if you're not using mod_php) using AppArmour to deny access to all but specific directories.

---

