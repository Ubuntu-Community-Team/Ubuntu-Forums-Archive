---
title: "installing php5-curl but broken packages"
date: 2008-11-18
forum: Server Platforms
---

### Post by robinc on 2008-11-18
Hello all,

I've just upgraded from 6.06 to 6.10 on a hired dedicated web server so I could get php 5.2.x as 5.1 is the newest package in aptitude for 6.06.

Everything went fine except for the mail server going a bit messed up because of a bug.

I've just tried to install Magnento* which is telling me I need mcrypt and curl for php installed. On trying to install php5-curl, I get this error. Could anyone help me out at all?

Sorry about the screenshot but when ever I paste it seems to delete all of the output that I paste, odd!!

[IMG]http://i35.tinypic.com/34y9qic.png[/IMG]

---

### Post by animaster on 2009-05-13
I also ran into the same problem. I have no idea how to solve it. Maybe I should try to build and install it from source?

---

### Post by wxman on 2009-07-03
I'm using 8.04 and have the same problem. An Internet search did nothing to help either. I got this when I tried:
```
The following packages are BROKEN:
  php5-curl
The following packages have been automatically kept back:
  libcompress-raw-zlib-perl linux-libc-dev
The following packages have been kept back:
  base-files
0 packages upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 25.0kB of archives. After unpacking 123kB will be used.
The following packages have unmet dependencies:
  php5-curl: Depends: php5-common (= 5.2.4-2ubuntu5.6) but 5.2.9-0.dotdeb.2 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libapache2-mod-php5
php5
php5-imagick

Downgrade the following packages:
php-pear [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]
php5-cgi [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]
php5-cli [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]
php5-common [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]
php5-gd [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]
php5-mcrypt [5.2.9-0.dotdeb.2 (now) -> 5.2.3-0ubuntu1 (hardy)]
php5-mysql [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.6 (hardy-updates, hardy-security)]

Score is 467

Accept this solution? [Y/n/q/?]

```

---

### Post by wxman on 2009-07-05
I don't know what's going on, but I'm trying to get a site going using Drupal, and it needs the curl library. It says that curl isn't installed, but I did install it in the beginning. if I do an apt-get install it says I have the latest copy. If I do the aptitude install php5-curl, I get the errors in the post above. I even tried manually adding extension=curl.so to the php.ini, but it just failed to find it when I restarted apache. I really need to have curl working for my sites, but I just can't figure what's gone wrong.

---

