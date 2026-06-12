---
title: "How to setup bridged networking in KVM - Tutorial"
date: 2011-06-25
forum: Virtualisation
---

### Post by Dedoimedo on 2011-06-25
Here's another nifty KVM tutorial. This topic is a little tricky, and so we have a tricky article. I will show you two ways you can get bridged networking up and running in KVM, one the usual method and the other a hack of pure genius. You will like this very much, I promise.

[http://www.dedoimedo.com/computers/kvm-bridged.html](http://www.dedoimedo.com/computers/kvm-bridged.html)


Regards,
Dedoimedo

---

### Post by Mr_Ust on 2011-06-27
I read the article. Great work, though I think the GUI screens can be hard to map to real commands for those of us who are running headless.

I'm wondering if you have an idea for how to create a bridged setup using an arp-proxy such as parprouted.  I've gotten the bridge setup to work, but my new hosting provider is only allowing one MAC per port.  So really I need to bridge all guests and the host across a second virtual device.

My idea was to create a tun/tap on the host with an internal IP, create a bridge out of this tun/tap INSTEAD of eth1 (like in your article), then connect all VMs directly to the bridge as before and configured with their external IPs.

Alternatively, I could use something like ebtables, but I think parprouted will do what I want and the interface is braindead.

---

### Post by Dedoimedo on 2011-06-27
Thanks!

I aimed for the average user, hence the screenshots. Haven't though about your setup ... hmm ... maybe I'll test that and see what gives.

Cheers,
Dedoimedo

---

