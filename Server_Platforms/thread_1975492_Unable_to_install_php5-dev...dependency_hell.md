---
title: "Unable to install php5-dev...dependency hell?"
date: 2012-05-07
forum: Server Platforms
---

### Post by s0c0 on 2012-05-07
I need to install php5-dev so I can install the xhprof PECL extension, but I am running into some problems. Was able to do this on my home system which is also running Ubuntu 11.10. I've probably done some funked up stuff to the ol' workstation... I am running PHP 5.3.6-13ubuntu3.7, but at one point I had installed a newer version of PHP (5.3.10 I think) from Debian sources. I think that had something to do with this whole mess. I have removed the dotdeb repo from my sources list and done apt-get update etc...

```

sudo pecl install channel://pecl.php.net/xhprof-0.9.2
11 source files, building
running: phpize
sh: phpize: not found
If the command failed with 'phpize: not found' then you need to install php5-dev packageYou can do it by running 'apt-get install php5-dev' as a root userERROR: `phpize' failed

```

Okay...

```

sudo apt-get install php5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 php5-dev : Depends: libssl-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

No problem, I'll just...

```

sudo apt-get install libssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.0e-2ubuntu4.5) but 1.0.0e-2.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

Anyone have some ideas short of compiling from source?

---

### Post by vVvSHADOWvVv on 2012-05-07
Just a note to everyone. The easy way to install PHP and such is via tasksel

sudo apt-get install tasksel

sudo tasksel install lamp-server

;-)

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

---

### Post by s0c0 on 2012-05-07
^ Not helpful.

---

### Post by s0c0 on 2012-05-07
...

---

### Post by s0c0 on 2012-05-08
I was finally able to resolve this. I downloaded the .deb version of openssl I needed directly from [https://launchpad.net/ubuntu/oneiric/+source/openssl/1.0.0e-2ubuntu4.5](https://launchpad.net/ubuntu/oneiric/+source/openssl/1.0.0e-2ubuntu4.5).

I installed that using dpkg -i.

Then I had to follow the instructions in this bug report to finally compile xhprof. [https://bugs.php.net/bug.php?id=58650](https://bugs.php.net/bug.php?id=58650)

Sheesh.

---

