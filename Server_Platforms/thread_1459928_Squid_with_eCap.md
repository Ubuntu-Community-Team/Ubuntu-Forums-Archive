---
title: "Squid with eCap"
date: 2010-04-22
forum: Server Platforms
---

### Post by SauRoN ZA on 2010-04-22
Good morning.

I have already installed Squid on Ubuntu 10.04, including accessing/configuring it via Webmin.

Problem is that now I've been asked to add eCap to it if possible, for hopefully rendering a toolbar of sorts for all pages being served by the proxy.

Problem is I have no idea how to go about implementing eCap, and can't really find any definitive documentation on installation/configuration.

Can anyone point me in the right direction?

---

### Post by jameztcc on 2010-05-19
Hi,

check this page out "http://code.google.com/p/squid-ecap-gzip/wiki/Installation"

thanks,
James Tan

---

### Post by Chris Alfred on 2012-07-19
I found it easier to install libecap using the first step in [http://code.google.com/p/squid-ecap-gzip/wiki/Installation](http://code.google.com/p/squid-ecap-gzip/wiki/Installation).

Then create an empty directory, and in there do: sudo apt-get source squid3

The Ubuntu squid sources already have the right configuration defaults. So you just configure with: ./configure --enable-ecap
Then make as usual:
   make all
   sudo make install

At the time of writing, Ubuntu squid sources were for Squid 3.1.19 and it requires libecap 0.0.3.

---

