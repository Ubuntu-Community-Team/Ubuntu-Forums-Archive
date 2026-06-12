---
title: "php5-gd outdated"
date: 2010-05-22
forum: Server Platforms
---

### Post by mjhasbach on 2010-05-22
I've managed to get my server up and running nicely after quite a bit of a learning curve.

I have decided to use Joomla for my website. There is an extension for Joomla called Photoslide GK3 that I want to use; however, it informs me that my php5-gd library is outdated (2.0).

As far as I know, none of the Ubuntu repositories nor the packages.dotdeb.org repository has a current version of php5-gd. If someone can link me to a precompiled version of php5-gd higher than 2.0.30 I would greatly appreciate it.

This has had me stumped for hours. I can't seem to find a precompiled version anywhere...

The latest version of GD can be found at [http://www.libgd.org](http://www.libgd.org) , but it would require compiling the source (a lot of dependencies) and recompiling php if I'm not mistaken. I'm afraid that's a bit beyond my experience. I don't want to mess my server up.

---

### Post by crazyone on 2010-05-22
here you go. not sure if you need 32bit or the 64bit so here is both
32bit
 [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.10.dfsg.1-2ubuntu6.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.10.dfsg.1-2ubuntu6.4_i386.deb)

64bit
[http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.10.dfsg.1-2ubuntu6.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.10.dfsg.1-2ubuntu6.4_amd64.deb)

they should be the right version. havent used ubuntu for myserver in a while so i cant rember the version numbering on it. to install it jsut run

wget "version needed" 
and then run
sudo dpkg -i "version needed"

replace the "version needed" with the copy you downlaoded without quotes. hope that helps you out

---

### Post by mjhasbach on 2010-05-22
> **crazyone said:**
> here you go. not sure if you need 32bit or the 64bit so here is both
32bit
 [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.10.dfsg.1-2ubuntu6.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.10.dfsg.1-2ubuntu6.4_i386.deb)

64bit
[http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.10.dfsg.1-2ubuntu6.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.10.dfsg.1-2ubuntu6.4_amd64.deb)

they should be the right version. havent used ubuntu for myserver in a while so i cant rember the version numbering on it. to install it jsut run

wget "version needed" 
and then run
sudo dpkg -i "version needed"

replace the "version needed" with the copy you downlaoded without quotes. hope that helps you out

I followed your steps and received an error on the last step:

```
dpkg: [COLOR="Red"]warning: downgrading php5-gd from 5.3.2-1ubuntu4.2 to 5.2.10.dfsg.1-2ubuntu6.4.[/COLOR]
(Reading database ... 57744 files and directories currently installed.)
Preparing to replace php5-gd 5.3.2-1ubuntu4.2 (using php5-gd_5.2.10.dfsg.1-2ubuntu6.4_amd64.deb) ...
Unpacking replacement php5-gd ...
dpkg: dependency problems prevent configuration of php5-gd:
 [COLOR="blue"]php5-gd depends on php5-common (= 5.2.10.dfsg.1-2ubuntu6.4); however:
  Version of php5-common on system is 5.3.2-1ubuntu4.2.[/COLOR]
dpkg: error processing php5-gd (--install):
 dependency problems - leaving unconfigured
Processing triggers for libapache2-mod-php5 ...
 * Reloading web server config apache2                                   [ OK ]
Errors were encountered while processing:
 php5-gd
```

I'm guessing the part I highlighted in red means that the php5-gd link you provided is older than what I already have installed? And the part in blue means that one of the required dependencies is older than what I have installed?

I'm pretty sure there isn't a newer php5-gd on Ubuntu repositories than what I already have. I read somewhere that Ubuntu refused to compile a newer version in PHP because of security issues or something. If there's a newer compiled version out there it's more than likely going to be from a third-party.

---

### Post by crazyone on 2010-05-22
the problem is it is a downgrade form what you have. you are on php 5.3.2. 


edit
ok foudn the problem(hopefully). it is the libgd2-xpm that is the problem. try running this to update the gd libary and than try the extenstion again. do the same thing as i said above but with the right version of this package.

32bit
[http://mirrors.kernel.org/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.36~rc1~dfsg-3.1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.36~rc1~dfsg-3.1ubuntu1_i386.deb)

64bit
[http://mirrors.kernel.org/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.36~rc1~dfsg-3.1ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.36~rc1~dfsg-3.1ubuntu1_amd64.deb)

it may or may not let u install them. if it complains about dependances than youll have to recompile the gd libary by hand and not use a package becuase it will then become a major dependance problem. have done something like it before and cuase myself a major headack by trying to get all the dependancies fixed

---

