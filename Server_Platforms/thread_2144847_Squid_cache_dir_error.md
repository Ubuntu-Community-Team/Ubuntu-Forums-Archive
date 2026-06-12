---
title: "Squid cache dir error"
date: 2013-05-13
forum: Server Platforms
---

### Post by umfunix on 2013-05-13
I've installed squid 3 on a ubuntu 32 bit server with all the default installs.

Whenever I enable (uncomment) the default cache dir, squid doesn't want to start.  I've checked that the actual directory does exist and I've run squid3 -z to initialise.

What could be the issue?

---

### Post by SeijiSensei on 2013-05-13
Does it have the right permissions?  It probably needs to be owned by squid:squid.  What do the logs report?

---

### Post by umfunix on 2013-05-14
Hi, I can't see any reason for not starting - just typed in sudo service squid3 start but checking the status shows stop/waiting.

---

### Post by umfunix on 2013-05-14
How do I ensure the permissions is right?

---

### Post by SeijiSensei on 2013-05-14
1)  Did you look at /var/log/squid3/cache.log?  What errors do you see?

2)  Navigate to wherever the cache is stored and use "ls -l" to see what the user and group ownerships are.  The user and group that owns the cache directories need to match the values assigned to the "cache_effective_user" and "cache_effective_group" directives in squid.conf.

---

### Post by umfunix on 2013-05-15
Hi

Thanks!!!!  It seemed to be directory/file ownership!  Got it to work.

---

