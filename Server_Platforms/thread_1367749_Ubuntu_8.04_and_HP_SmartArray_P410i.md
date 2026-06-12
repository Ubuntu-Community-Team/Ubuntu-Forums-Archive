---
title: "Ubuntu 8.04 and HP SmartArray P410i"
date: 2009-12-29
forum: Server Platforms
---

### Post by calmkelp on 2009-12-29
I have a number of HP Proliant DL160 G6 servers with the SmartArray P410i and no battery backed cache upgrade.

A while back HP released and advisory on issues with this config:

[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c01688233](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c01688233)

There are kernel updates from RedHat and SUSE to address the issue, but I've seen nothing from Ubuntu.

I've had little luck building the CCISS driver module source HP provides here:

[http://cciss.sourceforge.net/](http://cciss.sourceforge.net/)

I've reported a bug in the kernel here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499312](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499312)

Basically the kernel spews this message over and over any time there is moderate or high disk IO:

cciss: fifo full

There may also be a significant performance impact to this issue. HP warns that the controller can stall at random times. 

Has anyone run into this issue and come up with a fix for Ubuntu 8.04? Upgrading to a non-LTS release isn't an option for me right now. Nor is waiting for 10.04.

I've also seen this issue on DL380 G6 servers, but added a battery backed cache, which fixed the problem. I'd rather avoid the expense with the DL160s.

---

