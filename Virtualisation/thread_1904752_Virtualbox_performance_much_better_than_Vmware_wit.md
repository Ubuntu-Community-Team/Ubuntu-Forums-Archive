---
title: "Virtualbox performance much better than Vmware with same specs"
date: 2012-01-05
forum: Virtualisation
---

### Post by azenz on 2012-01-05
Found this interesting: I got a vmware and a Virtualbox guest Windows XP, both same RAM, both expandable HDDs, run from same host SSD with quad core, vmware got 2 CPUs and Virtualbox only 1 CPU assigned. Guest OS config is almost the same (fresh installs) except the Virtualbox has a Comodo firewall and therefore (theoretically) a speed disadvantage.

Vmware:

Boot 45 sec, shutdown 19 sec


Virtualbox:

Boot 27 sec, shutdown 11 sec


Difference: over 50%!

I find that interesting...

---

### Post by dcstar on 2012-01-06
> **azenz said:**
> Found this interesting: I got a vmware and a Virtualbox guest Windows XP, both same RAM, both expandable HDDs, run from same host SSD with quad core, **vmware got 2 CPUs** and **Virtualbox only 1 CPU** assigned.
.........

Assigning multiple CPUs to a VM can actually slow the VM down because the Host has Priority to all CPU resources and if **both** virtual CPU's are not available to the VM then it waits for both to be available.

Statistically there is far more chance of a single CPU being available if the host is busy so the VM with only one CPU allocated has more opportunity to use that resource than if it had to wait for two CPUs to become available.

In the past I have had VMware VMs run a lot better using a single CPU than more than one.

---

