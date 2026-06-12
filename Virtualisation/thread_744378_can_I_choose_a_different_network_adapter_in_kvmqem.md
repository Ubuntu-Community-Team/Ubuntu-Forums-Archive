---
title: "can I choose a different network adapter in kvm/qemu"
date: 2008-04-03
forum: Virtualisation
---

### Post by gstt on 2008-04-03
I installed kvm/qemu successfully in my ubuntu Fiesty. The default network adapter is Realtek RTL8028 with 10M speed. Can I choose another network adapter with 100M or higher speed? 

I tried the cmd :
kvm -net nic,model=?

But this only showed the general help message.

---

### Post by msisamonopoly on 2008-04-05
try model=pcnet

---

### Post by gstt on 2008-04-07
> **msisamonopoly said:**
> try model=pcnet

Thank you. This gives me a new adapter: AMD PCNET Family PCI Ehternet Adapter. It comes with 100M duplex mode. 

However, after I chose "100Mbps full Duplex" from "External PHY", I still got 10M bps speed in the network connection dialog box. Restarting machine did not change anything.

Here is the full command I start kvm:

 sudo kvm -no-acpi -m 512 -cdrom /dev/cdrom  -net nic,model=pcnet -net tap   mykvm.img

I went through the help message and tried to google qemu documents but still could not find how to set the network link speed to 100Mbps.

---

### Post by problematique on 2008-04-08
I'm having the same issue but with a different network adapter. I suppose 10M will have to do.

---

### Post by jserink on 2008-07-19
Here is my startkvm100.sh script:
kvm -boot c -hda /home/jserink/winxp1.img -m 384 -net nic,vlan=0,model=rtl8139 -net user -localtime &
/home/jserink/qgt-2005-03-02-19/host-linux 127.0.0.1 > /dev/null 2>&1 &

Everything you need to know is in there. I'm getting ~25Mbps throughput which is much better than the 2-4Mbps you get with the 10M NIC.

Looking for a 1000MNIc support to clean this up even further if anyone has suggestions.

Cheers,
John

---

### Post by Milan Knizek on 2009-01-04
> **gstt said:**
> 
I tried the cmd :
kvm -net nic,model=?

But this only showed the general help message.

You need to supply also the image name (also named "target" in the man page):
kvm -net nic,model=\? ubuntu.img

---

