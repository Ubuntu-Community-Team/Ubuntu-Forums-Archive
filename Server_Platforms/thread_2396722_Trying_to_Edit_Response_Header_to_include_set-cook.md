---
title: "Trying to Edit Response Header to include set-cookie secure and httponly flags"
date: 2018-07-20
forum: Server Platforms
---

### Post by Robert_Boutin on 2018-07-20
Ok, so this is driving me absolutely crazy.  For security purposes, I need to modify my response header to include httponly and secure flags in the format:

*Set-Cookie: <name>=<value>[; <Max-Age>=<age>] [; expires=<date>][; domain=<domain_name>] [; path=<some_path>][; secure][; HttpOnly]*

but I have no idea which file to edit.  I've tried Googling to find where to head but without success.  Can anyone tell me in which file I would add this line?

My server runs Ubuntu 16.04 Server, Apache 2.4.34, PHP 7.0.30.

Thanks for any/all assistance.

---

