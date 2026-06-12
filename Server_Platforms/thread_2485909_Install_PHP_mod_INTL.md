---
title: "Install PHP mod INTL"
date: 2023-04-13
forum: Server Platforms
---

### Post by khryshchuk on 2023-04-13
Hi. How to Install PHP mod php-intl for PHP7.3 on Ubuntu 16?

When, I try to install module
```
#apt-get install php-intl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php-intl is already the newest version (1:7.0+35ubuntu6.1).
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

But, in php -m - I don't see this mod. And php -v - has a Warning library 'intl'
```
# php -v
PHP Warning:  PHP Startup: Unable to load dynamic library 'intl' (tried: /usr/lib/php/20180731/intl (/usr/lib/php/20180731/intl: cannot open shared object file: No such file or directory), /usr/lib/php/20180731/intl.so (/usr/lib/php/20180731/intl.so: cannot open shared object file: No such file or directory)) in Unknown on line 0
PHP 7.3.27-9+ubuntu16.04.1+deb.sury.org+1 (cli) (built: Feb 23 2021 15:09:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.3.27, Copyright (c) 1998-2018 Zend Technologies
    with Zend OPcache v7.3.27-9+ubuntu16.04.1+deb.sury.org+1, Copyright (c) 1999-2018, by Zend Technologies
```

How to install php-intl for PHP 7.3?

---

### Post by deadflowr on 2023-04-13
My guess is is that the sury ppa is no longer supported for 16.04.
So you have  php from the sury ppa and the php-intl from the normal repos.
Which causes a mismatch

You probably need to downgrade the php version to the version provided by the repos.

Or find an archived version of the package somewhere that matches the php version you have.

---

### Post by khryshchuk on 2023-04-13
Ok. What I need to do for fix it?
Where I can find the archived version of the packag?

---

### Post by SeijiSensei on 2023-04-13
Ubuntu 16 has long reached its end of life and is no longer supported. Upgrade to 22.04. php-intl doesn't come with the shipped version of PHP, but it's installable with apt. You'll just have a lifetime of woe trying to maintain a six-year-old version of Ubuntu.

---

### Post by khryshchuk on 2023-04-13
The webserver is live, and multiple sites are configured on the server. For one of them - I need php7.3-intl module. 
Can this module be installed without upgrade Ubuntu to 22.04?

---

### Post by SeijiSensei on 2023-04-13
You can probably compile it from source code. Again you will have mountains of trouble in the long run trying to maintain that server.

I have all my websites running on a 22.04 [Linode]("https://www.linode.com/products/shared/") for $5/month. You might consider migrating yours to a cloud server while you rebuild your existing box. 

Is this a physical machine colocated at a provider's site? I gave up on that long ago. I brought my server home for a while, but eventually I moved everything to Linode. For cheap money I get backup power and airconditioning and a big pipe to the Internet. It's pretty easy to move a website since everything that matters likely resides in a single directory. For WordPress sites, I use the "Duplicator" add-on to migrate sites.

Trying to stay on Ubuntu 16 is recipe for heartbreak.

---

### Post by mIk3_08 on 2023-04-13
> **khryshchuk said:**
> Hi. How to Install PHP mod php-intl for PHP7.3 on Ubuntu 16?

If you have a plan to upgrade, This will be a long jump 16  to 22.04. Be sure to back up all necessary data. If there is an app  running live on this server, be sure that this will also going to run  when it will be migrated to the new upgraded system. This will be a huge  work, so be careful. Good luck! Regards and cheers.

---

