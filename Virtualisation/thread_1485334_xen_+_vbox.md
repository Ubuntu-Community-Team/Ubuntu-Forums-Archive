---
title: "xen + vbox"
date: 2010-05-16
forum: Virtualisation
---

### Post by u_kapaley256 on 2010-05-16
Hi all,
      I have virtualbox on my system that i use occasionally.Now i need to install xen for a project.Would that be fine ? I wont be using them simultaneously of course but they both would be installed on the system...
Thanks 
Udayan

---

### Post by TheFu on 2010-05-16
I don't know if it is actually possible, perhaps you can have both on the same partition, but I wouldn't.

I know you can have both a Xen kernel and a non-Xen kernel in your grub config and select which to boot. That definitely works.

Whether you can only load the virtualbox modules in the non-Xen kernel easily enough is what I don't know. Would other startup scripts get in the way?  Probably.

Honestly, I'd setup a 10GB partition for the least used kernel, settings and setup grub to boot that specifically to avoid the mixed hypervisor package issue. I normally setup 20GB for / and place all the other important things on their own partitions (/var, /home, /opt) so they can easily be retained between OS upgrade, reinstalls.

---

