---
title: "dpkg"
date: 2008-12-31
forum: Server Platforms
---

### Post by quikone8 on 2008-12-31
I was trying to install LAMP and get the following error;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

When I run this it just seems to stall.  Is there any way to get around this?

---

### Post by linux_tech on 2008-12-31
run this
```
dpkg --configure -a
```
then try LAMP install again

---

### Post by quikone8 on 2008-12-31
> **linux_tech said:**
> run this
```
dpkg --configure -a
```
then try LAMP install again

I tried the above code, the machine just sits there and does nothing, I waited for almost an hour.

This is what happens when I run dpkg --configure -a

ron@tolmarket:~$ sudo dpkg --configure -a
Setting up phpbb2-conf-mysql (2.0.22-3) ...
Creating MySQL database...
Creating MySQL user...
Creating MySQL tables if they don't exist yet...
Creating phpbb_sessions_keys table if it doesn't exist yet...
Creating search_time column if it doesn't exist yet...
dpkg: error processing phpbb2-conf-mysql (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 phpbb2-conf-mysql

I finally enter Ctrl+C to terminate

---

### Post by quikone8 on 2009-01-03
> **quikone8 said:**
> I tried the above code, the machine just sits there and does nothing, I waited for almost an hour.

This is what happens when I run dpkg --configure -a

ron@tolmarket:~$ sudo dpkg --configure -a
Setting up phpbb2-conf-mysql (2.0.22-3) ...
Creating MySQL database...
Creating MySQL user...
Creating MySQL tables if they don't exist yet...
Creating phpbb_sessions_keys table if it doesn't exist yet...
Creating search_time column if it doesn't exist yet...
dpkg: error processing phpbb2-conf-mysql (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 phpbb2-conf-mysql

I finally enter Ctrl+C to terminate

Bump

---

### Post by seshomaru samma on 2009-01-05
i have the same problem
i used ```

 sudo aptitude remove phpbb2-conf-mysql --purge
```
to free apt
are you using hardy?
i think the best way would be to install phpbb from their website

---

