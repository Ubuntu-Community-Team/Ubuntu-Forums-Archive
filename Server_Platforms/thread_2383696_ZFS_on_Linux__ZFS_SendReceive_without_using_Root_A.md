---
title: "ZFS on Linux:  ZFS Send/Receive without using Root Account?"
date: 2018-01-28
forum: Server Platforms
---

### Post by mattlach on 2018-01-28
Hey all, I'd like to pick your brains on this.

My main storage server uses ZFS for all of its storage needs.   I recently was able to set up a hosting agreement, where I can put my old storage server offsite, and back up to it.

I would like to do this using ZFS Send/Receive over SSH.

The problem is this.  ZFS seems to expect that you log in as root in order to accomplish this.  Call me crazy, but I just don't like the concept of having root account login enabled on a public IP address. I've always liked that Ubuntu disables root logins by default.

Is there a better way to accomplish this?

I've done some googling and found suggestions to enable root logins, but only using RSA keys, not using password, with the argument that this doesn't really compromise security.

What do you guys think?  What is the best approach?

Thanks,
Matt

---

### Post by rperkins on 2018-01-29
maybe setup a vpn with openvpn ?

---

