---
title: "How to make my USB ports password protected?"
date: 2008-07-20
forum: Security
---

### Post by sambhav on 2008-07-20
I am newbie to linux and i nees to know wether it is possible to make USB ports password protected so that limited users can acess it

---

### Post by bogdanbiv on 2008-07-20
It's unclear to me if you want to grant more rights to users or you want to restrict them to use a password whenever using usb devices.

If the first is true (most common):
Add the users to the fuse system group, though I'm still not sure that is the right group. They will be able to access it, but other than the password introduced at login there is no further authentication.

I would have provided more details on how to do that if you mentioned which edition of Ubuntu you have (what desktop environment...).

---

### Post by sciurus on 2008-07-20
I believe the proper group is plugdev, not fuse. To restrict the use of USB storage devices, you can edit the authorizations for org.freedesktop.hal.storage.mount-removable using polkit-gnome-authorization.

---

