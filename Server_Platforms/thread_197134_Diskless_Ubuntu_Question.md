---
title: "Diskless Ubuntu Question"
date: 2006-06-15
forum: Server Platforms
---

### Post by secureboot on 2006-06-15
I've looked at
[https://wiki.ubuntu.com/DisklessUbuntuHowto?highlight=%28diskless%29](https://wiki.ubuntu.com/DisklessUbuntuHowto?highlight=%28diskless%29),
and i've got a couple questions about it.

I want to export the same NFS root to a bunch of clients.  I noticed that /etc is NOT a tmpfs on each client.

I can't figure out whether to export NFS root to clients rw or ro.

If you export rw, it seems like clients will overwrite /etc/hostname with the hostname they get from dhcp, which will screw things up on all the other clients, right?

If you export ro, no client will be able to set their hostname correctly...

It seems like there are a bunch of similar issues that crop up in the /etc directory with this.

What's the workaround here?  I'd rather not have to create a tmpfs /etc on each client, but if I have to, what's the easiest way to do this?  Where do you put the commands to generate the tmpfs for /etc?

---

### Post by coolclub on 2006-07-11
drbl.sf.net

---

