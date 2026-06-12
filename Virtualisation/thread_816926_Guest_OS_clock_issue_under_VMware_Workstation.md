---
title: "Guest OS clock issue under VMware Workstation"
date: 2008-06-03
forum: Virtualisation
---

### Post by svenole on 2008-06-03
I've been running VMware workstation 6 on Ubuntu 7.10 for a year without any problems. My hardware is a Dell Latitude D620. The guest OS is Windows XP. After I upgraded my Ubuntu to 8.04 and got VMware workstation up on this new OS release, I've got into problems with clock sync in the Windows XP guest OS. I've searched the network and made the corrections suggested there (put in some lines in the /etc/vmware/config file, host.cpukHz = "2000000", host.noTSC = "TRUE", ptsc.noTSC = "TRUE"), but I am not able to get the time right in Windows XP. The clock is synced when the guest OS starts, but it speeds away at once and goes about 1.5 faster than it should. Again, this happened when I upgraded to Ubuntu 8.04. Is there any solution to this problem out there?

---

### Post by bmwman on 2008-06-03
I had similar problem. I use Vmware workstation 6.03. It was working fine for a while then one day it just decided to speed up. I reinstalled VMware tools and rebooted few times the whole system. The issue dissappered same as it came on - byt itself. Everything works fine now. Weird.

---

### Post by svenole on 2008-06-03
Ahh.. Thanks. I will certainly   try that and add the result to this thread.

---

