---
title: "Website file location"
date: 2008-08-14
forum: Server Platforms
---

### Post by johan.alfa on 2008-08-14
Hello all,

The default file location for websites is /var/www
Is it recommended to use that folder or should I take my home folder as site root?

Two considerations:

Security
Ease of use ( root for /var/www versus normal user for home folder)

greetings,

Johan

---

### Post by jonabyte on 2008-08-14
if you use your home folder and need other users to upload to that location, you could run into issues, never tried it though.

---

### Post by windependence on 2008-08-14
The default location is in /var for a reason. IMHO using a home directory for document roots is not a good idea both from a security standpoint and an ease of use standpoint. You can always create symlinks to use files in your home of you need to. Of course you have to turn on follow symlinks in Apache but that's easy.

-Tim

---

### Post by kustomjs on 2008-08-14
its better to have it under /var/www/

---

### Post by 2smooth on 2008-08-14
> **windependence said:**
>  using a home directory for document roots is not a good idea both from a security standpoint 

Why?

---

