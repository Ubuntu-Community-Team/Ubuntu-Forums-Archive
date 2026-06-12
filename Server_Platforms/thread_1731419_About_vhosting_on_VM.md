---
title: "About vhosting on VM"
date: 2011-04-17
forum: Server Platforms
---

### Post by satimis on 2011-04-17
Hi folks

Can virtual hosting work on VM?

host - ubunut 1010 desktop 64bit
virtualizer - VirtualBox ver 3.2.10 r66523
guest (VM) - ubuntu 1010 server 64bit

I followed;
Creating Simple Virtual Hosts With mod_mysql_vhost On Lighttpd
[http://www.howtoforge.com/creating-simple-vhosts-with-mod_mysql_vhost-on-lighttpd-debian-etch](http://www.howtoforge.com/creating-simple-vhosts-with-mod_mysql_vhost-on-lighttpd-debian-etch)

to setup virtual hosting.

example.com = a registered domain
example.org = a free subdomain on "http://freedns.afraid.org/subdomain/"
(I don't have another registered domain for this testing)

Both domain points to the same public IP.  The public IP is also forwarded to the local IP of the VM.

Installation went through w/o much problem.  After finish "example.com" works without problem.  However example.org can't be browsed.

On console ping both domains working.

Any suggestion?  TIA

B.R.
satimis

---

### Post by elico on 2011-04-17
why shouldn't it?
VM is like a real machine that you configre and connect using Network Interface.
many companies are working with VHOSTS on VM guests.
almost  any hosting company uses that.

---

### Post by satimis on 2011-04-17
> **elico said:**
> why shouldn't it?
VM is like a real machine that you configre and connect using Network Interface.
many companies are working with VHOSTS on VM guests.
almost  any hosting company uses that.
Hi,

Yes, I agree.  But I'm stuck here for several hours on testing lighttpd.  vhosts with domain can be browsed but vhosts with subdomain can't be browsed.  I suppose it is the config problem.  But I got no reply from their forum nor mailing list.  

Does Apache2 have the same issue?  Any folk on the forum has any suggestion?  TIA

satimis

---

