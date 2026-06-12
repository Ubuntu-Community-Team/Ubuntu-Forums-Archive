---
title: "VMware 1.0.6 build-91891 and Keyboard input problems in other apps"
date: 2008-08-01
forum: Virtualisation
---

### Post by toucher5 on 2008-08-01
I have VMware Server 1.0.6 build-91891 and Ubuntu 8.04 up to date. I have an issue with keyboard input in the host environment after running a virtual machine where any keyboard input in host will cause the other app to close. (i.e., Firefox - typing in address or anything closes window)

Has anyone encountered this and if so how do you fix this?

Thanks

---

### Post by Masoris on 2008-08-02
That's a famous bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982)

---

### Post by thetillster on 2008-10-30
Thank you, this link helped me understand what it is happening, though the bug is not fixed completely, I will try some of the work-arounds.

---

