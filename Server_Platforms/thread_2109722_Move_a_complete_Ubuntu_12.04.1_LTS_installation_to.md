---
title: "Move a complete Ubuntu 12.04.1 LTS installation to another server"
date: 2013-01-28
forum: Server Platforms
---

### Post by Gilgha on 2013-01-28
Hi,

I rent a dedicated server running Ubuntu 12.04.1 LTS and I will soon move to an other dedicated server provider. Everything is running fine and I don't wanna waste my time re-configuring everything from a stock Ubuntu 12.04.1. Is there a way to move a complete Ubuntu 12.04.1 installation from a server to an other server without having physical access to the machines?

Thanks.

---

### Post by tgalati4 on 2013-01-28
There may be a cloud-based tool to do this.  Tools such as:
oem-config-remaster - Remaster a CD with additional oem-config functionality
and remastersys require a physical CD/DVD, although you could create the *.ISO file put it on Ubuntu One, then use unetbootin to try to install it remotely.  You would have to change some network configuration parameters, so your machine would be down until that is done.

I'm not aware of a Live Migration tool that can work across physical machines, although kernel virtual machine (KVM) has the hooks to do it.  When searching for "Live migration Ubuntu server" this comes up:

[http://www.bearfruit.org/2010/04/14/migrate-a-live-server-from-ubuntu-to-debian-remotely/](http://www.bearfruit.org/2010/04/14/migrate-a-live-server-from-ubuntu-to-debian-remotely/)

It's from 2010, so I'm sure there are better tools to do this now.

---

