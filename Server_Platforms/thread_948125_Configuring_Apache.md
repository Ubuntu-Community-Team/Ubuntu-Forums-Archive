---
title: "Configuring Apache"
date: 2008-10-14
forum: Server Platforms
---

### Post by Drezard on 2008-10-14
Just need a quick bit of help. 

I have run:

> 
apt-get install apache2 


So I have a default install. Where abouts is the DirectoryIndex variable??? Its not the apache2.conf or the default in the /sites-enabled.

Where is it?

Daniel

---

### Post by lykwydchykyn on 2008-10-15
/etc/apache2/mods-available/dir.conf

---

