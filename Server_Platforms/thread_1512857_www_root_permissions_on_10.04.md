---
title: "www root permissions on 10.04"
date: 2010-06-18
forum: Server Platforms
---

### Post by fred2028 on 2010-06-18
Every time I copy new files into /var/www/ or /etc/apache2/ or stuff like that I keep having to sudo chmod them to 777. Is there a way to make all files under /var/www/ and /etc/apache2/ and /etc/php5/ automatically 777?

---

### Post by Ryan Dwyer on 2010-06-18
You shouldn't need to. All those files should be owned by root and have the other+read permission so Apache can read them.

You *should* be required to authenticate to handle those files, otherwise any user on your server can deface your website.

---

### Post by fred2028 on 2010-06-21
> **Ryan Dwyer said:**
> You shouldn't need to. All those files should be owned by root and have the other+read permission so Apache can read them.

You *should* be required to authenticate to handle those files, otherwise any user on your server can deface your website.
I'm not logged in as root though

---

### Post by Ryan Dwyer on 2010-06-21
That's the whole idea. Regular users shouldn't be able to modify those files. Anyone in the admin group (probably you) should be able to use sudo to modify them.

If you're the only user on the server and it's just a test machine, you should consider moving the www folder into your home folder so you can develop easier.

---

### Post by dapperdanny77 on 2010-06-21
be aware that there's a meaning protecting config files - disabling this security measures makes your system vulnerable

it's always comfort vs. security - the more comfort the less security

---

