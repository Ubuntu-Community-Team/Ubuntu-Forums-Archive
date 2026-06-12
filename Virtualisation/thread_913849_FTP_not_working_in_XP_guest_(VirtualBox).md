---
title: "FTP not working in XP guest (VirtualBox)"
date: 2008-09-08
forum: Virtualisation
---

### Post by turezky on 2008-09-08
Hello everyone,
I'm running Windows XP as the VirutalBox guest in 8.04.1.
The problem is I cannot use any FTP client in XP (tried loads of clients). I reckon the problem is that 21'st port used for FTP connections is not forwarded by VirtualBox to the guest machine, and all FTP clients fail listing directories when it comes to their part.
Any possible solutions for this problem??? :)
Thanks in advance!

---

### Post by HermanAB on 2008-09-08
Enable FTP in the host OS (Ubuntu Firestarter?) firewall.

Cheers,

Herman

---

### Post by turezky on 2008-09-08
Thanks, Herman...
I tried Firestarter... But, unfortunately, couldn't figure out how precisely to allow VirtualBox process (or whatever it uses to connect to the net) to access 21'st port.
Some kind of short HowTo would be nice in this case ;)

---

