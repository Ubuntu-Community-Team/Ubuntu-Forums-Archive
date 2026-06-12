---
title: "sql problem"
date: 2011-06-24
forum: Server Platforms
---

### Post by mclovin000 on 2011-06-24
I cant get sql to run on 11.04 any suggestions?  Installed fog server and it says that sql is installed but i cant connect to database

---

### Post by ruffEdgz on 2011-06-24
I'm guessing you are talking about MySQL? If you are, is the service on?

Check for me:
```

sudo service mysql status

```

If it doesn't show it running, start the process up:
```

sudo service mysql start

```

If you are still having any more issues, please provide more detail about your issue so we can help you even better.

---

### Post by mclovin000 on 2011-06-24
ok I checked the status of mysql and its already running. what more info do you need? so lost!

---

### Post by ruffEdgz on 2011-06-24
Well, how are you trying to access the database? What command are you using? Are you using any documentation for this FOG server you are trying to setup?

I found one bit of documentation on FOG and it looks cool but it would be wise to understand what are the major components of the service, how does the service work and what else I need to know by getting more involved with the FOG project.

Here are some things I found for documentation:
[http://www.fogproject.org/wiki/index.php?title=Ubuntu_10.04#Ubuntu_10.04](http://www.fogproject.org/wiki/index.php?title=Ubuntu_10.04#Ubuntu_10.04)

[http://www.fogproject.org/?q=node/5](http://www.fogproject.org/?q=node/5)

---

### Post by mclovin000 on 2011-06-24
trying to access it by going to [http://192.168.0.23/fog/management](http://192.168.0.23/fog/management)

i got documentation from the fog website

gonna try the links u sent, thanks 4 ur help

---

### Post by Dangertux on 2011-06-24
This might seem like a no brainer , but did you create a database, user and grant appropriate permissions for FOG?

---

### Post by mclovin000 on 2011-06-24
Sure didnt.... you got a link on how to do that? those werent in my instructions :(

---

### Post by Dangertux on 2011-06-24
These two links should have all the information you need however the part I think you're getting caught up on is that by default FOG tries to login as root on MySQL with no password.

This can be edited in the /fog/commons/config.php file.

You can either supply it with the root (note this is the password you set for MySQL root not the root account in Ubuntu) password, or possibly grant it it's own username and database, with mysqladmin. For further information about that consult the two links. I put them in order of what I felt would be more relevant but both seem to contain the information you seek.

[http://sourceforge.net/projects/freeghost/forums/forum/730843/topic/2252518](http://sourceforge.net/projects/freeghost/forums/forum/730843/topic/2252518)
[http://www.fogproject.org/wiki/index.php?title=FOGUserGuide](http://www.fogproject.org/wiki/index.php?title=FOGUserGuide)

---

