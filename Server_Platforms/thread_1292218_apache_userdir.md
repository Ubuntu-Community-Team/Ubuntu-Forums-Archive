---
title: "apache userdir"
date: 2009-10-15
forum: Server Platforms
---

### Post by theeal on 2009-10-15
I'm new to this and I need help with:
were and how do I set a uerdir in apache
all I have searched at google are poorly or give me error.
Please help me

---

### Post by kestrel1 on 2009-10-15
I think what you are after is a www folder in /var
So something like:
sudo mkdir /var/www
I could be wrong though.

---

### Post by diesch on 2009-10-15
Run
```
sudo a2enmod userdir
```
and edit /etc/apache2/mods-enabled/userdir.conf if you don't like the defaults.

---

### Post by theeal on 2009-10-16
Do I need to enable something from apache2.conf or httpd.conf

or is there somthing else?
(i heve run the "sudo a2enmod userdir" command)

---

### Post by theeal on 2009-10-16
Oh, I forgot to put the address *~userdir...
SOLVED

---

