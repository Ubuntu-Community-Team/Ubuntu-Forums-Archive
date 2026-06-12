---
title: "Trac loose LDAP authentification after karmic upgrade"
date: 2009-11-03
forum: Server Platforms
---

### Post by ploum on 2009-11-03
Hello,

For years (at least 18 months), I've been using Trac with LDAP authentification over Apache. I don't remember how I configured this (probably on a Hardy installation) but it has worked since then accross multiple upgrades until… Karmic !

Indeed, now Trac replies that : "Authentication information not available" (see [http://bug.fritalk.org/login](http://bug.fritalk.org/login) ) and I've no idea at all on how I can solve that problem.

I never installed anything in the Trac projects themselves and they haven't been touched by the upgrade.

Does anybody here has a working Trac+LDAP setup on Karmic ?

Thanks in advance.

---

### Post by ploum on 2009-11-13
The solution was found here :
[http://trac.edgewall.org/ticket/3821](http://trac.edgewall.org/ticket/3821)

in /etc/apache2/conf.d/localized-error-pages

comment out the line :

ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var


Restart apache : it does the trick.


Really strange!

---

