---
title: "vmware connected to internet via wireless connection"
date: 2008-05-09
forum: Virtualisation
---

### Post by dzorzoli on 2008-05-09
Hi,

I've a win xp pro notebook with vmware workstation 6.0.

One virtual o.s. is a windows 2003 enterprise server (with some business application).

I need to connect the virtual machine directly to internet via a wireless router (USR 9111).

Is it possible?

Regards
DZ

---

### Post by Kokopelli on 2008-05-09
Yes it is possible, simply create a bridged interface in your workstation config that uses your wireless card.  Then add a virtual interface that uses it to your virtual machine.

---

### Post by agibby5 on 2008-05-11
I just went through doing this by running vmware-config.pl.  However, I'd like to know what adaptor was setup... eth0 was setup on /dev/vmnet0... I know I could (and probably will) run the config again and note the adaptor. However, I wanted to also view some other settings that were setup (and for future reference....  How could I view the config settings for vmware?

---

