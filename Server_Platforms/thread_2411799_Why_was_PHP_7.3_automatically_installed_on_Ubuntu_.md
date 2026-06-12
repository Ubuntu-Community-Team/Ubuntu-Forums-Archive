---
title: "Why was PHP 7.3 automatically installed on Ubuntu 16.04?"
date: 2019-02-04
forum: Server Platforms
---

### Post by ericjoh on 2019-02-04
Hi,

I have been trying to figure out a problem with a Ubuntu 16.04 server for a while and recently found that the problem is that php 7.3 seems to have been automatically installed during a "apt-get update ; apt-get -y dist-upgrade" on October 15, 2018 so that the system started to use php 7.3 instead of php 7.1 that was already installed.

On August 2, 2018, I had these php related packages installed according to "dpkg -l|grep php|grep -v ^rc" (I have a saved output of "dpkg -l" from that date):

libapache2-mod-php7.1
php-apcu
php-common
php7.1
php7.1-cli
php7.1-common
php7.1-curl
php7.1-gd
php7.1-intl
php7.1-json
php7.1-mbstring
php7.1-mysql
php7.1-opcache
php7.1-readline
php7.1-soap
php7.1-xml
php7.1-xmlrpc
php7.1-zip

If I compare with a saved output of "dpkg -l" from August 2, 2018, and  today February 4, 2019, I see that I now have these additionally php  packages installed:

libphp7.3-embed
php7.3-cli
php7.3-common
php7.3-json
php7.3-opcache
php7.3-readline

The log from "apt-get update ; apt-get -y dist-upgrade" on October 15, 2018, looks like this:

[...]
The following NEW packages will be installed:
  libargon2-0 libpcre2-8-0 libphp7.3-embed libsodium23 php7.3-cli
  php7.3-common php7.3-json php7.3-opcache php7.3-readline
The following packages will be upgraded:
  libapache2-mod-php7.1 php-apcu php7.1 php7.1-cli php7.1-common php7.1-curl
  php7.1-gd php7.1-intl php7.1-json php7.1-mbstring php7.1-mysql
  php7.1-opcache php7.1-readline php7.1-soap php7.1-xml php7.1-xmlrpc
  php7.1-zip python-requests python3-requests
19 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
[...]

I would like to figure out why those php 7.3 related packages where  automatically installed on October 15, 2018. Any idea?

---

### Post by coffeecat on 2019-02-04
The version of php available in the Ubuntu repositories for Ubuntu 16.04 is php7.0. Do you have a 3rd-party / PPA repository enabled?

---

### Post by ericjoh on 2019-02-04
> **coffeecat said:**
> The version of php available in the Ubuntu repositories for Ubuntu 16.04 is php7.0. Do you have a 3rd-party / PPA repository enabled?

Thanks, yes, I'm using ppa:ondrej/php (deb [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) xenial main). I still wonder how php7.3 was able to be automatically install. What dependency did cause that?

---

### Post by howefield on 2019-02-04
Moved to the "*Server Platforms*" forum.

---

