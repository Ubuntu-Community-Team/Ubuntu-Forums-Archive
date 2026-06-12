---
title: "Dokuwiki has gone 404 after 13.10 upgrade"
date: 2013-10-21
forum: Server Platforms
---

### Post by halfbeing on 2013-10-21
Yesterday I upgraded to 13.10 and now Apache2 says that my Dokuwiki wiki is 404. During the upgrade I opted to keep my existing configuration files. I don't know if this was the right thing to do, but I have tried removing them and doing  re-install of the Dokuwiki package, but it makes no difference. This is turning into a major crisis. Does anyone know how I can fix this?

Many thanks.

---

### Post by koenn on 2013-10-21
dokuwiki is just a handfull of php on a webserver, not much can go wrong there  (-> *famous last words*)

- check your apache logs to see where the "not found" happens, i.e. what file/url is failing
- look through your apache config files to see if you still have a site pointing to  /var/lib/dokuwiki/
- see if you still have dokuwiki content in /var/lib/dokuwiki/data/pages/

---

### Post by halfbeing on 2013-10-21
Thanks for replying, koenn. In the end I decided that the easiest thing would be to get rid of the Ubuntu package of Dokuwiki altogether and instead install the tarball directly into /var/www. That way I don't have to worry about messed up aliases and I won't won't ever have to worry again about what the next upgrade will do to me. My wiki's a bit messed up now because of the change in version and the messy copying, but at least I can see my pages.

---

### Post by koenn on 2013-10-21
yeah, tarbal vs. repo packages, I still don't know which route is best. I usually prefer the effort of Debian/Ubuntu package maintainers to try and separate data from program and presumably make the setup somewhat more secure than "just dump everything in /var/www", but even so, it sometimes looks like this sort of applicationss wasn't meant tp be packaged. 
Never had any trouble with dokuwiki in particular, though.  

> won't ever have to worry again about what the next upgrade will do to me
Theoretically, if the tarbal version gets too far ahead of the repo version and starts to critically depend on  php module versions  or other stuff that is newer than what's available in the repo's, you may still have issues if you try  to upgrade *dokuwiki* itself. But you're probably right about not having to worry about OS upgrades.

---

### Post by halfbeing on 2013-10-21
You're right to mention the security aspect. In my case I use Dokuwiki for a private wiki and journal so I'm less worried about other people breaking in and more worried about losing access to everything I have collected and written. One plus point about having everything in /var/www is that if I ever need to switch to another operating system my wiki can come with me.

---

