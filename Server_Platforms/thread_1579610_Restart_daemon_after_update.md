---
title: "Restart daemon after update"
date: 2010-09-22
forum: Server Platforms
---

### Post by manski on 2010-09-22
Hi everyone,

I'm using Ubuntu (and Debian before that) on several servers for some time now, but there's one question I didn't find an answer for yet. Maybe you can help:

How do I know whether I need to restart a certain daemon after updating a package?

An example: Today I updated "libssl" to its current version (I'm using Ubuntu Server 10.04). As far as I know this is a dynamically linked library and it's being used for example by the OpenSSH server. Now when I update this library, do I need to restart the OpenSSH server so that it can use the new version of libssl? Or does it use the new version automatically (which I doubt)?

Furthermore then: If I need to restart daemons depending on a certain library, is there any way to find out which daemons need to be restarted? As far as I can see, apt-get doesn't restart any daemons (except those whose packages had been updated as well).

Tanks for any help.

Regards
Manski

---

### Post by manski on 2010-09-28
(bump)

---

### Post by linux-hack on 2010-09-28
Well sometimes you don't need to restart it just force it to read agen his config. I know this works on solaris but I don't know if it works in linux. something like (service refresh openssh).

And I know that kernel updates need reboot but not everything else. It depends on the application I think. But for the libs I don't think so.

---

