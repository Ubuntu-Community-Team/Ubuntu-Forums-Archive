---
title: "Webmin won't autostart in edgy"
date: 2006-10-13
forum: Server Platforms
---

### Post by quackking on 2006-10-13
Hi. I'm not sure this is the correct forum for this post; if it belongs someplace else, I apologize, and ask the admins to move it. 

I have several Dapper servers, and I use Webmin 1.300 to administer them. I installed Webmin from webmin.com and not from the repositories. Webmin is configured as if it is running on a Debian 3.0 system. All works great.

I have set up a test machine using Edgy Eft, with all current updates done at least once a day. 

Ever since Edgy moved to upstart instead of sysvinit, I have to manually start Webmin, which is a real pain. On all of my other machines I made use of the question at the bottom of the webmin config page which asks if you want Webmin to start at system startup. This writes some files to /etc/init.d/rc.d/webmin. Despite cloning this directory structure, the Webmin auto-start function no longer works at all using upstart.

I know this falls into the netherworld - is it Webmin's fault or upstart? Personally I believe that upstart ought to completely emulate sysvinit behavior for something like this, and I am pretty sure that others will have this problem too.

Is there a HOWTO I can follow to make this work? - or better, can something be done to assure upstart compatibility with old sysvinit behavior?

---

### Post by ranf on 2006-10-15
> **quackking said:**
> This writes some files to /etc/init.d/rc.d/webmin. 

There is no such sub dir (/etc/init.d/rc.d) on Debian based distros.

---

