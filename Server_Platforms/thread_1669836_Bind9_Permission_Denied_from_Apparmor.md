---
title: "Bind9 Permission Denied from Apparmor"
date: 2011-01-18
forum: Server Platforms
---

### Post by edthetoad on 2011-01-18
When I attempt to start bind9 I see in the system log 
/etc/bind/named.conf.local:4: open:/home/administrator2/apples.conf: permission denied
type=1400 audit(1295359149.893:40): apparmor="Denied" operation="open" parent=7421 profile="usr/sbin/named" name="home/administrator2/apples.conf" pid=7426 comm="named: requested_mask="r" denied_mask="r" fsuid=115 ouid-115

I have moved the configuration file that bind is trying to load to my home folder.  I have changed the owner to bind and ran bind as root.  How do I make bind load this file?

---

### Post by SeijiSensei on 2011-01-18
> **edthetoad said:**
> I have moved the configuration file that bind is trying to load to my home folder.  I have changed the owner to bind and ran bind as root.  How do I make bind load this file?

What are the permissions on your home folder?  You'll need at least 0755 so that named can read the file.

Moving configuration files for servers is almost never a good idea.

---

### Post by edthetoad on 2011-01-21
I moved the configuration file back set the permission to 0755 and it now just says /etc/bind/named.conf.local:4: open: /usr/local/samba/private/named.conf: permission denied.  What should i do now?

---

### Post by SeijiSensei on 2011-01-21
> **edthetoad said:**
> I moved the configuration file back set the permission to 0755 and it now just says /etc/bind/named.conf.local:4: open: /usr/local/samba/private/named.conf: permission denied.  What should i do now?

Fix line four of /etc/bind/named.conf.local so it points to the correct location.

---

