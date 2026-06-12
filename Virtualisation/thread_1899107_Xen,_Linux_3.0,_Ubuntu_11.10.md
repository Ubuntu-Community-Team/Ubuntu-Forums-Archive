---
title: "Xen, Linux 3.0, Ubuntu 11.10"
date: 2011-12-22
forum: Virtualisation
---

### Post by DeadlyOats on 2011-12-22
I googled xen and found some articles about Linux including a bunch of tools and depends for xen - natively in the 3.0 kernel this past July.

I have it to understand that Ubuntu 11.10 uses the 3.0 Linux kernel.....

So, why aren't there any howto's or talk about it here in this forum?  It's six months later....

---

### Post by Dangertux on 2011-12-22
> **DeadlyOats said:**
> I googled xen and found some articles about Linux including a bunch of tools and depends for xen - natively in the 3.0 kernel this past July.

I have it to understand that Ubuntu 11.10 uses the 3.0 Linux kernel.....

So, why aren't there any howto's or talk about it here in this forum?  It's six months later....

What do you want to know about it?

```

sudo apt-get install xen-hypervisor-4.1-i386

```OR

```

sudo apt-get install xen-hypervisor-4.1-amd64

```If you just want to install the hypervisor. If you want something else feel free to post.

---

### Post by DeadlyOats on 2011-12-23
Thanks for the reply.  I was really asking, because there's a sticky up there for Xen on Ubuntu 9.04, but nothing updated since then.  I figured someone would have updated the stickies, or something by now.....  That's all.

Is there a reason nothings been updated in those stickies?

---

### Post by nupur on 2012-01-02
I have been trying to install Xen on Ubuntu 11.10
I am following the steps given in this blog.  [http://www.beyondlinux.com/2011/11/02/install-xen-4-1-and-setup-your-cloud-os-on-ubuntu-11-10/](http://www.beyondlinux.com/2011/11/02/install-xen-4-1-and-setup-your-cloud-os-on-ubuntu-11-10/) 

Though, after the first 1 step, when I reboot. I do not have a Xen entry to boot into. It still shows the same grub entry.

Will having a desktop ubuntu make any difference?

Any suggestions.

---

