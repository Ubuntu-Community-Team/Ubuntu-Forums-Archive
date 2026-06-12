---
title: "Recovery of files on EXT4"
date: 2010-01-09
forum: Security
---

### Post by karmic-koala on 2010-01-09
I had a question. This hasn't yet happened but was thinking what if it would.

So I run Ubuntu with my login as USER1. I have an external drive formatted as EXT4. Permissions on all folders on the drive is set such that USER1 has all access but group and others don't have any access.

My Ubuntu crashes and I reinstall, this time with login set to USER2. 

Will I still be able to access files on my external drive? I don't think so as all files can only be accessed by USER1 which doesn't exist. How does one access files on the external drive then?

---

### Post by unixbhaskar on 2010-01-09
Aha! you have one user called "root" in every GNU/Linux box....take help of that ;)

---

### Post by karmic-koala on 2010-01-09
Okay, so again scenario 2:

A colleague finds my USB drive (which I thought was safe because only me USER1 can access it). He su/sudo's in and can read all my data. 

That ain't very secure either (let's assume I am dumb and don't know about encryption, etc).

---

### Post by movieman on 2010-01-09
> **karmic-koala said:**
> A colleague finds my USB drive (which I thought was safe because only me USER1 can access it). He su/sudo's in and can read all my data.

Anyone with physical access to your hardware potentially has access to all your data unless it's encrypted: in the worst case they can boot from a live CD and then they're root... game over.

---

### Post by falconindy on 2010-01-09
physical access IS root access. Even encryption won't necessarily keep you secure. The only truly safe place for a computer is turned off, unplugged, locked in a safe, and guarded by a hungry mastiff.

---

