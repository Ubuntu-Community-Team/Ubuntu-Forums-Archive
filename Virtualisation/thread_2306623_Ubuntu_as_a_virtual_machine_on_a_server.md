---
title: "Ubuntu as a virtual machine on a server"
date: 2015-12-17
forum: Virtualisation
---

### Post by rafael38 on 2015-12-17
Hello,

we want to install three virtual Ubuntu machines on one server. Which operating system should we take as basis?

We think of Windows Server 2012. Any experience?

---

### Post by howefield on 2015-12-17
Thread moved to the "*Virtualisation*" forum.

> Write your posts in English unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries, and English is the common language of these forums.

---

### Post by Habitual on 2015-12-17
Define "Ubuntu machines".
What is their intended purpose or role?

---

### Post by rafael38 on 2015-12-21
Well we want to run three php applications. Currently one of them runs on an Ubuntu Server. But we want all three to run on one physical machine. We need to seperate them though. So we thought of using virutlabox (or something similar) with three Ubuntu boxes in order to run them together on one machine but independently from each other.

---

### Post by SeijiSensei on 2015-12-21
You can certainly do this with VirtualBox using Windows or Linux as the host OS.  Choose "bridged" networking instead of "NAT" so the virtual machines will have IP addresses directly on your network.

I have single machines with one instance of Apache running multiple PHP applications all the time.  Is there some reason why you think it important to have separate VMs?

---

### Post by rafael38 on 2015-12-21
Thnx for your reply. Well all three software applications need to be accessed via different ip addresses. That is why we use three virtual machines.

---

### Post by SeijiSensei on 2015-12-21
Not really as it turns out if you're running Linux.  You can create multiple virtual interfaces with different addresses as long as they are in the same IP subnet.  I do that on machines that need SSL, which generally works best with a unique server address.  You define interfaces like eth0:0, eth0:1, ... , eth0:N and assign them each a separate address.  For details see [http://linuxconfig.org/configuring-virtual-network-interfaces-in-linux](http://linuxconfig.org/configuring-virtual-network-interfaces-in-linux).

---

