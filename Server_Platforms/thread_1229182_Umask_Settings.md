---
title: "Umask Settings"
date: 2009-08-01
forum: Server Platforms
---

### Post by zemon_ on 2009-08-01
I want all uploaded files and folders to have permissions 777 what umask value should I use?

Im editing the umask in these config files.

/etc/proftpd/proftpd.conf

/home/user/.profile

Is this correct?

---

### Post by quixote on 2009-08-03
You can think of the umask as subtracted from 777.  So a umask of 022 means permissions will be set to 755.  So to get 777, the umask should be 000.

That said, are you absolutely sure you really want to set default permissions on all new files to 777?  Or are you doing that because you're trying to get something to work that permissions are interfering with?  If the latter, it's really a bad idea to do it this way.  I'm not familiar with proftpd.conf, but be sure you know all the consequences before changing defaults in any system files, like config files in /etc.

---

