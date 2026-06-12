---
title: "Printing with an HP K8600dn"
date: 2012-08-14
forum: Ubuntu Studio
---

### Post by jesushero on 2012-08-14
Does anyone have any experience with the HP K8600dn? I can make it work with USB, but I can't figure out the IP side of things. It is defaulted to work with DHCP, and I don't use DHCP on my LAN. Everything is set to work with Static IP. Can I set this printer to work with static IP on ubuntu?

---

### Post by gordintoronto on 2012-08-14
According to the manual for that printer, it has a built-in web server for configuration. You should be able to connect to it by entering the IP address into your browser's address bar.

To find out the IP address, open your file manager, and click on "browse network." The result should be a list of the names of all the devices on your network. To translate the name into an IP address, use this command: nmblookup [name of device]

There might be a configuration option to set the printer to a static IP address.

---

### Post by jesushero on 2012-08-15
Thanks for your reply. Indeed, there was a very nice admin page on the printer's IP, from where I can set a static IP. So problem solved. The only sort of tricky part is that the default setting for the printer is DHCP. So to actually be able to see this admin page and set it to Static, I had to set up a DHCP for the printer's MAC address, to assign an IP that would be reachable from the LAN. After doing that, I could set the Static IP and all other settings, and then disable the DHCP again, as the printer will use Static from now on (hopefully)..!

---

