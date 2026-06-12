---
title: "Light httpd"
date: 2007-10-31
forum: Server Platforms
---

### Post by johnnyw on 2007-10-31
when trying to see wether I installed it ok it gives me this as a result

> johnnyw@johnnyw-desktop:~$ sudo lighttpd -t -f lighttpd.conf
2007-10-31 16:08:36: (configfile.c.901) opening configfile lighttpd.conf failed: No such file or directory 

---

### Post by koenn on 2007-10-31
unluess you have a lighttpd.conf in your home directory, you need to specify to absolute path to the file : eg

```
 lighttpd -t -f /etc/lighttpd/lighttpd.conf
```

---

### Post by johnnyw on 2007-10-31
[sudo] password for johnnyw:
Syntax OK
:KS 
:)

---

### Post by koenn on 2007-10-31
;)

---

### Post by johnnyw on 2007-10-31
> **koenn said:**
> ;)

I feel myself retarded

> 2007-10-31 21:16:39: (configfile.c.901) opening configfile lighttpd.conf failed: No such file or directory
johnnyw@johnnyw-desktop:~$ sudo lighttpd -D -f lighttpd.conf
2007-10-31 21:16:42: (configfile.c.901) opening configfile lighttpd.conf failed: No such file or directory
johnnyw@johnnyw-desktop:~$
johnnyw@johnnyw-desktop:~$ lighttpd -D -f /etc/lighhttpd/lighttpd.conflighttpd.conf
2007-10-31 21:17:31: (configfile.c.901) opening configfile /etc/lighhttpd/lighttpd.conflighttpd.conf failed: No such file or directory
johnnyw@johnnyw-desktop:~$


---

