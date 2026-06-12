---
title: "Apache Mod_Rewrite issues"
date: 2010-10-19
forum: Server Platforms
---

### Post by xebedee on 2010-10-19
Help! After an upgrade (in 10.04 Server) Mod_Rewrite doesn't work.[INDENT]a2enmod rewrite doesn't error & Apache has been restarted

apachectl -M shows rewrite_module (shared)

the host config file has AllowOveride All

but only putting in index.php works
[/INDENT]Any ideas would be greatly appreciated.

---

### Post by xebedee on 2010-10-19
I discovered that rewrite.conf was missing from mods-available & mods-enabled

I added RewriteEngine On to it - and restarted Apache, but still no luck :-(

Adding a RewriteLog (level 9) to the host doesn't produce anything either.

---

### Post by Ahriman on 2010-11-28
Hi

you've marked this as solved, but haven't explained how you solved it. Can you elaborate, please?

---

