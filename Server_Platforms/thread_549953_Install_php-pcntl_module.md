---
title: "Install php-pcntl module"
date: 2007-09-13
forum: Server Platforms
---

### Post by mantomin on 2007-09-13
Hello!
I need to install pcntl libraries [http://php.net/manual/en/ref.pcntl.php](http://php.net/manual/en/ref.pcntl.php).

First I have searched the module in apt-get but I haven't found it. Then I use Google and I found php-pcntl (4.3.8-2) and php-gtk-pcntl(1.0.0-2).

I've installed both with our dependencies but I haven't seen any change. I suppose it's necessary recompile PHP and that's my problem. I installed PHP by apt-get, and now I don't know how to recompile PHP. 

I read some documentation and I made the follow actions:

1.	Download the source code php 5.2.1 -> apt-get source php5
2.	Change to /php5-5.2.1 directory and execute: configure --enable-pcntl --enable-shmop --enable-cli --without-apache --disable-cgi --enable-posix --enable-pcre
3.	and now.. ?¿?¿


I'm a new user of Ubuntu and is the first time that I recompile something :) ?

Thanks a lot!

P.S: Sorry for my English...

---

### Post by skout23 on 2008-07-11
I know this is way after the fact, but since I was searching for this too... thought I would post what I found out.

This [bug item]("https://bugs.launchpad.net/ubuntu/+source/php5/+bug/93603") had a good start.

```
mkdir php
cd php
apt-get source php5
cd php5-(WHATEVER_RELEASE)
$EDITOR debian/rules -> find "--with-curl" line and add configure option
$EDITOR debian/modulelist -> add module
dpkg-buildpackage -rfakeroot
cd ..
```

I ended up adding a line to the debian/rules file

```
--enable-pcntl \
```

However adding the pcntl to the list of modules caused it to fail.  So removed the modules, and just kept the line to the debian/rules file which built the new php5 binary.  

However after testing the new and old binaries, I found that I did not need to recompile the php5 itself, just to access the pcntl funtions.  

Was a good lesson though.  All I needed to do was compile the pcntl module and install it.

compiling and installing the module:

```

mkdir php
cd php
apt-get source php5
cd php5-(WHATEVER_RELEASE)/ext/pcntl
phpize
./configure
make
```

** I believe you could do a "make install" here, however I was not certain it would place the modules in the correct spot.  So I just manually moved and created the init file.

```
cp modules/pcntl.so /usr/lib/php5/WHEVER_YOUR_SO_FILES_ARE/
echo "extension=pcntl.so" > /etc/php5/conf.d/pcntl.ini
```

Hope that helps the next person save some time, it took me about 3 hours of compiling before I found out I did not need to recompile php5 itself to access the pcntl module.

Cheers

---

