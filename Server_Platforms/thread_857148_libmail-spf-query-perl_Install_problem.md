---
title: "libmail-spf-query-perl Install problem"
date: 2008-07-12
forum: Server Platforms
---

### Post by thiswaynow on 2008-07-12
Hi,

I am trying to set Spamassassin up on my Dapper box. 

This produces the following error:

spamassassin: Depends: libmail-spf-query-perl but it is not going to be installed

I then try:

apt-get install -f libmail-spf-query-perl

and get:


Unpacking libmail-spf-query-perl (from .../libmail-spf-query-perl_1.997-3_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libmail-spf-query-perl_1.997-3_all.deb (--unpack):
 trying to overwrite `/usr/sbin/spfd', which is also in package cpan-libmail-spf-perl
Errors were encountered while processing:
 /var/cache/apt/archives/libmail-spf-query-perl_1.997-3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have tried 'apt-get install -f' and 'apt-get upgrade -f ', etc

Any ideas?

PS: I'm new to Ubuntu, please don't shout if I'm missing something obvious

---

### Post by thiswaynow on 2008-07-14
Can anyone help on this?

---

