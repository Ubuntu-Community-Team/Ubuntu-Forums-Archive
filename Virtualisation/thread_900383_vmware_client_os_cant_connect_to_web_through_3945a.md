---
title: "vmware client os cant connect to web through 3945abg wireless card"
date: 2008-08-25
forum: Virtualisation
---

### Post by bzimage on 2008-08-25
hi,
  I have a new thinkpad X61, and installed ubuntu804 as host, its network ok, then I get vmware and install a winxp as a client os, it use bridged mode of network connection, but it doesnt work. is there any hints about this.

thanks a lot.

---

### Post by fjgaude on 2008-08-25
In VMware set the network to NAT for the Windows VM... that will likely work.

---

### Post by bzimage on 2008-08-26
> **fjgaude said:**
> In VMware set the network to NAT for the Windows VM... that will likely work.

that works, thanks a lot, 
but would you please tell me why the bridged mode cant work?

---

### Post by fjgaude on 2008-08-26
I don't normally use bridged but I'm sure it has to do with not setting the IP addresses correctly so that your router, or what have you, can correctly connect to the Internet. Notice there are several ports working with vmware for multiple addresses.

I think the vmware manual tells all.

---

