---
title: "How to setup Selective (permission) access for Directories in Apache2 web server"
date: 2016-04-22
forum: Server Platforms
---

### Post by govindaraj2 on 2016-04-22
I am a new system admin and learning Ubuntu. 
I have to setup a  restricted (permission) for directories in Apache web server. 
The  scenario is as follows. The folders are,

```
/var/www/hrd/
/var/www/technical/
/var/www/management/
/var/www/data/
```

The users in hrd (HR Department) group must access /var/www/hrd/ contents only.

The users in technical group must access /var/www/technical/ contents only.

The users in management group can access all the contents.

All the users & groups can access the common /var/www/data/ directory.

How to implement this? Can anyone help me out? Thanks in advance.

---

### Post by slickymaster on 2016-04-22
*Thread moved to ***Server Platforms*** sub-forum*

---

### Post by Habitual on 2016-04-22
and by "restricted", do you intend to allow "users" to edit files in those locations?

---

### Post by Graham_Willis on 2016-04-25
It sounds a bit confusing that you want to restrict permissions to directories **in Apache Web Server**. If what you want to do is specific sites being able to be opened only by users in a given group, then AuthBasic over SSL and group authorization seems like the right response:

[http://httpd.apache.org/docs/current/howto/auth.html](http://httpd.apache.org/docs/current/howto/auth.html)

If you also want only users of a specific group to have access to the given directory, you can go with creating virtual FTP accounts (one account for each user in the given group) chrooted to the proper directories.

---

