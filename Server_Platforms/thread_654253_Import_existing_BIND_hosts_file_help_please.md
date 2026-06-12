---
title: "Import existing BIND hosts file help please"
date: 2007-12-30
forum: Server Platforms
---

### Post by drhiii on 2007-12-30
Have searched and searched and am at an impasse....

I have an existing BIND installation.  Have installed a new server, including a new BIND v 9.3.2.  

Question is, how can I import the existing BIND file e.g.  xyz.com.hosts    into the new BIND installation.  Obviously copying the *.hosts into /var/lib/named/etc/bind directory did not work.  I have Webmin but could not find a way to import an existing .hosts file into the new installation.

Help anyone?

---

### Post by andol on 2007-12-30
Copying the zone-files is the right thing to do. Just that it is only half the solution. Now you also need to tell your new Bind to actually start using them. I have no idea how it works with Webmin, but here is a rather down to earth instruction how to manually setup Bind in Ubuntu.

[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

---

