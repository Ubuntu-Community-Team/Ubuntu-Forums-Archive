---
title: "music files requiring root access..."
date: 2012-04-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Baldrick_NZ on 2012-04-09
Hi all, 

I've just discovered that in 12.04 all my music files have locked symbol on them. They can be played fine, and I can unlock then one-by-one using 'gksu nautilus', but this is will be a very drawn out process.

Is there a simple script that I can run which will assign each file to my user name, all at once as a batch?

Any help would be much appreciated...

---

### Post by lisati on 2012-04-09
I'm wondering if it's a permissions and/or ownership issue.

---

### Post by Baldrick_NZ on 2012-04-09
> **lisati said:**
> I'm wondering if it's a permissions and/or ownership issue.

It was ownership. Thanks for that, but I found the answer from my friend Google, here.. [http://ubuntuforums.org/showthread.php?t=1556352](http://ubuntuforums.org/showthread.php?t=1556352)

Cheers.

---

### Post by kurja on 2012-04-09
I'll borrow this thread to ask a related question - I have an internal hard drive, to which I copied everything from an old failing one while booted from a live cd, and after resuming to run from "normal" boot I had no access to those files unless as root untill I ran "chown -R username:username", but now of course I only have access as "username"...

How to change permissions/ownership so that the disk and it's contents are available to all users?

---

