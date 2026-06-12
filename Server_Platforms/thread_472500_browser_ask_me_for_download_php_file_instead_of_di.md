---
title: "browser ask me for download php file instead of displaying it"
date: 2007-06-13
forum: Server Platforms
---

### Post by conchimartin on 2007-06-13
I've followed all steps in [URL="https://help.ubuntu.com/community/ApacheMySQLPHP#head-67cb901b98d8dd3892cec7ebf48e961c6f19467f"]ApacheMySQLPHP
[/URL] page but I cannot display php files.

When I write

sudo a2enmod php5

I obtain:

This module does not exist!

But the module is installed. Any idea ??? :(

---

### Post by conchimartin on 2007-06-13
I think that php5.load file must be in mods-enabled folder when I install php5 and others packages listed in  but  I haven't got it...
I've reinstalled php5 package and nothing... any idea ??

---

### Post by conchimartin on 2007-06-13
OK. I've solved it.
I've only need to reinstall libapache-mod-php5, and php5.load file have appeared correctly in mods-available folder.

---

