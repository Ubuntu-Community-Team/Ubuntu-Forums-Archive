---
title: "Apache still not working ..."
date: 2006-02-21
forum: Server Platforms
---

### Post by dbee on 2006-02-21
Can anyone help...

My apache server won't parse php files 

Have I restarted the apache server ?

Yes, numerous times ...

Do I have php installed ?

Well, according to synaptic I do. But then according to synaptic I've mod-sec installed as well. I can't find a trace of either of them in mods-enabled or apache.conf - I had to uncomment both of these lines myself for some reason

AddType application/x-httpd-php .php
AddType application/x-httpd-php .phps

Why isn't my apache parsing php files ?????
Where is mod-sec ???
Why am I using ubuntu as a LAMP server ?????

Thanks :o

---

### Post by heimo on 2006-02-21
Do you have the php modules in modules-available directory? If so, enable them using a2enmod [modulename].

---

