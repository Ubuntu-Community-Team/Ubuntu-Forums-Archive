---
title: "Server Management"
date: 2009-06-18
forum: Server Platforms
---

### Post by wolfteeth on 2009-06-18
Dont' know if anyone who can tell some about the Linux Environment Server Managment, by comparing to Windows platform, windows own the SCCM for server inventory, patch managment, software deployment, etc.. then what is on Linux? also, windows own MOM/SCOM to monitor service performance, what is for Linux Environment? 

Upgrade to Linux server from Windows Server is a expectation but requires the centralized SCCM/SCOM for linux, does anyone has experience or guide any tool for enterprise?

many thanks in advance for your any updates.

---

### Post by yota on 2009-06-18
Hi,

for a commercial solution have a look at: [http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape)

for a free solution look at [http://packages.ubuntu.com/jaunty/puppet](http://packages.ubuntu.com/jaunty/puppet) and [http://packages.ubuntu.com/jaunty/puppetmaster](http://packages.ubuntu.com/jaunty/puppetmaster) (available in the repositories)

also please consider that also a little switch in the perspective is needed.
On windows world there is a single vertical application that tries to serve a user's need (top-down monolithic approach) on the unix side usually you have to mix&match different tools to build your own solution for your specific needs (each tool does just one thing, but it's highly specialized and it does in the best way).

hope this helps!

---

### Post by wolfteeth on 2009-06-18
many thanks for your information and advise.

the only problem is that the Puppet is the command line without any GUI...but Landscape is not for free...

:)

---

