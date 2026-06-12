---
title: "Ethernet nor correctly detected ?"
date: 2008-12-19
forum: Server Platforms
---

### Post by taget on 2008-12-19
I have ubuntu server set up on a computer that i am setting up to be my router. i added another nic before installing. ran through the entire install and everything seemed fine. when i ran ifconfig it listed eth0 as the second nic and nothing for the onboard nic, when it did finally come up it was listed as eth1 and i cant get it to obtain an address or take it up or down. it was my understanding that the first logical device would be eth0 and the second pci ethernet card would be eth1.  

lspci shows that the onboard nic comes before the pci nic.

also when ifconfig runs it posts eth1 and eth1:avahi with a automatic private address like windows would do if no dhcp server was present.

how can i fix this?

---

### Post by albinootje on 2008-12-19
> **taget said:**
> I have ubuntu server set up on a computer that i am setting up to be my router. i added another nic before installing. ran through the entire install and everything seemed fine. when i ran ifconfig it listed eth0 as the second nic and nothing for the onboard nic, when it did finally come up it was listed as eth1 and i cant get it to obtain an address or take it up or down. it was my understanding that the first logical device would be eth0 and the second pci ethernet card would be eth1.  

lspci shows that the onboard nic comes before the pci nic.

also when ifconfig runs it posts eth1 and eth1:avahi with a automatic private address like windows would do if no dhcp server was present.

how can i fix this?
Since a while Ubuntu (and Debian) use a different system to appoint those network interface names.
I've seen machines where i would put in a second NIC and it would be eth5 or eth4 (!!).
(Somewhere in /etc/ this is defined.)

Did you try getting an ip on both NICs ?
(You can ignore the eth1:avahi).

---

### Post by taget on 2008-12-19
well i got eth1 to get an ip address,"grr, typo on the CLI" but it dosent seem to start at boot, if i add it to /etc/network/interfaces as auto would that bring it up at boot ?

---

### Post by cariboo on 2008-12-19
The short answer is yes. When you run:

```
sudo lshw -C network
```

do both nics show up, and are they both enabled?

Jim

---

### Post by albinootje on 2008-12-19
> **taget said:**
> well i got eth1 to get an ip address,"grr, typo on the CLI" but it dosent seem to start at boot, if i add it to /etc/network/interfaces as auto would that bring it up at boot ?

Yes, it should.

---

### Post by taget on 2008-12-19
> **cariboo907 said:**
> The short answer is yes. When you run:

```
sudo lshw -C network
```

do both nics show up, and are they both enabled?

Jim

Yes both nics do show up.

---

### Post by MJN on 2008-12-20
> **taget said:**
> it was my understanding that the first logical device would be eth0 and the second pci ethernet card would be eth1.No, the only way to fix the 'order' of network adapters is to use /etc/iftab to map each device (usually identified by its MAC address) to the desired label.

Mathew

---

