---
title: "Network mount to appear as a device"
date: 2013-01-02
forum: Server Platforms
---

### Post by tornadof3 on 2013-01-02
Hello

I am interested in using either SAMBA or NFS to mount shared resources on a file server to be accessed from a pool of ubuntu clients. Previously I have just had this mount to a certain folder (usually in /mnt) and the users navigate there or have shortcuts etc.

Is it possible to get an NFS or Samba share to mount as a 'device' so in nautilus it would have a similar link as say a USB drive?

~Thanks

---

### Post by darkod on 2013-01-02
If I'm not mistaken, it depends on the destination mount. /mnt is part of Filesystem and doesn't show as device on the left side in Nautilus.
But /media does show.

You can test easily. Create for example /media/share1 and mount one samba share there, and see how it shows in Nautilus. It should be there and usable even without clicking on it first.

If that works, you can even mix shares. Have some of them mount at /mnt without showing in Nautilus directly, and have others mount at /media.

---

### Post by tornadof3 on 2013-01-02
That is a really smart idea - I'll give that a try. Thanks!

---

