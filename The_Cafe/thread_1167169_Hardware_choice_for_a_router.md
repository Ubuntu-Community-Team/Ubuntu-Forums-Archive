---
title: "Hardware choice for a router"
date: 2009-05-22
forum: The Cafe
---

### Post by and.hunt on 2009-05-22
I'm planning on building myself a router (by which I actually mean modem + router + wireless router etc.) at home from scratch, partly for fun, partly to have a flexible home router, which also serves the home phone network. The problem is hardware choice: I have seen various low power boards around, but don't really know what is needed for this sort of project. I also do have some rather diverse requirements which complicate matters, since what I really need/want is:
[LIST]
[*]Modem which can connect to ADSL using PPPoA. (Essentially the European version of PPPoE.)
[*] Possibly, depending on the country I am in, I might need a DOCSIS compliant cable modem instead of the above.
[*] 4-8 Ethernet ports which can be used to directly connect other computers into network.
[*] Wireless card for 802.11g, which can run in master mode (AP mode) for serving a wireless network.
[*] A FXS phone serving card which can be used with Asterisk, for connecting a standard wired phone in. (But alternatively this could be done using an ATA to convert Ethernet into analogue, or I could just get an IP phone some time in the future.)
[*] A FXO card to pick up my normal landline telephone. (You can usually get a combined FXO/FXS card.)
[/LIST]
Essentially what is needed is a mainboard with 3 pci sockets, or alternatively with 4 built in ethernet ports and 2 pci sockets.
The software I need to run isn't too complicated, it would be:
[LIST]
[*]DHCP server
[*]Firewall (but this is built into kernel anyway).
[*]Asterisk (but only handling maximally one call at a time, with connection to landline and also VOIP).
[*]Possibly a light http server (for internal network use only).
[/LIST]
Can anyone recommend hardware for this setup, e.g. at least the motherboard/cpu setup that is recommended. It has to be low power, so no standard desktop equipment.

//Edit: I completely forgot to mention that I might also want to build in a print server, using CUPS, for a printer connected via USB. It would actually be good to have a setup where a relay is connected to the print server, which controls the power to the printer, so whenever no one is printing the printer is left off, but when someone sends a print job, the printer is switched on before printing commences.

---

