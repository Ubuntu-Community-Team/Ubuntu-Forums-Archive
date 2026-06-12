---
title: "Get kvm Virtual Guest To Use Router DHCP Service"
date: 2009-09-30
forum: Virtualisation
---

### Post by jakekatz on 2009-09-30
I would like my kvm virtual guests to use my routers DHCP server, this way, all hosts on my network will be able to communicate using just the host name of the virtual machine.

I've searched for two days, and have come across a few posts, but none of them helped me.

  [FONT=Courier New]Host OS: Ubuntu 8.04.3 64bit LTS Desktop Edition
Guest OS: Ubuntu 8.04.3 64bit LTS Server Edition[/FONT]

My virtual guest is assigned a MAC address that **appears **to be constant across boots, so..., I should be able to plug this (fake) MAC addr. into my real router, and get my router DHCP to assign any IP I wish or a dynamic IP from a range to that virtual machine.  

Once booted (like my real hosts) I'll be able to ping the virtual guest using just the host name.  And issuing my guest OS the same IP every time  also means I can use port forwarding on my router for the virtual guest OS -- That's what I want...!

In the host OS, I notice that the IP address of the virtual machine is handed out by libvirt program somehow (192.168.1.123 and up)  

Right now, once the guest is booted, only the HOST OS can ping using the host name of the virtual guest, all other hosts on my network know nothing about this host.  I'd rather not use the IP 192.168.122.1 as my name server on all my other boxes on my network, my Router does that for me now.

I would like to be able to boot my kvm virtual machine and have my router assign its IP addresses based on its (fake) MAC address.

Is this possible?

If this is not possible, how then can I assign a static IP to my Guest OS?  Is it by just using the guests OS /etc/network/interfaces file?

Tks.

---

### Post by Littleweseth on 2009-10-01
Just remember that as far as the virtual machines are concerned, they're real computers. How would you set up a real computer to do the thing you want?

- L.

---

### Post by jakekatz on 2009-10-01
> **Littleweseth said:**
> Just remember that as far as the virtual machines are concerned, they're real computers. How would you set up a real computer to do the thing you want?

- L.

Oh the irony of that statement, I just wish they'd act like a real computer :(  kvm has a way to go before they can begin to compare to a Solaris zone.

---

