---
title: "Use Samba accounts for htaccess?"
date: 2009-11-12
forum: Server Platforms
---

### Post by renzokuken on 2009-11-12
Hi,

i have a ubuntu server that runs as our domain controller and filestore for people in our group. everyone has their own samba login and usernames for the domain so they can log in from xp based pcs.

i've recently set up a local web server on the server to run a private "intranet" website for our group.

to protect it from unauthorised access i've used the htaccess file to create a single username and password for everyone to use when accessing the site (through their browser).

instead of using this single login u/n and p/w combo......is it possible to use their existing samba credentials to log into the site instead?

cheers

rob

---

### Post by Ilalmi on 2009-11-12
Hi Rob,

try modntlm ([http://modntlm.sourceforge.net/](http://modntlm.sourceforge.net/)). It worked for me.

Regards,
Ilalmi

---

### Post by renzokuken on 2009-11-12
perfect, will check it out,

thanks Ilalmi

---

