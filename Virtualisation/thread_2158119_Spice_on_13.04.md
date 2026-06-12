---
title: "Spice on 13.04"
date: 2013-06-27
forum: Virtualisation
---

### Post by pnunn on 2013-06-27
Hi Guys,

I'm yet another one trying to get Spice working on KVM without any success. I've found a few threads on here (and about) talking about how it should work, but not too many saying they have it working.

I'm getting the "cannot find module spice client gtk" when I open the machine in virt-manager. I've dumped the xml and its using the correct hypervisor, but still not finding the display module it seems.

To keep it simple I'm trying to open a Ubuntu 13.04 client running on a Ubuntu 13.04 host. The machine I'm running virt-manager on is also 13.04. Both the host and virt-manager machine have the spice-client-gtk package installed.. why would it not be found? This seems to be totally broken on Ubuntu as far as I can see.

Is anyone working on it?

Ta

Peter.

---

