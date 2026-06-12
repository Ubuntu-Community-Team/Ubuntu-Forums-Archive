---
title: "How to remove/change /phpmyadmin link"
date: 2011-11-21
forum: Server Platforms
---

### Post by markomk on 2011-11-21
Hi,
I don't have experience with servers and I need little help.
After successfully installed Ubuntu Server, as well php5,phpmyadmin,sqlserver etc. I directed my IP to DNS. So, the  webpage working fine,problem is if I add /phpmyadmin on the dns name will shows the panel. How to change/remove this phpmyadmin? and if I do it, can I have some problem with the page?

Thank you.

---

### Post by volkswagner on 2011-11-21
Your post is a little hard to follow.

What panel are you referring to?

Can you post a screen shot of the web page?

Normally since /PhpMyAdmin is a sub directory, you don't need any DNS entries.  If your site is mydomain.com, you point your DNS A record to your ip address.  There is no need to point a DNS setting to mydomain.com/PhpMyAdmin.

---

### Post by markomk on 2011-11-22
> **volkswagner said:**
> Your post is a little hard to follow.

What panel are you referring to?

Can you post a screen shot of the web page?

Normally since /PhpMyAdmin is a sub directory, you don't need any DNS entries.  If your site is mydomain.com, you point your DNS A record to your ip address.  There is no need to point a DNS setting to mydomain.com/PhpMyAdmin.


Hmm..I installed moodle on apache, ubuntu server. I installed myphpadmin so I can add sql base for the moodle. So, if I type my domain.com will open moodle but if I type domain.com/phpmyadmin, the phpmyadmin panel will open. I want this /phpmyadmin link to remove/change somehow.I hope I give you more info.

---

### Post by satanselbow on 2011-11-22
Assuming (dangerous I know, but that's how I roll!) you may need phpmyadmin at a later date - for full dB backup etc you could add rewrite line in your .htaccess:

Something along the lines of:

Generates a 403
```
RewriteRule ^(.*/)?\\phpmyadmin/ - [F,L]
```

or to generate a 404:
```
RedirectMatch 404 /\\phpmyadmin(/|$)
```

You could also remove the phpmyadmin package altogether... or password protect it... rename it something obscure that is unlikely to be found easily... 

There are numerous solutions you just need to put a little bit of thought into it as to what suits you best and research the relative merits of each approach.

---

