---
title: "How to create a subdomain for your forum?"
date: 2008-09-07
forum: Server Platforms
---

### Post by 2smooth on 2008-09-07
I want to change the url of my forum from

[www.mysite.com/forum](www.mysite.com/forum) to forum.mysite.com?

Do i have to create a new vhost for apache?
Or their drawback to this url?

Thanks

---

### Post by hyper_ch on 2008-09-07
either vhost or rewrite

---

### Post by volkswagner on 2008-09-07
I just went trough this.  I would create another vhost in apache.  Just have it point to the current location of the root directory for the currently running site.  That is all you should have to do.

In case you did not know, you will need to create the subdomain/host url at your dynamic resolve provider, or at you registrar if you have a static ip.

EDIT:  If you already have a vhost for this site, you can just edit the config file and change the name to forum.yoursite.com

---

### Post by Dmitrey on 2010-03-23
I have similar problem, forum.mysite.com is required, mediawiki installed on my server overwrites all paths with wiki keywords.
Now my apache2.conf looks like this:

   Alias /forum/index.php /usr/share/phpbb3/www/index.php
   Alias /skins /var/lib/mediawiki/skins
#   Alias /index.php /var/lib/mediawiki/index.php/
   Alias /images /var/lib/mediawiki/images/
   Alias / /var/lib/mediawiki/index.php/
  <Directory /var/lib/mediawiki>
     Options -Indexes
   </Directory>
But iw works only for /forum/index.php, other phpbb paths are overwritten by mediawiki.
Can anyone explain what should I change? I cannot remove  "Alias / /var/lib/mediawiki/index.php/" because it is required to have wiki paths like mysite.org/asdf.
I'm not a webmaster but haven't possibility to hire professional, can anyone explain rather precisely or give a link into detailed instructions?
Thank you in advance, D.

---

