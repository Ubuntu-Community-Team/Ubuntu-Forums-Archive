---
title: "mod_security in ubuntu 10.10"
date: 2011-01-22
forum: Security
---

### Post by szpuni on 2011-01-22
Hello,

I'm trying to run mod_security as an module with apache with ubuntu 10.10.

I have mod_security working but for some reason it doesn't filter any content.

I'm sure that apache running mod_security thanks to lsof
```
apache2 7674 www-data  mem    REG    8,1   272956 3670175 /usr/lib/apache2/modules/mod_security2.so
```Configuration file to enable configuration for mod_security is in file conf.d/mod-security
with content:
```
<IfModule security2_module>
Include modsecurity-rules/*.conf
Include modsecurity-rules/base_rules/*.conf
</IfModule>
```i have files downloaded from sourceforge.net with mod_security rules in this directory as in configuration file.

I have file in server with nasty bug view any file in a system like /etc/passwd and with all of this configured my php still give me content of passwd file instead of blocking request.

Do anybody have working mod_security in ubuntu server? 
Any ideas where i'm making mistake?

---

### Post by wojox on 2011-01-22
> **szpuni said:**
> 
Any ideas where i'm making mistake?

You need to upgrade or fix whatever bug you have that is giving out /etc/passwd file. I wouldn't rely on mod_security alone.

[How to mod_security Ubuntu 9.04]("http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/")

---

