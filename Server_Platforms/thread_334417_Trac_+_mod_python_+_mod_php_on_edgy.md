---
title: "Trac + mod_python + mod_php on edgy"
date: 2007-01-08
forum: Server Platforms
---

### Post by lnxtech on 2007-01-08
My webserver runs with mod_php5 and php4-cgi (using fcgid) on edgy.
I'm trying to migrate my Trac environment from another server to this one and use mod_python for my trac virtual host.

For some reason if I have mod_php5 loaded and mod_python loaded at the same time, when I go to my Trac homepage the apache error log gives show a mod_python Segmentation fault (11)
If i remove the php5 module and restart apache then Trac works fine.

I've done some searching on the net and found a couple different things that didn't seem to apply to me.
1. Version differences with expat <- I checked the python module and the system and they are the same
2. Mysql conflict with php and python <- I only have the php mysql libraries. I'm not using python for mysql
3. Sqlite conflict with php <- I remove the php4-sqlite and php5-sqlite packages

Any idea what else i can try?
Any help is appreciated

---

