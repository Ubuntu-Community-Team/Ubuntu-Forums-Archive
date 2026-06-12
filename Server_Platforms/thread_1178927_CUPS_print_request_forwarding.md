---
title: "CUPS print request forwarding?"
date: 2009-06-05
forum: Server Platforms
---

### Post by null-cipher on 2009-06-05
Hi everybody.
The situation I am in, is a VPN between 3 locations.
Site 1 has a server that runs samba, and hosts all the network's files. It also has a Fuji Xerox network printer (mondo sized!).
Site 2 and Site 3 also have similar model network printers.

I have seen that these printers support protocols such as IPP and SMB.
I have also discovered that they can be attached to a host computer if necessary.

The VPN is a client-to-server setup, where each machine has a Certificate. I'd prefer not to change this if I could avoid it. It works, so why fix it. ;)

My problem: I want to set up inter-site printing.
This poses a problem for me, as I am quite certain they wouldn't run OpenVPN.
An idea I had, was perhaps find a way for CUPS/Samba to do "print request forwarding". What I mean is set up a virtual printer on the server, which accepts requests, then passes them onto the actual printer on the VPN.

Please advise me if this is a good plan or not, or whether it would be simpler to expand my VPN.
Thanks.

---

