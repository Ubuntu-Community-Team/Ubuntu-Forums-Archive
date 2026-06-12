---
title: "Installing Tomcat 6 manually or from repository?"
date: 2010-05-13
forum: Server Platforms
---

### Post by leesiulung on 2010-05-13
So researching how to install Tomcat 6, I ran across a [guide ]("http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/")that specifically states there are issues with the repository version of Tomcat. Doing some more research it seems like this is reported in multiple places including a disussion on the [official mailing list ]("http://groups.google.ca/group/ubuntu-users-archive/browse_thread/thread/ca16d0714f43420d/f0646c6434ea2529?#f0646c6434ea2529")that was inconclusive. 

So my question is, if this is intended for a production server should I use the repository one or manually install it?

Does this suggest I can't trust the repository to keep my software updated properly?

---

### Post by leesiulung on 2010-05-15
I guess nobody uses Tomcat here?

Official Mailing list response:

[http://www.mail-archive.com/users@tomcat.apache.org/msg52780.html](http://www.mail-archive.com/users@tomcat.apache.org/msg52780.html)

Official bug filed here:

[https://bugs.launchpad.net/ubuntu/+source/libcommons-dbcp-java/+bug/315314](https://bugs.launchpad.net/ubuntu/+source/libcommons-dbcp-java/+bug/315314)

It seems like a bunch of the threads discuss how the startup script is broken and etc....

---

### Post by iversonm on 2010-05-16
I have a vanilla install of Alfresco running on the packaged Tomcat installation under 10.04. I've not noticed any Tomcat related bugs.  I wouldn't hesitate to install the packaged version. The specific bug you mentioned, per launchpad, was fixed in January, 09. 

In general, I think you need a fairly concrete reason to want to maintain a generic install of a package vs. the maintained package. There is a very real maintenance cost to keeping a package up to date and secure. It is not difficult, but too many installs to maintain starts to be a resource drain. Besides, if you really get in a bind, you could always buy support from Canonical.

Concrete reasons do start popping up when you start messing with multiverse and universe packages, since some of these can be out of date or have spotty quality.

---

