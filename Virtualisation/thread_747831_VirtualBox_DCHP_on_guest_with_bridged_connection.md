---
title: "VirtualBox DCHP on guest with bridged connection"
date: 2008-04-06
forum: Virtualisation
---

### Post by Amorget on 2008-04-06
Is it possible?  I found this in the Wiki:

"Unfortunately, at the time of writing I don't think DHCP auto configuration will work in the VM, so make sure you set a static IP in the virtual machine."

Is that still true?  If it is true, are there any that can use DHCP on the guest and still be about to use a VPN connection, etc?

---

### Post by karyonix on 2008-04-07
It works with ethernet LAN. 
I use DHCP for my virtual machine.  The host machine's eth0 is connected to LAN.  The host machine's eth0 and vbox1 interfaces were attached to br0.  My virtual machine was set to use host interface vbox1.  It can get an IP address & other options from DHCP server on another computer on host's LAN.  

If you use wireless network, bridging may not work with some card or some access point. I have not tried.

---

### Post by Amorget on 2008-04-07
Do you have a tutorial for setting it up that way?  I am using wireless, though..

---

### Post by Amorget on 2008-04-09
Anyone?  I really want this to work.. I don't even what to think of using Vista as my primary OS :(

---

### Post by karyonix on 2008-04-09
My settings for bridging LAN with VirtualBox Host Interface. ==> 
[http://ubuntuforums.org/showpost.php?p=4656505](http://ubuntuforums.org/showpost.php?p=4656505)

However, I don't use wireless network on my computer, so I cannot help you about it.

---

