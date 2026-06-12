---
title: "PXE TFTP Boot Server edition + encryption"
date: 2011-05-27
forum: Security
---

### Post by anarack on 2011-05-27
Hi - I have posted this in the security section as i believe that the encryption bit is the most relevant...apologies as it covers more ground..

I am trying to setup a secure server which will house email archives and hence is labelled as 'sensitive data'.
In order to make the data secure, encryption is required.

We have Sonicwall TZ210 Firewall which we are using as our main DHCP server and a Apple XServe ( latest Snow Leopard )which is running our emails.
I believe the mac server can host PXE TFTP service OK and that the Sonicwall should be able to pass the bootp client ( Sun V20Z server ) to the mac server to load a boot partition image.

This will also be a headless machine so I am hoping to use VNC to connect into the Sun server to administer it as required.

OK the question is - what would be the best strategy to encrypt the Sun Server's data storage, so that if I reboot it, it would boot over the network and bring up my VNC session?

At the mo, I have it running with a boot partition on it, but in the name of physical security ( if the machine (or the HD's ) were taken ), should I be able to achieve the boot sequence :-

Firewall ( client IP )-> TFTP ( on Mac server - send boot image) -> server boots, loads VNC -> auto mounts encrypted volume ( maybe get encryption pw/key from another network device?)

Sorry if this seems overkill...but its the scenario I have been given.

Any help gratefully received.

Tim

---

