---
title: "JeOS. It is for the host or the guest?"
date: 2009-03-13
forum: Server Platforms
---

### Post by erlguta on 2009-03-13
Hi.
I am in doubt about Ubuntu JeOS edition. It is optimized for one "Guest" server installation, or the "Host" server installation?.
I was trying to install one "JeOS ubuntu server" in one guest (in one physical ubuntu server with vmware-server) and I see that there is an option (in Tasksel) that says "Virtual Machine Host". Must be this option selected to install the host (with vmware-server on the top) or for the guest??
Because it says "Virtual Machine **HOST**"

Thank you.

---

### Post by Brazen on 2009-03-13
Jeos is for virtual machine guests.  That tasksel must be a mistake.

---

### Post by erlguta on 2009-03-13
Thank you.
;)

---

### Post by windependence on 2009-03-15
You should try VMware ESXi. No host OS is necessary. It runs on bare metal and is much faster and uses less resources than VMware server.

-Tim

---

