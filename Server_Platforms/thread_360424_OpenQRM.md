---
title: "OpenQRM?"
date: 2007-02-13
forum: Server Platforms
---

### Post by chewie124 on 2007-02-13
I just read the [article from ONLAMP]("http://www.onlamp.com/pub/a/onlamp/2007/02/08/managing-virtualization.html") about [OpenQRM]("http://www.openqrm.org").

From the article:
> openQRM, which just reached version 3.1, is an open source cluster resource management platform for physical and virtual data centers. In a previous life it was a proprietary project. Now it's open source and is succeeding in integrating different leading open source projects into one console. With a pluggable architecture, there is more to come. I've called it "cluster resource management," but it's really a platform to manage your infrastructure.

Whether you are deploying Xen, Qemu, VMWare, or even just physical machines, openQRM can help you manage your environment.

I've got some Xen servers, and it definitely sounds like an interesting project.  

Anybody ever use OpenQRM with Ubuntu?  What's your experience with it?

---

### Post by Brazen on 2007-02-13
OpenQRM is definately an "interesting" project.  We use VMWare ESX Server here so I thought it would be redundant to use OpenQRM.  There would be additional features using OpenQRM along with VMWare, but for myself, the features I would want could be had with just a Nagios server anyway, so I have not explored it.

Besides, I think one of the components that OpenQRM uses _is_ Nagios, so I need to figure that out first.  A little advice, OpenQRM is a complicated beast, but break it down and take it one piece at a time and you'll figure it out.

---

