---
title: "KVM - Windows server VM freezing large data transfers"
date: 2020-05-15
forum: Server Platforms
---

### Post by michaelneh on 2020-05-15
Hi I am running Ha servers Utilizing KVM/DRBD on server  18.04.4 LTS and I have a VM running windows server 2019 and It appears to Freeze randomly when copying large amounts of data the network connection will go down and I will have to force to VM to shut down and re-start. Runs fine otherwise Any ideas. ?

---

### Post by volkswagner on 2020-05-15
Which driver are you using for NIC?

---

### Post by TheFu on 2020-05-15
Some info about the HW, VM settings and network architecture would be helpful.  For example, are there multiple subnets connected to the VM so DRBD traffic doesn't saturate a nic?  Have you reduced the packet sizes and net buffers?

---

