---
title: "What might be the best basis for software VM?"
date: 2008-10-15
forum: Virtualisation
---

### Post by berkbw on 2008-10-15
YES! - I DO like ubuntu!  But is it the best base upon which to run VM'd OSs?  In general, ubuntu is speedy enough, as an OS, but I am wondering if it would be better to run it, and other OSs, over a different base..... Or if it were the best [or one of the best] bases in itself.

I'm thinking of VMing a few OSs..M$ only because they keep coming up with codec req'd stuff, needed by company email :(

I'm looking for whatever quickly covers the lowest levels of function, completely, to build upon.

As an aside, how does one not automatically upgrade kernel?

thx -

b-

---

### Post by ilrudie on 2008-10-15
A side note for you. Running Vista in a VM is illegal unless you buy a commercial version of Vista Ultimate (maybe on of the business ones is ok too) and it's illegal to run Windows Media Player in a VM regardless of version.  I'm not sure if this has changed recently but this was the case when Vista was released.  I would definitely look into it.  

As for which base to use that would depend.  Your request for a very low level hypervisor (kernel upon which one or more VMs can be run) would lead me to suggest looking into the vmware hypervisor (which I believe is free) however I'm not sure how easy it is to get a cosole session on that.  Those tools are generally what you have to pay for I think.  Xen is a very good choice as well and you can look into software called kvm to get console access on xen domained servers.  I think xen may require a paravirtualized kernel so I'm not sure if windows will run in a xen dom0.

That said if you just want to run Ubuntu with virtualbox, qemu or vmware's free solution (don't remember what its called for linux) you can skip all the hassles of bare metal / low level hypervisors and still get reasonable performance for many things.  

I'd recommend doing a little research to determine which way you want to go and then maybe post back here with more specific questions.

---

