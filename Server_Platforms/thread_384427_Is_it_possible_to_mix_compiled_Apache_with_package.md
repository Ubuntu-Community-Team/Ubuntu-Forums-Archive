---
title: "Is it possible to mix compiled Apache with packages?"
date: 2007-03-14
forum: Server Platforms
---

### Post by ujeezy on 2007-03-14
Hi all,

I just compiled Apache 2.2  for the mod_proxy_balancer support.  I then executed the following command:

 apt-get install libapache2-mod-php5 php5-mysql

Now, I'm having trouble restarting Apache ... if I compile Apache, do I have to compile all my modules as well (i.e., PHP)?

Thanks

---

### Post by arvindkst on 2007-03-14
Ideally you need not compile apache you will need to compile the module into apache with axps, this can be done with the apache-dev package.

---

### Post by ujeezy on 2007-03-14
That would be ideal but unfortunately, Apache 2.2 seems to be requisite for mod_proxy_balancer.  Assuming that I do have to compile Apache 2.2 from source, does this mean I have to do the same for PHP/ZLib/SSL/etc? Is this where apxs would come in?

Also, let's say three months down the line, I decide I want FastCGI support or something like that -- how traumatic will it be for my system if I need to recompile Apache? I'm pretty ignorant of where libraries, shared objects, modules, etc. come into play -- is there a guide somewhere that explains all of this? 

Thanks!

---

