---
title: "Apache: how to get mod_log_config?"
date: 2008-11-24
forum: Server Platforms
---

### Post by mdeen on 2008-11-24
I must be stupid or so, but I see mod_log_config in the Apache help files, but I don't have it installed (it's not in /usr/lib/apache2/modules/) and I can't find anywhere how to install it.


Can anyone help me with that? On Ubuntu 8.04.

---

### Post by Dr Small on 2008-11-24
I don't have it listed either.

---

### Post by mdeen on 2008-11-25
The reason I'm asking is because in the Mediawiki docs there is a suggestion when installing Squid, there is a [section describing how to change the Apache logging](http://www.mediawiki.org/wiki/Manual:Squid_caching) using mod_log_config.

If mod_log_config apparently isn't available, how can this be accomplished?

---

### Post by MJN on 2008-11-25
If you look at the [Apache page](http://httpd.apache.org/docs/2.0/mod/mod_log_config.html) for this module you will see that its status is 'Base' which means it is part of the core Apache build (unless you have explicitly removed it) hence all of the directives are already available to you for use.
 
Mathew

---

