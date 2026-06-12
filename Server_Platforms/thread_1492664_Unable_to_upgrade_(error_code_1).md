---
title: "Unable to upgrade (error code 1)"
date: 2010-05-25
forum: Server Platforms
---

### Post by donovanh on 2010-05-25
I recently upgraded my dist to 10.04 (server) and most things seem fine. However, I'm getting a warning from PHP to do with a missing library:

> PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613/mhash.so' - /usr/lib/php5/20060613/mhash.so: cannot open shared object file: No such file or directory in Unknown on line 0

I'm not sure how to handle this, so I tried to update and upgrade to see if it could be fixed. However when I run apt-get upgrade it keeps giving errors. I tried to install php5 in the hopes that it would resolve the missing library, and got these errors:

> Errors were encoun              tered while processing:
 /var/cache/apt/archives/libxml2_2.7.6.dfsg-1ubuntu1_amd64.deb
 /var/cache/apt/archives/php5-cli_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/php5-xsl_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/php5-mcrypt_5.3.2-0ubuntu1_amd64.deb
 /var/cache/apt/archives/php5-xcache_1.3.0-5ubuntu1_amd64.deb
 /var/cache/apt/archives/php5-pspell_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/php5-memcache_3.0.4-2build1_amd64.deb
 /var/cache/apt/archives/php5-snmp_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/php5-curl_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/php5-xmlrpc_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/php5-sqlite_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/libgd2-xpm_2.0.36~rc1~dfsg-3.1ubuntu1_amd64.deb
 /var/cache/apt/archives/php5-gd_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/libgomp1_4.4.3-4ubuntu5_amd64.deb
 /var/cache/apt/archives/libltdl7_2.2.6b-2ubuntu1_amd64.deb
 /var/cache/apt/archives/libmagickcore2_7%3a6.5.7.8-1ubuntu1_amd64.deb
 /var/cache/apt/archives/libmagickwand2_7%3a6.5.7.8-1ubuntu1_amd64.deb
 /var/cache/apt/archives/php5-imagick_2.1.1RC1-1build3_amd64.deb
 /var/cache/apt/archives/php5-cgi_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/php5-mysql_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/libapache2-mod-php5_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/php5-common_5.3.2-1ubuntu4.2_amd64.deb
 /var/cache/apt/archives/php5_5.3.2-1ubuntu4.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have tried using apt-get -f install to fix the issues but it reports 0 packages installed. Any idea what I could try next?

---

### Post by donovanh on 2010-05-25
This seems relevant, but it's two complex for me to understand:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=563726](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=563726)

There's talk of a patch here, but I don't know what I'm looking at. Can someone translate?

---

### Post by donovanh on 2010-05-25
Think I need to update Tar

[http://packages.debian.org/unstable/tar](http://packages.debian.org/unstable/tar)

No idea how to though. Argh!

---

