---
title: "php.ini gd.ini parsed but not enabled"
date: 2009-04-06
forum: Server Platforms
---

### Post by mobcdi on 2009-04-06
According to my phpinfo file the gd.ini file is parsed, thats supposed to enable gd but the software (drupal) says its not.

The gd.ini just has an entry for extension=gd.so which is located in a folder called 20060613+lfs in the php5 folder

Is there some commands a newbie can run to see where the problem lies?
Or does the gd.so need to be located somewhere else but I'm hoping to avoid making too many config changes from the installed settings

I'm using hardy if it helps

---

### Post by mobcdi on 2009-04-06
Should also add I've installed plesk 8.6 on the server to help manage it before creating any websites.

I'd like to narrow down any root php5,apache2 issues before going further up the software tree to drupal

---

### Post by mobcdi on 2009-04-07
I read that the php5-gd that comes with ubuntu 8.04 doesn't include all the necessary libraries that are available if I compiled my own version from the source files. So while gd may be installed its not the full fat version

Is this true?

---

