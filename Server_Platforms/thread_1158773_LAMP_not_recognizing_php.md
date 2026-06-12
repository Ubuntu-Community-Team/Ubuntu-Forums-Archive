---
title: "LAMP not recognizing php"
date: 2009-05-14
forum: Server Platforms
---

### Post by piratebill on 2009-05-14
I have a working php website on a campus web server, but I need to move the site to another server.  At home I run a ubuntu file server and figured, heck I might as well host it from home until I can find a more permanent solution.  using tasksel I installed LAMP.  Basic Html files work, but every time I want to access something with php, firefox prompts me to save the file.  How can I get apache to render the php?  Thanks in advance :)

---

### Post by piratebill on 2009-05-14
Wow.....I dont know how but since posting this thread, it suddenly works, even after a reboot.  I have no idea how or why though.  Any idea why it suddenly decided to work?:confused:

Anyways, thanks for reading.

---

### Post by a9k3d on 2009-05-14
Often seeing php code instead of having it work is a symptom of not enabling the mod_php module. Next time you can check /etc/apache2/mods-enabled/ to see if php is in there.

If adding mod_php was a recent change you may need an apache restart to get the module loaded.

---

### Post by mbeach on 2009-05-14
It may have have been a cache issue with your browser.

Some related reading:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

---

### Post by atomicarena on 2009-05-29
hi,

I think its a problem of cache. I just restarted the system and everything was fine then. I think mere restarting firefox should also resolve this problem of php not being recognized by the browser.

This forum post did help me lot.

Thanks
Praveen Kannan

---

