---
title: "Webmin and apache"
date: 2007-05-21
forum: Server Platforms
---

### Post by sefs on 2007-05-21
The situation
----------------

Apache, BIND and webmin installed

I've set up two zones in BIND  a.lan and b.lan.  they both resolve to the same ip address.

I want to set up to virtual servers (webmin speak)  where the directores are in two different locations on the same hard disk.

But when i do this in webmin, and type in a.lan or b.lan they all go to the same directory.  What i am trying to do is get a.lan directed to one directory and b.lan to another.

How can I successfully set up these "virtual servers" via webmin to operate like that.

---

### Post by Brazen on 2007-05-21
Must it be done through Webmin?  I love Webmin, but Apache config is one thing I prefer to do through the text config files.

Basically you need to add the 'ServerName' directive to each of your virtual hosts.  One would be 'ServerName a.lan' and the other would be 'ServerName b.lan'.

If you want, post the contents of any files under /etc/apache/sites-available/ and I (or someone else here) can have a look at them and help you out better.

---

