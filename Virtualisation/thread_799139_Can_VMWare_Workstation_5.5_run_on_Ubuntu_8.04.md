---
title: "Can VMWare Workstation 5.5 run on Ubuntu 8.04?"
date: 2008-05-18
forum: Virtualisation
---

### Post by xp_newbie on 2008-05-18
Can VMWare Workstation 5.5 run on Ubuntu 8.04?

I know that VMWare Workstation 5.5 can run on Ubuntu 6.06.
But can it run on Ubuntu 8.04?

Thanks,
Alex

---

### Post by Malac on 2008-05-23
> **xp_newbie said:**
> Can VMWare Workstation 5.5 run on Ubuntu 8.04?
 
I know that VMWare Workstation 5.5 can run on Ubuntu 6.06.
But can it run on Ubuntu 8.04?
 
Thanks,
Alex
I am currently working on this.
I have got it to compile using the any-any-116 patch however it won't run as yet due to driver errors I am going to try a fix tonight when I get home. Will let you know how it goes.
Or if you want to try it yourself.
```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

---

### Post by bgoody on 2008-05-23
Hi.  I tried but couldn't get it to work without major fooling around.  I noticed that the upgrade to 6 was $100 so I tried the demo and it installed as expected.  The product has enough changes to warrant the upgrade anyway beside the fact that it installs easily.
Brian

> **xp_newbie said:**
> Can VMWare Workstation 5.5 run on Ubuntu 8.04?

I know that VMWare Workstation 5.5 can run on Ubuntu 6.06.
But can it run on Ubuntu 8.04?

Thanks,
Alex

---

### Post by dpj23 on 2008-05-23
One quick note... Any Machines created in workstation6... you won't be able to play them with workstation 5.5....  Now this also affects vmplayer as well...  Any machines created with workstation 6 you won't be able to play them with player 1.4... You'll need vmplayer 2.0...  This comes with workstation 6...

---

### Post by xp_newbie on 2008-05-24
Folks, thank you for letting me know about this. I have been working with VMWare Workstation 5.5 under Ubuntu 6.06 for a long time with great satisfaction.

I am trying to minimize expenses for now, so I wonder whether Xen is now up to task.

By "task" I mean: can it run Windows XP in a virtual machine?

I know that Xen requires IVT in order to run Windows XP and I believe that my CPU has that support. The question now is whether Xen is as user friendly an polished as VMWare. 

Any experience with Xen?

Thanks,
Alex

---

