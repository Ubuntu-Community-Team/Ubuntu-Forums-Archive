---
title: "Multiple ubuntu on desktop with internetworking"
date: 2011-04-07
forum: Virtualisation
---

### Post by Yogesh_P on 2011-04-07
Hi All

I wish to have 3 ubuntu installations on my laptop so that I can try working on applications related to Distributed Systems. I already have Ubuntu10.04 installed on virtual box, how can I install more copies so that I can run all 3 simultaneously and there should be LAN like connectivity among 3 machines. 

Is there any way where I can install 3 separate ubuntu on Virtual box or run 3 copies of Ubuntu from already installed one.

Memory and hard disk size are not a constraint here.

Thanks and Regards
Yogesh

---

### Post by falko on 2011-04-08
If you have a DHCP server in your network (usually on your router), this hsould be no problem as all virtual machines will get different IP addresses so that they don't interfere with each other.

---

### Post by Hedgehog1 on 2011-04-09
> **Yogesh_P said:**
> Hi All

I wish to have 3 ubuntu installations on my laptop so that I can try working on applications related to Distributed Systems. I already have Ubuntu10.04 installed on virtual box, how can I install more copies so that I can run all 3 simultaneously and there should be LAN like connectivity among 3 machines. 

Is there any way where I can install 3 separate ubuntu on Virtual box or run 3 copies of Ubuntu from already installed one.

Memory and hard disk size are not a constraint here.

Thanks and Regards
Yogesh

If you export your current Ubuntu10.04 VM (Menu to: File >> Export Appliance ), you can then import that .osa file two more times and have three systems.  This is faster than repeating the install of 10.04.


***The Hedge***

:KS

---

### Post by Yogesh_P on 2011-04-09
> **Hedgehog1 said:**
> If you export your current Ubuntu10.04 VM (Menu to: File >> Export Appliance ), you can then import that .osa file two more times and have three systems.  This is faster than repeating the install of 10.04.


***The Hedge***

:KS

Thanks , that looks an easier option. But how can I connect them like a LAN so that if I run 1 program it can access other machines too. I tried internal networking adapter and NAT adapter in virtualbox but each machines gets assigned same IP address so there is no way to tell which machine to access.

Regards

---

### Post by Hedgehog1 on 2011-04-09
There are 3 options for your network adapter in the virtual machine setup.  If you have DCHP from your router (or another DHCP server), two of them (and am away from my system with VBox, so I cannot recall the exact names of them) will end up with every virtual machine with it's own IP address.


***The Hedge***

:KS

---

