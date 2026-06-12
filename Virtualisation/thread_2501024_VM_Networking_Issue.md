---
title: "VM Networking Issue"
date: 2024-09-19
forum: Virtualisation
---

### Post by spamsurgeon on 2024-09-19
I have an Ubuntu guest running on a Proxmox host. After a recent update, it can no longer reach the local network. It gets an address and route via dhcp, but then is unable to ping the gateway. When pinging the hypervisor's address, it drops a large percentage of packets.

Everything was working well on the system until a reboot, so I suspect it was an automated update that has caused the issue. 

Any ideas?

---

### Post by wildmanne39 on 2024-09-19
Moved to virtualization for a better fit.

---

