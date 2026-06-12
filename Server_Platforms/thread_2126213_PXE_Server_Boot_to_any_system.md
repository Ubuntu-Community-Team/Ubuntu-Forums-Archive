---
title: "PXE Server Boot to any system??"
date: 2013-03-16
forum: Server Platforms
---

### Post by drumltd on 2013-03-16
I have setup a PXE boot server, and sucessfully installed Ubuntu Server 32bit to boot from the server. The first client (the one I used for setup) boots just fine.

However when I try to boot any other machine they get asfar as scripts\init-bottom then appear to hang.

The machines are different specs, so I was wondering is there something I've done wrong, or is there a way I can make the installation more portable to the other clients?

---

### Post by drumltd on 2013-03-16
I have been playing with some other boot images, and found that this not not specific to bee na server setup like I thought it was, and the same happens with a desktop ubuntu install.

I suspect the problem is related to booting from a remote NFS drive. With this in mind is it possible for a moderator to move this thread to a more appropriated section?

---

