---
title: "How to VMs in Libvirt connect direct to Internet"
date: 2011-06-01
forum: Ubuntu Cloud and Juju
---

### Post by lemon1707 on 2011-06-01
Hi all, 
I has setup UEC by using Ubuntu 10.04 LTS. The problem is the VMs are running but can not connect from another Laptop on Lan. It seem like Libvirt problem, I mean the VMs run in Libvirt and Libvirt can not connect to outsite. 
Could you give me more solution to solve ? How to VMs in Libvirt connect direct to Internet ?

---

### Post by kim0 on 2011-06-04
Hi,
My understanding is that you'd need to setup iptables masquerading on CC machine for outgoing traffic from the cloud to reach the internet. Also try normal steps of testing pinging ip addresses directly, then testing dns ..etc

---

### Post by lemon1707 on 2011-06-04
> **kim0 said:**
> Hi,
My understanding is that you'd need to setup iptables masquerading on CC machine for outgoing traffic from the cloud to reach the internet. Also try normal steps of testing pinging ip addresses directly, then testing dns ..etc

Hi kim0,
Ubuntu 9.10 used Full Virtualization technology to setup cloud and the Ubuntu 10.04 and later used Paravirtualization technology, is It right ?
I also installed Ubuntu 9.10, Ubuntu 10.04 LTS and Ubuntu 11.04. They are so different. Could you tell me more about the Virtualization inside them ?

---

