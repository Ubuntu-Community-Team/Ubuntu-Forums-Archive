---
title: "Proper Apache Setup and workflow? (New to Ubuntu)"
date: 2007-11-16
forum: Server Platforms
---

### Post by FishGills on 2007-11-16
I've searched the forum as best I could for an answer to this, so I'm sorry if its a duplicate. :)

Typically, I usually just edit httpd.conf (Well, really my virtual host config) to point to where I want my site to run off of. 

I notice Apache in Ubuntu has this whole "sites-available" thing. Before I just go and redo the configuration, I'd like to try how Ubuntu is suppose to work. 

Is there a place I can get info on creating websites on ubuntu as well as the proper way to have users edit the content? I don't want to just brute force passed whatever Ubuntu has already setup.

---

### Post by kidders on 2007-11-18
Hi there,

Throwing everything into a single config file is very inextensible, and makes it unnecessarily difficult to alter apache configurations with scripts ... something that Ubuntu needs to be able to do, even if *you* don't. Most modern distros prefer a modularised approach over a monolithic config file, and then build their package managers & server configuration utilities around it, so I wouldn't recommend deviating from any distro's conventions, unless you know enough to be able to preempt and work around the problems you'd create.

Ubuntu's virtual host configuration works by storing self-contained config files for all virtual hosts in /etc/apache2/sites-available, and symlinking the ones you happen to want switched on in /etc/apache2/sites-enabled. /etc/apache2/apache2.conf then includes these with...```
Include /etc/apache2/sites-enabled/[^.#]*
```

Apache modules work the same way. As a result, installing & removing/disabling modules, and creating & destroying virtual hosts with scripts rarely involves editing any files, and is far less likely to break your web server.

There's more information in /etc/apache2/README. I would suggest taking a look at it.

---

