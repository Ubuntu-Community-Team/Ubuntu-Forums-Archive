---
title: "KVM &amp; Spice on 12.04"
date: 2013-10-04
forum: Virtualisation
---

### Post by KillerKelvUK on 2013-10-04
Started looking at Spice as a way to improve gfx and audio...hit a bug and found this...[https://bugs.launchpad.net/ubuntu/+source/qemu-kvm-spice/+bug/970234](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm-spice/+bug/970234).

Seems the problem has been resolved in 13.04+, however I can't upgrade to 13.04 desktop as there is a different bug with creating KVM guests in an LVM :(   The launchpad thread above talks about upgrading qemu-kvm-spice to version 1.2 but I've googled and can't locate a solution for doing this in 12.04, has anybody else got a quick fix for this as I don't want to start building my own binaries?

Thanks,

K

---

### Post by Rob_H on 2014-02-08
I'm battling this, too. Did you ever find a solution?

---

### Post by TheFu on 2014-02-09
a) 13.04 is out of support now. You could migrate (not necessarily an upgrade) from 12.04 --> 12.10 --> 13.04 --> 13.10 in the mean time. Have fun! Definitely do it on a test system first.
b) Probably best to wait until late April and install 14.04 LTS.

I was able to get spice working on 12.04. The audio worked, but the video was still choppy over a wired GigE network. Plus, some of the keyboard mapping was terrible. Important keys were not mapped from either Windows7 clients or Ubuntu clients.

In the end, I switched back to using FreeNX servers and the NoMachine nx client v3.5x for all the other reasons I run desktops inside VMs - not audio or video.

---

### Post by Rob_H on 2014-02-09
I moved to 13.10 and it is working now.

---

### Post by TheFu on 2014-02-09
Now if we could just get the OP to mark thread as "solved"?

---

### Post by KillerKelvUK on 2014-02-10
Sorry guys been a whilst since I checked in and I didn't subscribe to the thread.  Appreciate the updates which is great news, will be waiting until April for the 14.04 release personally.

K

---

