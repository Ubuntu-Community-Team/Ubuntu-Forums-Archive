---
title: "building a virtualization box for my lab"
date: 2010-02-21
forum: Virtualisation
---

### Post by naelq on 2010-02-21
hi,
i'm in the process of upgrading my lab for a 'better' testing/learning experience of networks/servers management & hopefully virtualization..

i've been investigating this field a while now, & gathered some good info regarding virtualization in general but only a few regarding linux based virtualization, read KVM. which led me to one of the following conclusions: (or even both!)
1. KVM is not mature enough & not ready yet for production
2. or my *googling* skills could be improved!

so, here i am, posting @ the Ubuntu forums seeking for some answers :)

hardware-wise i'll be basing my build on the following parts:
CPU: Intel Core i7 860
MoBo: Intel DQ57TM
RAM: 4x 2GB DDR3 1333MHz
HDD: 2x WD 640GB Black

the cpu is a quad core with 8 threads featuring both VT-x & VT-d. the mobo is based on the Q57 chipset with an Intel 1GbE & 2 pci-e x1 available slots for extra 1GbE/RAID controller (if needed!)
8gb of ram is the max i can get (with reasonable price!) as long as the 4GB modules don't get cheaper. & the disks will be @ RAID1 for the system & VM's. extra storage/backups will be on my NAS box..

given that i'm willing to use **KVM**, the questions are:
1. how powerful would the above hardware be? i mean should it be capable of running both a x2 linux, x1 W2k3 or W2k8 server, x2 windows 7 VM's?
2. as far as virtual-networking, is good enough for testing "micro-production-scenarios" which involves the use of bridged mode networking..
3. management, is it comfortable when talking about multiple concurrent VM's?


as a side note, i'm aware of the existence of the Proxmox VE, which seems very promising though i would like to use my own distro/configurations.


thanks,
nael

---

### Post by pirateghost on 2010-02-21
why dont you run a full blown XEN or ESXi server?  they are both free, and technically they are both linux based.

i found that esxi worked the best for my setups.

---

### Post by naelq on 2010-02-22
& KVM didn't work for you? how hard did you try? when was it? what kind of problems? what hardware do you have? what is your typical usage?...

thank you for the effort pirateghost, but unfortunately you did **NOT** answer any of my questions..

---

### Post by Jeff Anthony on 2010-02-23
You might be able to check out some small server VMs already on the hardware you already have. Most computers built within the past 2-3 years are capable of some form of virtualization. You don't need the latest greatest unless you're running vSphere or something. Try installing VirtualBox via Ubuntu Software Center and mounting some server images from Turnkey. For something a bit more heavy-duty check out Proxmox, which I hope will have an Ubuntu aptitude install eventually.

---

