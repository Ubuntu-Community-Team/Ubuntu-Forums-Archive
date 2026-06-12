---
title: "Virtualize Netbsd in ubuntu?"
date: 2009-03-31
forum: The Cafe
---

### Post by linuxisevolution on 2009-03-31
Virtualbox is not compatible with Netbsd, and I would really like to try netbsd (get dhcp, X setup, decent DE) before I do a full hdd install on another computer. 

I don't have the money for Vmware....

Would qemu work? It's interface looks confusing.

---

### Post by dragos240 on 2009-03-31
> **linuxisevolution said:**
> Virtualbox is not compatible with Netbsd, and I would really like to try netbsd (get dhcp, X setup, decent DE) before I do a full hdd install on another computer. 

I don't have the money for Vmware....

Would qemu work? It's interface looks confusing.

There may be a workaround for virtualbox, google it. I will try to do so too.

---

### Post by kk0sse54 on 2009-03-31
[Vmware Server]("http://vmware.com/products/server/"), it's what I use for any BSD virtualization and it doesn't even cost a nickel :). I believe Qemu should also work and KVM might too but I've never tried it.

---

### Post by aeiah on 2009-03-31
it works with xen

[http://www.netbsd.org/ports/xen/](http://www.netbsd.org/ports/xen/)

i think you can use kvm with xen (since kvm is just the manager). i havent much experience with xen because it's not very good for windows server 2008, which is a shame. it was fun having two machines with an ubuntu virtual machine kinda floating between the two. i could unplug either of the machines and the vm would just keep on pinging back and running as normal as if nothing had happened thanks to live migration and failover

---

### Post by Sporkman on 2009-03-31
VMWare Server is free & easy to use.

---

