---
title: "Dnsmasq custom redirection"
date: 2016-09-28
forum: Server Platforms
---

### Post by fraizor on 2016-09-28
I'm trying to make a custom DNS redirection

if the user visited "natick.com/3456" then he will be redirected to "aiman.com/redirect.php?id=3456"

is that even possible through dnsmasq ? 
if not possible what would be another solution/workaroud ?

---

### Post by SeijiSensei on 2016-09-28
No, but it would be possible if you were in control of the server for natick.com.  Apache, for instance, allows you to rewrite incoming URLs or redirect queries to other locations.  

DNS cares only about hostnames.  It doesn't handle URLs at all.

---

