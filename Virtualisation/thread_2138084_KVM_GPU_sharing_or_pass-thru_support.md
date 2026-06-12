---
title: "KVM GPU sharing or pass-thru support?"
date: 2013-04-22
forum: Virtualisation
---

### Post by tree chang on 2013-04-22
I'm looking for a solution for sharing or pass-thru my GPU to VM with Ubuntu KVM.
Can Ubuntu KVM support GPU sharing or pass-thru? How can I do that?
Is specific GPU required?

---

### Post by Cheesemill on 2013-04-23
For PCI passthrough to work you need to have the following things....

A CPU that supports VT-d or AMD-Vi.
A motherboard that supports VT-d or AMD-Vi.
BIOS that supports VT-d or AMD-Vi.
A graphics card that supports VGA passthrough.

If you have all of these then yes, you can set up PCI passthrough with KVM on Ubuntu.

You may want to take a look at this thread...
[http://ubuntuforums.org/showthread.php?t=2111175](http://ubuntuforums.org/showthread.php?t=2111175)

---

### Post by tree chang on 2013-04-25
Thanks for the information.
But I checked the thread. All the success in the thread are for xen.
[http://ubuntuforums.org/showthread.php?t=2111175](http://ubuntuforums.org/showthread.php?t=2111175)
And is there solution for sharing GPU between VMs at the same time like VMware does?

---

### Post by heiko_s on 2013-04-26
> **tree chang said:**
> Thanks for the information.
But I checked the thread. All the success in the thread are for xen.
[http://ubuntuforums.org/showthread.php?t=2111175](http://ubuntuforums.org/showthread.php?t=2111175)
And is there solution for sharing GPU between VMs at the same time like VMware does?

While I'm using Xen, there are reports that kvm will work too. Here is a short howto, though not Ubuntu specific: [http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787]("http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787").

I've posted a howto using Xen on Linux Mint (Ubuntu-based) here: [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013"). Perhaps you like to try Xen? Even if you use kvm, the hardware advise and the links posted in this howto may be helpful.

As someone above already wrote: You need compatible hardware and BIOS. Don't even think about trying if any of the mentioned requirements are not met. This is true for both Xen and kvm.

---

