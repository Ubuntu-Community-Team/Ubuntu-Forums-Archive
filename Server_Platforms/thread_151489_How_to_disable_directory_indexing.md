---
title: "How to disable directory indexing?"
date: 2006-03-28
forum: Server Platforms
---

### Post by hcker2000 on 2006-03-28
I have tryed making .htaccess files with no luck. I checked threw webmin and can't seem to find a seting that disables it. ](*,) 

If any one could help that would be great.

---

### Post by LordHunter317 on 2006-03-28
Globally?  In a single directory?  Details?

In /etc/apache2/sites-enabled/000-default removing Indexes from the Options for / ought to do it for most of the site, but you have to give details.

---

### Post by hcker2000 on 2006-03-29
Globally would be best and would like the ability to be able to disable it for a few directories.

---

