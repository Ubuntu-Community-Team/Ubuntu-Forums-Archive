---
title: "Printing from a VBox OSE virtual machine- network printing?"
date: 2011-03-31
forum: Virtualisation
---

### Post by varelov on 2011-03-31
I am using Ubuntu 10.10 and VirtualBox OSE, and running an Ubuntu Server virtual machine from which I have to print few conf files.
On my Ubuntu desktop I have attached a USB printer that is shared for the network. The network mode for the virtual machine is Bridged and I can ping both ways successfully, so network connection between physical and virtual machine is working. VirtualBox OSE however doesn't give me the option to connect virtual machines to USB devices so I chose to make my USB printer shared on the network.
On the virtual installation of Ubuntu Server I have install minimal GUI desktop via apt-get install gnome-core xauth xorg so I have graphical access not just CLI. Thinking that the very printing itself is not enabled on Ubuntu Server I have also installed CUPS. Still, I don't have the option to print to network printer, the only option offered is print to file.
What else should I do to enable the virtual install of Ubuntu Server use the USB printer attached to the host?

---

### Post by varelov on 2011-04-01
OK, solved. Or at least in my case. All it took was changing a line in /etc/cups/cupsd.conf, at the section about "Show shared printers on the local network", I turned browsing to On (default is Off), restarted cups ( sudo /etc/init.d/cups restart) and voila! The network printer was there, printed a random page and verified it was working.

---

