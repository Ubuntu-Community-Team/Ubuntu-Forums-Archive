---
title: "up-to-date PHP 5.2 versions for Hardy needed!"
date: 2010-08-23
forum: Server Platforms
---

### Post by snek on 2010-08-23
I am currently running multiple VPS's of which one is a Hardy based LAMP install with PLESK. I have just one gripe about running Hardy on this VPS: PHP 5.2 is horribly outdated!! It has 5.2.4 in the repos, whilst 5.2.14 was released a while ago.

As an LTS server distro you would expect these kinds of packages to be updated to ensure security?

Please don't tell me I can use Dotdeb, it was never meant for Ubuntu and I have had problems with it in the past.

---

### Post by dgoosens on 2010-08-23
euh...
just update the server and it should be ok...

---

### Post by snek on 2010-08-23
Errr no...
> 
Package: php5
State: not installed
Version: **5.2.4**-2ubuntu5.10
Priority: optional
Section: web
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 20.5k
Depends: libapache2-mod-php5 (>= 5.2.4-2ubuntu5.10) | php5-cgi (>= 5.2.4-2ubuntu5.10), php5-common (>= 5.2.4-2ubuntu5.10)
Description: server-side, HTML-embedded scripting language (meta-package)
 This package is a meta-package that, when installed, guarantees that you have at least one of the four server-side versions of the PHP5 interpreter installed.  Removing this package won't remove PHP5 from your system, however it may
 remove other packages that depend on this one. 
 
 PHP5 is an HTML-embedded scripting language. Much of its syntax is borrowed from C, Java and Perl with a couple of unique PHP-specific features thrown in. The goal of the language is to allow web developers to write dynamically
 generated pages quickly. 
 
 Homepage: [http://www.php.net/](http://www.php.net/)


---

### Post by cdenley on 2010-08-23
5.2.4-2ubuntu5.10 > 5.2.4

Fixes made in more recent releases get backported to the stable version (5.2.4) in the repos.
```

zcat /usr/share/doc/php5-common/changelog.Debian.gz|less

```

What are you concerned about specifically?

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

### Post by craigp84 on 2010-08-24
Hi,

You can trivially build your own php package for any version you choose. Don't feel you're constrained to what's in the repos. It's 100% your choice what you run. This option requires you to take complete responsiblity for future updates though.

However, as cdenley says, the only reason to do this would be feature upgrades as security fixes are backported.

---

### Post by snek on 2010-08-24
> **cdenley said:**
> 5.2.4-2ubuntu5.10 > 5.2.4

Fixes made in more recent releases get backported to the stable version (5.2.4) in the repos.


Ah I was not aware of this. Thank you for the information, that fixes my worries :)
And about building PHP mysql, I just can't be bothered. I am a PHP programmer and I don't have too much time to do system maintenance.

Normally I run Zend Server with PHP 5.3, but it doesn't play nice with Plesk.

---

