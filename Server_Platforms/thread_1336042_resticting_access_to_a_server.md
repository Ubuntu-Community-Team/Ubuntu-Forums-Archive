---
title: "resticting access to a server"
date: 2009-11-24
forum: Server Platforms
---

### Post by ccaaee on 2009-11-24
I've been trying to restrict access of one of our servers on the lan to only certain hosts.  For example, if I don't and a host with the ip address 192.168.1.5 to access 192.168.1.6, one would normally simply:

echo "ALL: 192.168.1.5" >> /etc/hosts.deny on 192.168.1.6  ...  

This doesn't seem to work.  192.168.1.5 can still access (at least) the web server on 192.168.1.6.  What am I doing wrong ???

---

### Post by Lars Noodén on 2009-11-24
Which web server and does it support tcpwrappers also called tcpd?

---

### Post by ccaaee on 2009-11-24
... Sorry  Apache2.  I might add that my original intent was simple to block access to the web server but upon reflection I thought that certain hosts shouldn't have any access to this machine. I had not hear of tcpwrappers before but I guess that's one of the good things about these forums - you get led to other things...  All the same, it seems to me that at one time one could simple use host.deny and host.allow to tailor across-the-board access to all services on a server independently of protocol.  Was I dreaming?

---

### Post by Bag-O-Stuff on 2009-11-24
Apache doesn't use the allow and deny files without some added work.  Apache has a number of other ways to do what you are looking for built in.  One is called mod_access.  Here's the documentation from their site.  It allows allow and deny by domain, host name, IP, etc...

[http://httpd.apache.org/docs/2.0/mod/mod_access.html](http://httpd.apache.org/docs/2.0/mod/mod_access.html)

---

### Post by i.r.id10t on 2009-11-24
Look at hte default sites-available file (/etc/apache2/sites-available/default or something like that) - there is an example in there about how viewing the docs is restricted to localhost.

---

### Post by Lars Noodén on 2009-11-24
Ok.  The proper way to do it with Apache would be to set [access control](http://httpd.apache.org/docs/2.2/howto/access.html) by host or subnet.  

See also various howtos and tutorials on access control. e.g.  [Restricting Website Access with Apache 2](http://httpd.apache.org/docs/2.2/howto/access.html)

---

### Post by ccaaee on 2009-11-24
Thanks a million, that did the trick.  I would, nevertheless, quite like to know about the hosts.allow,hosts.deny issue...  I thought it was possible to use these files to deny access to all services from a specific host.

---

### Post by Bag-O-Stuff on 2009-11-24
It can only allow or deny services to those services that abide by it.  For example, you can compile certain services to use tcpwrappers or not to use tcpwrappers.  If you do the latter, it won't matter what resides in the hosts.allow and hosts.deny files.  Many services use tcpwrappers by default, Apache doesn't.

---

### Post by Lars Noodén on 2009-11-25
@*ccaaee : As Bag-O-Stuff points out, the programs have to have recognition of tcpd built in during compilation.  You'll sometimes see this referred to as tcpd-aware or tcpwrappers-aware.

Apache happens to be one of the few common applications which is not tcpd-aware, mostly because it has its own set of access controls.

---

