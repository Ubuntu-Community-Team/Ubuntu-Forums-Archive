---
title: "php5 error"
date: 2008-09-21
forum: Server Platforms
---

### Post by yodomino6 on 2008-09-21
I just installed php5, and got some errors while doing so. One looking like:
```
apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/mod_mono_auto.load: Cannot load /usr/lib/apache2/modules/mod_mono.so into server: /usr/lib/apache2/modules/mod_mono.so: cannot open shared object file: No such file or directory
```

I get that error every time I start Apache. I assume it's an easy fix somewhere... (fingers crossed)

---

### Post by mbeach on 2008-09-22
if you don't need the mod_mono, comment out that line.  It would appear that your attempts for asp have not been successful.  It really has nothing to do with a php error.

edit the /etc/apache2/apache2.conf as pointed out in the error and either comment or remove that line (185), or edit the mod_mono_auto.load and comment out line 1.  Not knowing exactly what line 185 is, I'd probably start with disabling mod_mono (something like a2dismod mono [that's a guess])

this is not a php error, but an asp/mod_mono issue.  

have you read and followed:
[https://help.ubuntu.com/community/ModMono](https://help.ubuntu.com/community/ModMono)

Good luck.

---

### Post by yodomino6 on 2008-09-22
Ah, I just assumed it was because it only appears when I enable php5. ANYWAYS... I tried disabling mono (it ended up being a2dismod mod_mono) and it says "Module mod_mono already disabled"
I tried disabling line 185 of that other one, and that just caused another message:

Syntax error on line 143 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration

---

