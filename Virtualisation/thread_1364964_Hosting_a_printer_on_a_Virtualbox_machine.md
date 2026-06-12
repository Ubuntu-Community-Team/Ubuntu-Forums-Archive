---
title: "Hosting a printer on a Virtualbox machine?"
date: 2009-12-26
forum: Virtualisation
---

### Post by Objekt on 2009-12-26
Has anyone found a way to host a printer on a virtual Windows XP machine running under Virtualbox?  I need to do this because no Linux drivers of any kind exist for my printer, a Canon Multipass F60.  It is therefore completely inaccessible when running Kubuntu 9.04, the OS I use most.

The printer plugs in via USB.  I don't know much about accessing USB devices from a Virtualbox guest machine, but I assume that the printer's Windows-only software will not know the difference.

---

### Post by HermanAB on 2009-12-27
Howdy,

If the printer is USB, then you need to get Vbox from their web site.  The free version doesn't do USB.  Apart from that, all you would need to do is set WinXP to a static IP address and share the printer.

---

### Post by Objekt on 2009-12-27
I did most of that, except the last step.  How do I set the virtual machine to a static IP address?

I guess this is the critical step, because the Windows machine on my home network can't yet see the printer connected to the virtual XP machine hosted on my Kubuntu machine.  

The virtual machine does show up in our workgroup - I called it "VirtualXP" to preclude any confusion.  However, there is nothing connected to it, when viewed from the (physical) XP machine, so I can't add the printer.

"VirtualXP" is also visible from my Kubuntu machine (host of the virtual XP machine), in Dolphin as a Samba share.  Again, there are no resources attached to it.

I was hoping I might be able to set up the printer through CUPS, so I could print to it from my host machine as well as from the network XP machine.  No luck with either so far.

UPDATE:

The problem was the default "NAT" option for network access by the virtual machine.  Once I switched it to "Bridged adapter," the printer showed up as a Samba share, and we were able to print to it from another Windows machine on the network.

---

