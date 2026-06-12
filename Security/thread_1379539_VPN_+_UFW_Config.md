---
title: "VPN + UFW Config"
date: 2010-01-12
forum: Security
---

### Post by Patriota on 2010-01-12
Hi Guys,

I am currently connecting to a VPN via OpenVPN/OpenSSL. 

I was interested to know what rules I would need to put in place with UFW to only allow connections in/out via the VPN. For example I use Firefox/Pidgin/Torrent/Skype.

Also, I was interested in a script to connect to the VPN on Startup. 

FYI, I am running Karmic.

Would appreciate any assistance you guys can offer!

---

### Post by bodhi.zazen on 2010-01-13
Since no one has answered, see this tutorial (Spanish)

[http://www.juanpablo.netne.net/index.php/en/manuales-linux/red-privada-virtual-openvpn/item/58](http://www.juanpablo.netne.net/index.php/en/manuales-linux/red-privada-virtual-openvpn/item/58)

It lists iptables rules for OpenVPN. You can either add them directly to UFW by adding them to your /etc/ufw/before.rules or write rules for UFW.

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by Patriota on 2010-01-13
Cheers Bodhi, exactly what I was after! :):):):)

---

