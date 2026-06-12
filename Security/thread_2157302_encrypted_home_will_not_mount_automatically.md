---
title: "encrypted /home will not mount automatically"
date: 2013-06-24
forum: Security
---

### Post by ipeurtt on 2013-06-24
Hi guys,

I wounder if anybody can help with this issue:

I moved my /home folder to a new partition, following this guide:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

The issue is that my /home was encrypted, so it ended up moving the encrypted version, as well as the unencrypted one.

I reasoned that if I deleted my /home/username folder, then it would decrypt and mount automatically when at login.  Well, that's not happening. I now have the /home/.ecryptfs folder, but it will not mount at login.

I'm able to decrypt and mount its contents on a temporary folder by following this:

[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

But what I'd like to be able to do is to have it mount on /home/username at login

I've tried several things I've found at various threads, but nothing seems to work.

Any help would be appreciated.

Thank you

---

