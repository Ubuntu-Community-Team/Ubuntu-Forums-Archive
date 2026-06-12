---
title: "using vbox with ubuntu ltsp"
date: 2009-08-04
forum: Virtualisation
---

### Post by noorez on 2009-08-04
This is the setup that I have:

The first guest I created was for the ubuntu 9.04 guest installed with LTSP server. I configured this with two network cards both connected through NAT.
During installation I specified eth0 as the primary.

The second guest I configured to boot from lan, and also configured the network card to connect through nat.....

however, at this point i'm stuck....what do I do?

---

### Post by jocampo on 2009-08-04
> **noorez said:**
> This is the setup that I have:

The first guest I created was for the ubuntu 9.04 guest installed with LTSP server. I configured this with two network cards both connected through NAT.
During installation I specified eth0 as the primary.

The second guest I configured to boot from lan, and also configured the network card to connect through nat.....

however, at this point i'm stuck....what do I do?

I don't understand what are you trying to do If you are using NAT for your virtualbox, the Ubuntu setup will ask you for the hostname and the DHCP discovery will start and get the IP for you. Where are you stuck at?

---

### Post by noorez on 2009-08-05
Ok....totally my bad...I should have looked at the VirtualBox manual first....

So here is what I changed..on the "server" virtual machine I made the first network card go through NAT and the second be an internal connection. On the "thin-client" virtual machine I also made it an internal connection. This allowed the "thin-client" to connect and boot.

But there are still some problems that I am having:

I installed the edubuntu addon to give it a try and I attempted to use thin client manager but the manager did not detect a connection.

Any ideas on that one?

---

