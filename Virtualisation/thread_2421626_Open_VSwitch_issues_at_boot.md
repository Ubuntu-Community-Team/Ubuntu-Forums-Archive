---
title: "Open VSwitch issues at boot"
date: 2019-06-24
forum: Virtualisation
---

### Post by jwbryan on 2019-06-24
I am running Ubuntu 19.04 server with KVM/QEMU and Open vSwitch.  The hosts networking is configured to use networkd for configuration.  The VMs are configured to run on the virtual switch.  After reboot, the host is unable to communicate on the network and the VMs need to be pointed back to the switch.  If I remove the host's network port from the switch, the host gets connectivity again, but the VMs lose connectivity.  If I add the port back, the VMs are connected, but the host loses connection.  

I think the issue may be in how networking is being loaded, but am just not there in terms of how to get it corrected.  Looking for suggestions on what direction to take to get this working right.

---

### Post by houstonbofh on 2019-07-04
How did you configure networking on the host system?

---

