---
title: "W: Failed to fetch http?"
date: 2009-06-11
forum: Server Platforms
---

### Post by yldouright on 2009-06-11
I just installed the Ubuntu Jaunty server 9.04 on an Epox 8RDA+. This motherboard has an NF2 chipset with integrated LAN on the MCP-T southbridge. I didn't select an option in the tasksel dialogue because I have another device handling NAT and DNS (Verizon/Westell 327W). I will eventually put samba on it but for now, I just want a working desktop. I used```
sudo apt-get install ubuntu-desktop
```to get the desktop files but that was when I received the download error. Unfortunately, it looks like the names are not resolving on the server or the connection is failing for some other reason. Can someone help me shoot this down?

---

### Post by zharmad on 2009-06-11
Have you updated apt-get yet? Try sudo apt-get update

---

### Post by yldouright on 2009-06-11
I have and the same error comes back. When I look at the router, the physical connection is fine but the router doesn't see the server. It should be getting the DHCP address from the router like all the other nodes. The /etc/network/interfaces is correctly filled for DHCP assignment of an IP. I'm stumped, the only thing that makes me wonder is if the server requires a complete MAC address to install the IP network. This board does not show the complete MAC in the bios, you need to input it. Is there a way to get the MAC from the command line?

---

### Post by zharmad on 2009-06-11
ifconfig will show the hardware address of the network adapter.

---

### Post by yldouright on 2009-06-26
zharmad
Noted. Putting the MAC address in the bios and reconfiguring the router took care of the problems. Everything on that box is up. Thanks.

---

