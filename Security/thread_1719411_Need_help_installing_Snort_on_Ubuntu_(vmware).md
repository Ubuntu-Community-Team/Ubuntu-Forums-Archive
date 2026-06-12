---
title: "Need help installing Snort on Ubuntu (vmware)"
date: 2011-04-01
forum: Security
---

### Post by honkanen on 2011-04-01
Hey Guys,

I spent quite a while trying to do something I thought would be simple...install Snort on Ubuntu 10.04. Here's what I did so far:
1. "cd /usr/src"
2. sudo wget [http://www.snort.org/dl/snort-current/snort-2.9.0.4.tar.gz](http://www.snort.org/dl/snort-current/snort-2.9.0.4.tar.gz) -O snort-2.9.0.4.tar.gz  
3. tar xzvf snort-2.9.0.4.tar.gz (this uncompressed and created a snort-2.9.0.4 folder.
4. installed libpcap0.8-dev & libpcre3-dev
5. cd snort-2.9.0.4
6. sudo ./configure
    - this came back with: 
   ERROR!  Libpcap library/headers (libpcap.a (or .so)/pcap.h)
   not found, go get it from [http://www.tcpdump.org](http://www.tcpdump.org)
   or use the --with-libpcap-* options, if you have it installed
   in unusual place.  Also check if your libpcap depends on another
   shared library that may be installed in an unusual place

I thought I already have libpcap installed though?  When I do a "apt-cache policy libpcap0.8-dev" it comes back with:
libpcap0.8-dev:
  Installed: 1.0.0-6
  Candidate: 1.0.0-6

I see that I can't move onto the "make" or "make install" until I get this sorted out.  When I try to type "make" or "make install" it comes back with:
No targets specified and no makefile found.  Stop.

Any ideas?  
Thanks!

---

### Post by howefield on 2011-04-02
Thread moved to "*Security Discussions*"

---

