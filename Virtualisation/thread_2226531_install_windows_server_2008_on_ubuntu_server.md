---
title: "install windows server 2008 on ubuntu server"
date: 2014-05-27
forum: Virtualisation
---

### Post by benlee12 on 2014-05-27
Hi :

I'm newbie, just installed Ubuntu server, now how can I install windows server 2008 r2 use xen ?

or how to work vm?? anyone can help ???

Ben

---

### Post by cariboo on 2014-05-28
You'll probably get better and quicker help here than in ABT.

---

### Post by TheFu on 2014-05-28
Welcome to the forums.  That is a huge question for a first post and for an admitted Ubuntu newbie.  Be prepared for a steep learning curve.

[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen) is the community how-to guide.
I've had issues with Xen on Ubuntu (hostOS refusing to boot after kernel updates) and switched away to KVM years ago. KVM has been extremely stable with excellent performance. KVM is usually the fastest hypervisor according to SPEC VM performance tests, but different workloads will produce different results on different hypervisors. In short, YMMV.

However, I do NOT run Windows servers.

The best information about Xen is probably available from Citrix. I understand they have active forums.

---

