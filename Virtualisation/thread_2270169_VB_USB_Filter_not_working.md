---
title: "VB USB Filter not working"
date: 2015-03-20
forum: Virtualisation
---

### Post by jcllings on 2015-03-20
Problem: Ubuntu grabs and mounts my phone even if I have a filter specified in VirtualBox. 
See here:
[https://forums.virtualbox.org/viewtopic.php?f=8&t=45349](https://forums.virtualbox.org/viewtopic.php?f=8&t=45349)

It shows up as this:
Bus 003 Device 015: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II], GT-I9300 Phone [Galaxy S III], GT-P7500 [Galaxy Tab 10.1]

..however it's actually a Galaxy Note 4. 

Could use some trouble shooting tips. How might I tell fuse to completely ignore the device for example?

---

### Post by jcllings on 2015-03-20
Solved. You have to be a member of the vboxusers and vboxsf groups before filters start working.

---

