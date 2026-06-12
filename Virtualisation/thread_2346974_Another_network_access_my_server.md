---
title: "Another network access my server"
date: 2016-12-20
forum: Virtualisation
---

### Post by gaftzona on 2016-12-20
Hello I am new here and I hope I am writing this in the right place.
I installed a server on a machine in VMware Workstation Pro. I installed it everything I needed everything works fine.
My problem is when I want to enter my address browser from another computer that is on it did not hit me, I was looking for an answer for a few days and I can not find the answer.
Thanks in advance.

---

### Post by howefield on 2016-12-20
Moved to the "*Virtualisation*" forum.

---

### Post by efflandt on 2017-01-12
I am no expert, and am not familiar with VMware. But by default a virtual machine typically does NAT behind the IP of the host computer (masquerades its IP as the IP of the host). So your VM may be able to see or ping the other computer, but the other computer cannot see your VM IP.

Maybe someone else can help you with settings to make your VM server visible to the outside world.

---

### Post by geeksmith on 2017-01-12
Look at the VM network adapter settings in VMware. The virtual NIC must be bridged, not connected to a NAT or internal network.

---

