---
title: "Running KVM as normal user vs root (and a firewall question)"
date: 2011-12-27
forum: Virtualisation
---

### Post by CharlesA on 2011-12-27
Hiya,

I was thinking that I would configure KVM to run as a regular user instead of root. Is this a common practice and if so, what is the best way to set it up.

I found a pretty good howto [here]("http://itscblog.tamu.edu/startup-guide-for-kvm-on-centos-6/"), but I'm not 100% sure if I can access KVM with my normal account if I use the group setting and have the KVM images stored as another user.

Any ideas?

Also, since I am going to be using bridged networking, will I only have to firewall the bridge, or both br0 and eth0?

---

### Post by CharlesA on 2011-12-29
Giving this a bump. Any thoughts/ideas?

I figured out the firewall thing, both interfaces are firewalled since I did not specific an interface in the rules I use.

---

