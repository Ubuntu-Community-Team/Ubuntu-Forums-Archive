---
title: "can you connect your vm to the internet via another network"
date: 2007-12-05
forum: Virtualisation
---

### Post by n1ght28 on 2007-12-05
a quick question can you connect your vm to the internet via another network thus having two internet connections at the same time,

---

### Post by gtdaqua on 2007-12-05
you can. for e.g if u have two interfaces on linux e1 and e2. e1 connects to internet via subnet1. e2 connects via subnet2. u have to configure ur vm (vmware) to assign e2 as NIC for in the guest OS. assign subnet2 ip for nic in the guest os - u should be able to connect to internet via subnet2. if u want to use subnet1, map the linux's e1 as 2nd nic of the guest os and assign one  subnet1 ip. 

its very simple actually.

---

### Post by n1ght28 on 2007-12-09
exactly how would i go about doing that,

---

