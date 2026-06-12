---
title: "Recommend me a bare metal Hypervisor"
date: 2013-11-30
forum: Virtualisation
---

### Post by AADAS on 2013-11-30
I want to use my video card (gtx 660m) and my cpu(i7) for my windows machine.

---

### Post by rackit on 2013-11-30
Kinda high-end, but one of my favorite system manufacturers. [http://www.supermicro.com/products/nfo/Core_i7.cfm](http://www.supermicro.com/products/nfo/Core_i7.cfm) Google foxconn i7 for some less expensive alternatives. Foxconn products have been rock solid in my experience.

---

### Post by rackit on 2013-11-30
Kinda high-end, but one of my favorite system manufacturers. [http://www.supermicro.com/products/nfo/Core_i7.cfm](http://www.supermicro.com/products/nfo/Core_i7.cfm) Google foxconn i7 for some less expensive alternatives. Foxconn products have been rock solid in my experience. Sorry about the double post - one of my kids hit the back button when I was AFK.:oops:

---

### Post by TheFu on 2013-12-19
Is this a hypervisor question?

Nominally, the video card doesn't matter at all for virtual machines - a virtual video card is provided unless you take extra, highly unusual steps to get passthru working that less than 0.00001% of the people using virtualization use.

To my knowledge there is only 1 "bare metal hypervisor" - ESXi. All the others sit on an OS.  ESXi GPU passthru is new enough that it isn't 100% stable. [https://communities.vmware.com/message/2282917](https://communities.vmware.com/message/2282917)

Could you clarify your question please?

---

### Post by dcstar on 2013-12-23
You should be able to use "Passthrough" video with an additional video card with ESXi. It just has to be compatible hardware that ESXi recognises.

---

