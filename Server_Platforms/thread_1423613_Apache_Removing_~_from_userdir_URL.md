---
title: "Apache: Removing ~ from userdir URL"
date: 2010-03-06
forum: Server Platforms
---

### Post by reduxtion on 2010-03-06
I have read the Apache URL Rewriting guide and it gave me this mod_rewrite snippet ...

> RewriteEngine on
RewriteRule   ^/~(([a-z])[a-z0-9]+)(.*)  /home/$2/$1/.www$3

My question is, where is this file so I can edit it?

---

