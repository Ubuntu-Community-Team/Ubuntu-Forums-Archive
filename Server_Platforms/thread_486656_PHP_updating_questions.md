---
title: "PHP updating questions"
date: 2007-06-28
forum: Server Platforms
---

### Post by Steve3 on 2007-06-28
Hi all,

I've been experimenting with Ubuntu 6.06TLS for an internal development webserver for my company.  My php programmers are insisting that PHP be up to date, and the latest release is 5.2.3

I've updated php via apt-get, but it's only 5.1.2.  I'm fine with compiling it manually, but I'm accustomed to having phpinfo list the "configure command", so I could compile with the same options.

phpinfo on Ubuntu doesn't list the configure command.  Is there a way to either

1) Use apt-get (or an alternate package manager) to be more current than php 5.1.2

or

2) Determine the configure options used on the existing php, as it's working just fine.

Thanks,

Steve.

---

### Post by kidders on 2007-06-29
Hi there,

It seems that Debian-like builds of PHP tend to be patched to explicitly disable the inclusion of the ./configure command in phpinfo(). From the changelogs...

> * Add 052-phpinfo_no_configure.patch, which disables the display of our
    "Configure Command" in phpinfo(), which was the source of many bogus
    bug reports over the years, due to people misinterpreting its meaning.I can only presume that a PHP source build you'd perform yourself on Ubuntu (ie with apt/etc.) would have the same configuration options (at least by default) as the pre-built binaries ... so I suppose you could find out what they are by examining the source. In principle though, you should avoid using applications from outside Ubuntu's "main" repository on servers that need to be reliable & bug-free, so your programmers would want to have a very good reason for wanting an unsupported PHP build. At the very least, you should check there is no reason for the absence of a particular build from the repos.

---

### Post by az on 2007-06-29
> **Steve3 said:**
> Hi all,

I've been experimenting with Ubuntu 6.06TLS for an internal development webserver for my company.  My php programmers are insisting that PHP be up to date, and the latest release is 5.2.3.


Gutsy will be released with at least version5.2.3
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=php5&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=php5&searchon=names&subword=1&version=all&release=all)


> **Steve3 said:**
> 
I've updated php via apt-get, but it's only 5.1.2.  I'm fine with compiling it manually, but I'm accustomed to having phpinfo list the "configure command", so I could compile with the same options.

phpinfo on Ubuntu doesn't list the configure command.  Is there a way to either

1) Use apt-get (or an alternate package manager) to be more current than php 5.1.2


Dist-upgrade to feisty.  You would need to dist-upgrade to Edgy first since the bug-free path is to not skip releases.  This will not be an issue with LTS releases, but neither edgy nor feisty are LTS.


> **Steve3 said:**
> 

or

2) Determine the configure options used on the existing php, as it's working just fine.

Thanks,

Steve.

Enable the deb-src entries for main in your /etc/apt/sources.list and 
sudo apt-get source php5

---

