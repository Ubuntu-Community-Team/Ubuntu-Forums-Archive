---
title: "How to mount at startup a drive from fstab only if is found"
date: 2010-10-02
forum: Server Platforms
---

### Post by al_mic on 2010-10-02
Hello,

I want to ask if you know a way to place some lines in /etc/fstab for drive mounting at startup, but also check if that drive exists.

What I want to do, is to have in /etc/fstab something like this:

/dev/sdh /persistent ext3 defaults 0 0
/persistent/usr/local/pg84 /usr/local/pg84 none bind

Problem is that sometimes, at startup, /dev/sdh does not exists. (that drive is not there yet because I plug it out)
And if /dev/sdh does not exists, then my line from fstab will generate an error, and even make my server not be able to start.

Is there a way to check if that drive exists and then mount it?
I need this to be done automatic at startup.
Like, if /dev/sdh is found, then mount it, if not, don't mount it, and start everything else.

Thanks!

---

