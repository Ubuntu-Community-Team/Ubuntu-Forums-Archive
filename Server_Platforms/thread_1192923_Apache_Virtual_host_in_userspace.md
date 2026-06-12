---
title: "Apache: Virtual host in userspace?"
date: 2009-06-20
forum: Server Platforms
---

### Post by paradigm2 on 2009-06-20
Hello I have a dedicated server. What I want to do is set up a separate account for each domain.  i.e. -

mydomain1.com  account:mydomain1
mydomain2.com  account:mydomain2
mydomain3.com  account:mydomain3

These will be strictly name based.

I can figure out how to do the httpd.conf file but my question is how do I handle permission issues?  Apache needs to be able to access the files within the user's home directory.

I want the structure to be like:

/home/mydomain1/mydomain1.com/  <--- this would be [http://mydomain1.com](http://mydomain1.com) root

This way each domain has a separate login and can be administered via sftp and telnet.

To complicate this I will also be installing mysql and php and all these domains will make use of those.

Any advice?  Tips?

---

### Post by windependence on 2009-06-21
In Ubuntu, you don't use the httpd.conf file. The main configuration is file located at /etc/apache2/apche2.conf. For virtual hosts you also need to configure /etc/apache2/conf.d/virtual.conf and /etc/apache2/sites-available.

[http://www.corey-m.com/blog/?p=315](http://www.corey-m.com/blog/?p=315)

-Tim

---

