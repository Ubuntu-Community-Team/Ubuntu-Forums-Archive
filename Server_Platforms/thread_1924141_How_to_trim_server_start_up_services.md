---
title: "How to trim server start up services?"
date: 2012-02-12
forum: Server Platforms
---

### Post by l3ecl on 2012-02-12
I've been playing with my server quite a while and I noticed that I have a lot more background services running. How do I prevent these services from starting automatically during boot?

---

### Post by savanna on 2012-02-12
Services are started using init scripts:

% runlevel
N 2

% ls /etc/rc2.d
(it's runlevel 2 so look in the rc2.d directory)

% cat /etc/rc2.d/README --> gives you some doco
The scripts in this directory are executed each time the system enters
this runlevel.
...


To stop services from running at startup, you can rename the S files to K files as per the README, or use update-rc.d. See man update-rc.d:

% man update-rc.d

NAME
       update-rc.d - install and remove System-V style init script links

---

### Post by Deuce1912 on 2012-02-12
You can also install "Boot Up Manager" for a graphical interface if that's easier and if you have a desktop manager for your server. (Some people do, and some people don't)

sudo apt-get install bum

then run bum and uncheck anything you don't need.

- Deuce1912

---

### Post by l3ecl on 2012-02-12
> **Deuce1912 said:**
> You can also install "Boot Up Manager" for a graphical interface if that's easier and if you have a desktop manager for your server. (Some people do, and some people don't)

sudo apt-get install bum

then run bum and uncheck anything you don't need.

- Deuce1912

Thank you for the suggestion but I'm using a really old computer as a server with limited memory and resources, I prefer not to have a desktop enviroment.

---

### Post by l3ecl on 2012-02-12
> **savanna said:**
> Services are started using init scripts:

% runlevel
N 2

% ls /etc/rc2.d
(it's runlevel 2 so look in the rc2.d directory)

% cat /etc/rc2.d/README --> gives you some doco
The scripts in this directory are executed each time the system enters
this runlevel.
...


To stop services from running at startup, you can rename the S files to K files as per the README, or use update-rc.d. See man update-rc.d:

% man update-rc.d

NAME
       update-rc.d - install and remove System-V style init script links


I tried this approach but sometimes I see the same services in multiple rc.0-rc.6 folders. It's a bit confusing and complex, I prefer the simplicity of "boot up manager' but without the gui interface.

---

### Post by kevdog on 2012-02-14
Your server normally boots to runlevel 2, the 0-6 folders are for other run levels.  You are usually not running within these run levels, so what ever is contained in these folders is ignored.

---

### Post by ruffEdgz on 2012-02-14
> **l3ecl said:**
> I tried this approach but sometimes I see the same services in multiple rc.0-rc.6 folders. It's a bit confusing and complex, I prefer the simplicity of "boot up manager' but without the gui interface.

The command 'update-rc.d' command isn't that complicated. You just need to know your services a bit more before using it.

For example:

I would like to disable my apache2 service so to complete this I would run this command:
```

sudo update-rc.d apache2 disable

```
This will make sure that each runlevel will not start up apache2 as i have requested (the result of disabling apache2 on my system below):
```

Disabling system startup links for /etc/init.d/apache2 ...
 Removing any system startup links for /etc/init.d/apache2 ...
   /etc/rc0.d/K20apache2
   /etc/rc1.d/K20apache2
   /etc/rc2.d/S20apache2
   /etc/rc3.d/S20apache2
   /etc/rc4.d/S20apache2
   /etc/rc5.d/S20apache2
   /etc/rc6.d/K20apache2
 Adding system startup for /etc/init.d/apache2 ...
   /etc/rc0.d/K20apache2 -> ../init.d/apache2
   /etc/rc1.d/K20apache2 -> ../init.d/apache2
   /etc/rc6.d/K20apache2 -> ../init.d/apache2
   /etc/rc2.d/K80apache2 -> ../init.d/apache2
   /etc/rc3.d/K80apache2 -> ../init.d/apache2
   /etc/rc4.d/K80apache2 -> ../init.d/apache2
   /etc/rc5.d/K80apache2 -> ../init.d/apache2

```
I hope you found the way a way that you feel is easy.

Cheers!

---

