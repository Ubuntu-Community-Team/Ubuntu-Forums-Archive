---
title: "ubuntu ltsp on virtual box"
date: 2010-08-04
forum: Virtualisation
---

### Post by noorez on 2010-08-04
Hi

I am attempting to test ubuntu 10.04 ltsp installation in VirtualBox however it doesn't seem to be working. 

For the server machine, I created two network interfaces. The first one is bridged to my en1 (wireless interface) and the second is bridged to en0 (ethernet). During the installation, I selected en1 as the primary interface. The installation finished successfully.

I then created a second virtual machine to book from the network and its interface card was also bridged to en0. However, I am receiving an error message that it could not find a PXE file, however, it does seem to correctly locate the DHCP server and receive an IP address.

any ideas on how to fix this?

---

### Post by noorez on 2010-08-04
This is the message that I am getting on the thin-client:

PXE-T01: File not found
PXE-E3B: TFTP Error - File not found
PXE-M0F: Exiting Intel PXE ROM

Have I not configured my network interfaces correctly on virtual box?

---

