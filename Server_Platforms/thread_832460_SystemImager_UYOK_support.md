---
title: "SystemImager UYOK support"
date: 2008-06-17
forum: Server Platforms
---

### Post by porterde on 2008-06-17
Hi,

I am trying to get SystemImager UYOK support to work on Ubuntu 7.10 (although 8.04 has the same problem).  According to the documentation, this is done with this command:

  prepareclient --server <myserver> --no-rsyncd --my-modules

which returns:

  Unknown option: my-modules

This should be available in 3.6.  The odd thing is that dpkg says I have 3.2 (which is super old), but if I apt-get the source, it is for 3.6.  So which version is really shipped with ubuntu?

And is there any chance of an update?  The current stable release is 4.0.2.

Any help is much appreciated.

---

