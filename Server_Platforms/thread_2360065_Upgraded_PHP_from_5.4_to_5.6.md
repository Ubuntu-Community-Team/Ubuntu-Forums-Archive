---
title: "Upgraded PHP from 5.4 to 5.6"
date: 2017-05-01
forum: Server Platforms
---

### Post by vs-ruthless on 2017-05-01
Hi,

I've got an ubuntu 12.04 lts server running on a hosted VPS, been using it for years without much issues. But I've got this issue at the moment where  I cannot upgrade PHP from 5.4 to 5.6 as it keeps saying 
> 
PHP 5.5+ is required. 
 Currently installed version is: 5.4.45-4+deprecated+dontuse+deb.sury.org~precise+1


The issue I have is the same as this post [URL="https://askubuntu.com/questions/802570/upgraded-php-from-5-4-to-5-6-but-phpinfo-still-shows-5-4"]https://askubuntu.com/questions/802570/upgraded-php-from-5-4-to-5-6-but-phpinfo-still-shows-5-4
[/URL]  
dpkg -l '*php5*' output:
```

||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
un  libapache2-mod-php5             <none>                          (no description available)
un  libapache2-mod-php5.6           <none>                          (no description available)
rc  libapache2-mod-php5filter       5.4.45-4+deprecated+dontuse+deb server-side, HTML-embedded scripting language (apache 2 filter module)
un  libow-php5                      <none>                          (no description available)
un  php5                            <none>                          (no description available)
ii  php5-cgi                        5.4.45-4+deprecated+dontuse+deb server-side, HTML-embedded scripting language (CGI binary)
ii  php5-cli                        5.4.45-4+deprecated+dontuse+deb command-line interpreter for the php5 scripting language
ii  php5-common                     5.4.45-4+deprecated+dontuse+deb Common files for packages built from the php5 source
ii  php5-curl                       5.4.45-4+deprecated+dontuse+deb CURL module for php5
un  php5-fpm                        <none>                          (no description available)
ii  php5-gd                         5.4.45-4+deprecated+dontuse+deb GD module for php5
un  php5-gpib                       <none>                          (no description available)
un  php5-json                       <none>                          (no description available)
ii  php5-mcrypt                     5.4.45-4+deprecated+dontuse+deb MCrypt module for php5
un  php5-mhash                      <none>                          (no description available)
ii  php5-mysql                      5.4.45-4+deprecated+dontuse+deb MySQL module for php5
un  php5-mysqli                     <none>                          (no description available)
rc  php5-mysqlnd                    5.3.10-1ubuntu3.17              MySQL module for php5 (Native Driver)
un  php5-readline                   <none>                          (no description available)
un  php5-suhosin                    <none>                          (no description available)
ii  php5-xcache                     2.0.1-1~precise+1               Fast, stable PHP opcode cacher
un  php5.5-amqp                     <none>                          (no description available)
un  php5.5-geoip                    <none>                          (no description available)
un  php5.5-gmagick                  <none>                          (no description available)
un  php5.5-libsodium                <none>                          (no description available)
un  php5.5-memcache                 <none>                          (no description available)
un  php5.5-mongo                    <none>                          (no description available)
un  php5.5-oauth                    <none>                          (no description available)
un  php5.5-propro                   <none>                          (no description available)
un  php5.5-radius                   <none>                          (no description available)
un  php5.5-raphf                    <none>                          (no description available)
un  php5.5-rrd                      <none>                          (no description available)
un  php5.5-tideways                 <none>                          (no description available)
un  php5.5-uuid                     <none>                          (no description available)
un  php5.5-xhprof                   <none>                          (no description available)
un  php5.5-yac                      <none>                          (no description available)
un  php5.5-yaml                     <none>                          (no description available)
un  php5.5-zmq                      <none>                          (no description available)
ii  php5.6                          5.6.30-10+deb.sury.org~precise+ server-side, HTML-embedded scripting language (metapackage)
un  php5.6-amqp                     <none>                          (no description available)
un  php5.6-calendar                 <none>                          (no description available)
un  php5.6-cgi                      <none>                          (no description available)
ii  php5.6-cli                      5.6.30-10+deb.sury.org~precise+ command-line interpreter for the PHP scripting language
ii  php5.6-common                   5.6.30-10+deb.sury.org~precise+ documentation, examples and common module for PHP
un  php5.6-ctype                    <none>                          (no description available)
un  php5.6-exif                     <none>                          (no description available)
un  php5.6-fileinfo                 <none>                          (no description available)
ii  php5.6-fpm                      5.6.30-10+deb.sury.org~precise+ server-side, HTML-embedded scripting language (FPM-CGI binary)
un  php5.6-ftp                      <none>                          (no description available)
un  php5.6-geoip                    <none>                          (no description available)
un  php5.6-gettext                  <none>                          (no description available)
un  php5.6-gmagick                  <none>                          (no description available)
un  php5.6-iconv                    <none>                          (no description available)
ii  php5.6-json                     5.6.30-10+deb.sury.org~precise+ JSON module for PHP
un  php5.6-libsodium                <none>                          (no description available)
un  php5.6-memcache                 <none>                          (no description available)
un  php5.6-mongo                    <none>                          (no description available)
un  php5.6-oauth                    <none>                          (no description available)
ii  php5.6-opcache                  5.6.30-10+deb.sury.org~precise+ Zend OpCache module for PHP
un  php5.6-pdo                      <none>                          (no description available)
un  php5.6-phar                     <none>                          (no description available)
un  php5.6-posix                    <none>                          (no description available)
un  php5.6-propro                   <none>                          (no description available)
un  php5.6-radius                   <none>                          (no description available)
un  php5.6-raphf                    <none>                          (no description available)
ii  php5.6-readline                 5.6.30-10+deb.sury.org~precise+ readline module for PHP
un  php5.6-rrd                      <none>                          (no description available)
un  php5.6-shmop                    <none>                          (no description available)
un  php5.6-sockets                  <none>                          (no description available)
un  php5.6-sysvmsg                  <none>                          (no description available)
un  php5.6-sysvsem                  <none>                          (no description available)
un  php5.6-sysvshm                  <none>                          (no description available)
un  php5.6-tideways                 <none>                          (no description available)
un  php5.6-tokenizer                <none>                          (no description available)
un  php5.6-uuid                     <none>                          (no description available)
un  php5.6-xhprof                   <none>                          (no description available)
un  php5.6-yac                      <none>                          (no description available)
un  php5.6-yaml                     <none>                          (no description available)
un  php5.6-zmq                      <none>                          (no description available)

```


**my php -v info**
> 
PHP 5.6.30-10+deb.sury.org~precise+2 (cli) 
Copyright (c) 1997-2016 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2016 Zend Technologies
    with Zend OPcache v7.0.6-dev, Copyright (c) 1999-2016, by Zend Technologies


Please can someone point me in the right direction, I don't want to break my site it's been running for years.

Please note I'm an intermediate on linux.

Kind regards

Ruthless-K

---

### Post by darkod on 2017-05-01
Have you tried installing that libapache2-mod-php5.6 as suggested in that post? But I noticed the person that asked the original question never replied back whether he installed it too and whether it helped or not.

I'm no expert on apache or php, so I can't promise you 100% this is what you need to do. But according to your dpkg output it's clear the php5.6 module for apache is not installed. You might wanna focus on that and investigate if that is the necessary step.

---

### Post by vs-ruthless on 2017-05-05
Hi Darkod,

Thank you for replying, I tried to install libapache2-mod-php5.6 but it still said I had 5.4 installed.

I ended up formating and starting again, not bad I suppose been running my 12.04 server for 5 years with no issues.

Once again thanks for taking the time to reply.

---

