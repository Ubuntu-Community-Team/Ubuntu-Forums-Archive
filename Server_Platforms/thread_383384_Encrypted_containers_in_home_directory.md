---
title: "Encrypted containers in home directory"
date: 2007-03-13
forum: Server Platforms
---

### Post by nocturn on 2007-03-13
I would like to set up an encrypted part of my homedirectory.  Much like I did using LUKS on a flash drive.

The requirement is that it can be mounted as a user.

What is the best way to go about this?

---

### Post by Frosty Cold Drink on 2007-03-13
I *just* posted this for another thread. Take a look: [http://ubuntuforums.org/showthread.php?t=383657](http://ubuntuforums.org/showthread.php?t=383657)

I use(d) EncFS to encrypt subdirectories of my home directory. You can mount an encrypted filesystem, use it like normal, then unmount it when you are done.

---

### Post by nocturn on 2007-03-14
> **Frosty Cold Drink said:**
> I *just* posted this for another thread. Take a look: [http://ubuntuforums.org/showthread.php?t=383657](http://ubuntuforums.org/showthread.php?t=383657)

I use(d) EncFS to encrypt subdirectories of my home directory. You can mount an encrypted filesystem, use it like normal, then unmount it when you are done.

Thanks!  I'll try it out.

---

