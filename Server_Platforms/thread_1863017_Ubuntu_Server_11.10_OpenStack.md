---
title: "Ubuntu Server 11.10 OpenStack"
date: 2011-10-17
forum: Server Platforms
---

### Post by davim on 2011-10-17
Hello.
Is there some tutorial for deploy openstack with ubuntu 11.10

---

### Post by kirbini on 2011-10-18
> **davim said:**
> Hello.
Is there some tutorial for deploy openstack with ubuntu 11.10

Likewise.  The press for the new release is all about how OpenStack is built-right in.  So I downloaded the newest server release but there are no nova, swift or glance components installed.  I re-ran the installation thinking I must have missed something but no, no cloud/OpenStack install options.  apt-cache will list all kinds of OS components but that's about as useful as learning to build houses by touring a lumber yard.   The only docs I can find (outside the press about how OpenStack is the new cloud and comes with Ubuntu) is this blog:

[http://cloud.ubuntu.com/2011/10/ubuntu-cloud-deployment-with-orchestra-and-juju/](http://cloud.ubuntu.com/2011/10/ubuntu-cloud-deployment-with-orchestra-and-juju/)

Unfortunately the single server image is only available for AMD and the rest of the instructions require multiple servers which we don't have for testing.  *sigh*

It'd be nice if there was an Intel single-server install or a "here's the parts you need to install for a single server" how-to.  Has anyone seen either?

---

### Post by kirbini on 2011-10-18
Ok, I'll bite on my own post.  Found this:

[http://cloud.ubuntu.com/2011/08/ubuntu-natty-gets-openstack-book/](http://cloud.ubuntu.com/2011/08/ubuntu-natty-gets-openstack-book/)

it's not a how-to, and I admit to not having read any of it other than the ToC, but it may help.  A how-to for us aging geeks without the time to RTFM would still be nice though...

---

