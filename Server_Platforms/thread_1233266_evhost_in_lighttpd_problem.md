---
title: "evhost in lighttpd problem"
date: 2009-08-06
forum: Server Platforms
---

### Post by cybernet on 2009-08-06
I'm Using Ubuntu 9.04 Desktop
my config file [http://paste.lighttpd.net/358](http://paste.lighttpd.net/358)
i set my document-root to /var/www/domain.ro/public_****
and my evhost.path-pattern = "/var/www/%0/i/%3"

what i'm trying to do is
when i access cyberfun.ro - the doc root should be here /var/www/domain.ro/public_****
when i access any subdomain of domain.ro i wanna be here /var/www/%0/i/%3 - in english /var/www/domain.ro/i/any-subdomain



--- what i get
if i access domain.ro the doc root is /var/www/domain.ro/i/ - i don't wanna to be this because i have the subdomains there and i can't put nothing there
if i access any-sub.domain.ro - everything is working as it should

please help me

thanks in advance
sorry for my bad English

---

### Post by cybernet on 2009-08-07
bump:)

---

