---
title: "enabling python with apache"
date: 2010-06-25
forum: Server Platforms
---

### Post by Jordanwb on 2010-06-25
I'm trying to get python to work with apache using the mod_python module. I've activated it like so:

```
sudo a2enmod mod_python
```

and added "index.py" to the list of types in /etc/apache/mods-enabled/dir.conf and ran "sudo /etc/init.d/apache restart". When I browse to my python file, it prompts me to download the file instead of parsing it. i've read that I have to add "AddHandler python-program .py" but I don't know where to put that.

---

### Post by koenn on 2010-06-25
in the Directory definition

see also
[http://ubuntuforums.org/showpost.php?p=792999&postcount=3](http://ubuntuforums.org/showpost.php?p=792999&postcount=3)

---

### Post by Jordanwb on 2010-06-25
Thanks that works.

---

### Post by koenn on 2010-06-25
cool.

---

