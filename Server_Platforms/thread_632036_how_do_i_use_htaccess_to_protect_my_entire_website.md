---
title: "how do i use htaccess to protect my entire website?"
date: 2007-12-05
forum: Server Platforms
---

### Post by winstonzeng on 2007-12-05
how can i use htaccess to protect my entire website and all the directories under it? i can get htaccess to protect a folder but it doesn't protect all the files in the folder.

here is an example.
[https://24.85.38.53](https://24.85.38.53) is protected with .htaccess and .htpasswd but [https://24.85.38.53/cgi-bin/nph-proxy.cgi](https://24.85.38.53/cgi-bin/nph-proxy.cgi) isn't protected...

---

### Post by colo on 2007-12-05
That's because /cgi-bin/ is (usually) a ScriptAlias virtual directory. You can control its access configuration in the configuration file where the ScriptAlias is defined, in much the same manner as you did in your .htaccess for an actual directory under your webserver's DocumentRoot.

---

### Post by winstonzeng on 2007-12-05
how would i change the config of the scripallias? im using apache2 and in sites-avaliable i changed scripallias to allowoverride none to all. i did the same in the ssl config file too but no luck.

---

### Post by winstonzeng on 2007-12-05
bump

---

### Post by winstonzeng on 2007-12-06
bump

---

### Post by colo on 2007-12-06
Could you please post the configuration for the VHost in here?

---

### Post by rbprogrammer on 2007-12-06
OP, did you try using [Webmin]("http://www.webmin.com/")??  i use it for my web server, and it was quite easy.  and no knowledge of configuration files is needed.

---

### Post by winstonzeng on 2007-12-06
hmmm. ill fiddle around with webmin and see what i can do. thanks

well, i cant get it to work using webmin. heres my config files

[https://24.85.38.53/files/default](https://24.85.38.53/files/default)
[https://24.85.38.53/files/ssl](https://24.85.38.53/files/ssl)

---

### Post by winstonzeng on 2007-12-07
ooo okay. i solved it. all you have to do is put the .htaccess file in your scriptalias directory. in my case, i put the .htaccess in /usr/lib/cgi-bin/

---

