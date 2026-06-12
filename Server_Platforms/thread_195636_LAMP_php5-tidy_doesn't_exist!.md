---
title: "LAMP: php5-tidy doesn't exist!"
date: 2006-06-13
forum: Server Platforms
---

### Post by paul.maddox on 2006-06-13
Hi guys,

I'm setting up a development server for our company using ubuntu.

We run php5 / Apache2 and require a number of different php modules for our application to work properly. I've had good success except with Tidy which we use for cleaning HTML/XML that is entered by a user.

It seems that there is no php5-tidy module in the repositories :(
I have tried the following command:
```
pecl install tidy
```
but that just installs the old php4 version (v1.2)

The new Tidy2.0 which we require is bundled with PHP5 by default, but does not seem to have been included in the ubuntu build of PHP5 :(

Also I can't seem to find a download source for Tidy2.0 anywhere on the net, every site I go to just says 'It's bundled with php5'


Any ideas how I can get this module installed?

---

### Post by dlane on 2006-07-16
I'm also very interested in enabling tidy 2.0 support in PHP5 on Dapper - a number of our web applications depend on it (tidy support was enabled in the Mandriva PHP5 install that we used to use).  I'm currently trying to build Debs from the PHP5 source package with Tidy support - I can't see any reason why the Ubuntu/Debian package managers didn't include it by default...  If I can build a modified set of Deb binaries (I *would* pick PHP5 as my first build-deb-from-source project... *slaps forehead*).  If you have any joy finding a solution in the meantime, don't hesitate to let me know! :) 

Dave

---

### Post by paul.maddox on 2006-07-16
You're in luck, I managed to work out how to compile and install it successfully!

```

# Install libtidy (needed for tidy2.0 compile)
apt-get -y install libtidy-0.99-0

# Install GNU tools for compiling
apt-get -y install build-essential

# Download tidy2.0 source (this can also be found in the PHP5 sourcecode, I just tarred it up to make this easier)
wget -c http://support.office-shadow.com/installer/tidy2.0.tar.gz

# Unpack the source
tar xvzf tidy2.0.tar.gz

# Configure tidy for installed php5 API
cd tidy
phpize 

# Configure & Compile the source
./configure
make clean    <-- Without this the compile builds a bad module for some reason
make 
make install

# Install module into php.ini 
echo "extension=tidy.so" >> /etc/php5/apache2/php.ini;


```


This will install tidy2.0 and configure it with your installation of PHP.
All that is needed is to restart apache afterwards.

If you receive an error when trying to run 'phpize' then you will need to install the php5-cli package from the repositories

---

### Post by dlane on 2006-07-16
You beauty!  Thanks very much - managed to get that working.  Thanks also for putting together the tidy archive. The only issue I found was that I had to manually (via an editor rather than the echo) add the "extension=tidy.so" to the php.ini file (and one would normally have to add it to /etc/php5/cli/php.ini as well, if you want to use it in php shell scripts) and then restarted Apache2: /etc/init.d/apache2 restart

Brilliant!  (PHP5 debs aren't easy to rebuild from source - while changing the configure options at least - based on my experience)

Dave

---

### Post by Randomskk on 2006-07-16
A quick aside, but this is a nicer way to restart Apache:
apache2ctl restart

---

### Post by paul.maddox on 2006-07-16
No problem, glad I could help. Was a pig to work out how to install it at the time to be honest because of that 'make clean', without it Apache would throw an error when started and wouldn't include the tidy module. If anyone could explain why that is needed I'd be very interested to hear!

Just in case anyone anyone ever reads this in the future wanting to add tidy to their php installation and the tidy2.0.tar.gz isn't available anymore, you can find this inside the php5 source code from [www.php.net](www.php.net) in the folder ext/tidy/*

:)

---

### Post by chrilleh on 2006-07-18
For the phpize to work you also need php5-dev.
And if you get the following error message when trying to configure tidy:
configure: error: Cannot find libtidy

Then you need libtidy-dev.

Hope it can help someone...

---

### Post by library.ninja on 2006-07-20
Thanks!  I had started on a project that needed tidy a month ago. ](*,)  I gave up for awhile and started back on it today.  This was the missing piece to get it up and running!  :D

---

### Post by Dianoga on 2006-08-11
Thanks much...I've been trying to figure this out for a couple of hours.

---

### Post by simidau on 2006-12-04
> **chrilleh said:**
> For the phpize to work you also need php5-dev.
And if you get the following error message when trying to configure tidy:
configure: error: Cannot find libtidy

Then you need libtidy-dev.

Hope it can help someone...

Help me it did.

Ta.

---

### Post by motin on 2007-07-18
Me too, even though I didn't find the -dev package tip here in the first place :)

Thanks for the guide! I first installed 1.2 as it was the latest version available on [http://pecl.php.net/package/tidy](http://pecl.php.net/package/tidy)

Strange that they do not make 2.0 available there...

---

### Post by conjur3r on 2007-07-19
Looks like there is a package available for fesity: [http://packages.ubuntu.com/feisty/web/php5-tidy](http://packages.ubuntu.com/feisty/web/php5-tidy)  But not sure which version of tidy it is using.

---

### Post by paul.maddox on 2007-07-19
Seems to be the right version and works great with apache once installed...



```
paul.maddox@paul-laptop:~$ apt-cache show php5-tidy
Package: php5-tidy
Priority: optional
Section: web
Installed-Size: 96
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian PHP Maintainers <pkg-php-maint@lists.alioth.debian.org>
Architecture: i386
Source: php5
Version: 5.2.3-1ubuntu2
Depends: libc6 (>= 2.6), libtidy-0.99-0, phpapi-20060613+lfs, php5-common (= 5.2.3-1ubuntu2)
Filename: pool/main/p/php5/php5-tidy_5.2.3-1ubuntu2_i386.deb
Size: 16378
MD5sum: a384a5428227b67ebc5baadc9ac1867a
SHA1: 8ab46a0a0b9e676a2b0129b829c4302d2725fc16
SHA256: 7088c3bf7616b26d007ca5e45ec3f1dcc730f28808c18582c025987cf3515ce8
Description: tidy module for php5
 This package provides a module for tidy functions in PHP scripts.
 .
 Tidy is an extension based on Libtidy (http://tidy.sf.net/) and allows
 a PHP developer to clean, repair, and traverse HTML, XHTML, and XML
 documents -- including ones with embedded scripting languages such as PHP
 or ASP within them using OO constructs.
 .
 PHP5 is an HTML-embedded scripting language. Much of its syntax is borrowed
 from C, Java and Perl with a couple of unique PHP-specific features thrown
 in. The goal of the language is to allow web developers to write
 dynamically generated pages quickly.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

### Post by MxGB on 2007-09-09
Thanks, compiled it successfully on Dapper.

---

### Post by melonman on 2007-10-20
> **paul.maddox said:**
> 
```

# Configure & Compile the source
./configure

```


I inspected the configure file and found I needed to give it 
```

 ./configure --with-tidy=tidy-20051018/

```
in order to locate the required tidy source files (which were helpfully included in that bundle!)
=D>
I'd already installed tidy & libtidy from deb packages

Thanks heaps for this very non-dangerous howto! I was really not wanting to rebuild PHP on my nice clean system.
I use php-tidy as part of an [import-html]("http://drupal.org/project/import_html") process to Drupal CMS and I'll be linking my own documentation back to here.

---

### Post by khughitt on 2008-05-27
Off-topic but would anyone happen to know where the default configuration file for php5-tidy is stored? Or do I need to create my own?

Thanks!

---

