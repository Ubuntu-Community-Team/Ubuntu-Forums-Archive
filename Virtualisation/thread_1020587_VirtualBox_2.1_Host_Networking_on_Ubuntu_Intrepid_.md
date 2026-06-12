---
title: "VirtualBox 2.1 Host Networking on Ubuntu Intrepid 8.10"
date: 2008-12-24
forum: Virtualisation
---

### Post by noahsatellite on 2008-12-24
I'm running Ubuntu Intrepid 8.10 x64 with a Vista Business guest on VirtualBox 2.10.  I read that the Host networking in VB 2.1 is supposed to be amazing and work just out of the box, but that's not been my experience.  NAT works just fine but I can't get Host networking to work.  Vista doesn't see any network whether I use DHCP or a static IP.

I appreciate any help you can give.

Thanks,
Noah

---

### Post by bodhi.zazen on 2008-12-24
You can try a different interface. Under networking you have several options for the type of network card that is emulated. the vituralbox documentation reviews the options.

If that fails, I suggest you manually make a bridge (there are instructions on the mega thread) and add a tap for your guest.

---

### Post by b0b138 on 2008-12-24
Its worked fine for me. (with xp guest anyways) When you say it doesnt see any network, do mean your ubuntu host, or a network adapter? Did you install guest additions?

---

### Post by inobe on 2008-12-24
sounds like a network privilege problem with vista.

you will need to go threw the network setup docs for vista' unless of course your not trying to enable shares.

unlike xp, vista's security has much improved via shares.

---

### Post by Voland on 2008-12-25
I have another interesting problem. I can ping my local network, resolve internals and external names, but i can not ping external computers. WTF?

---

