---
title: "Automatically mount home directory from network share"
date: 2009-03-27
forum: Server Platforms
---

### Post by null-cipher on 2009-03-27
Hi everybody.
I'm setting up a small office system for my brother and I was wondering if anybody would have any suggestions for the following issue:

I am looking to have each user's home directory mounted on a network share, but if the user does not have access to the network for whatever reason (perhaps it's a laptop) they can write their files onto the local disk.

I was thinking:
- Have a log-in script that will try to mount the network share and if it fails, mount a local directory
- On shutdown, have a log out script that would copy all of the network share onto the local computer (so that they do not lose access to files they have been working on)
- Perhaps a log in/out script to sync the files?

If anybody has any pointers on how to make a log in script, it would help me greatly, or any other ideas on how to do this better. My method is a bit hack-y when I think about it, but it seems practical.

Oh! Also, clients will most likely be running Ubuntu 8.04 LTS if that is relevant.

Thanks.

---

### Post by doogy2004 on 2009-03-29
Check this out [http://www.ibiblio.org/oswg/oswg-nightly/oswg/en_US.ISO_8859-1/articles/gdm-reference/gdm-reference/configuration.html](http://www.ibiblio.org/oswg/oswg-nightly/oswg/en_US.ISO_8859-1/articles/gdm-reference/gdm-reference/configuration.html)

---

