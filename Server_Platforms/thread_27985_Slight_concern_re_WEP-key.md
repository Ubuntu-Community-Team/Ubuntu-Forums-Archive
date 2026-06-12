---
title: "Slight concern re WEP-key"
date: 2005-04-18
forum: Server Platforms
---

### Post by adder1972 on 2005-04-18
I have a slight concern regarding my WLAN WEP-key.  In my /etc/network/interfaces, the WEP-key for my WLAN is stored:

# The primary network interface
iface eth0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid Aksel
	wireless_key2 73746F3274526C45774F55364F

Is it any way to store the WEP-key encrypted - not in plain text as the example above?

Kind regs,

S

---

### Post by jdong on 2005-04-19
No; you may not store it encrypted. However, you can chmod it to 600 (chmod 600 FILENAME), which only gives root permission to read it.


WEP keys aren't secure at all anyway, so I wouldn't rely on them to do anything but deter the dumbest of script kiddies.

---

### Post by adder1972 on 2005-04-19
Obviously, I have also disabled SSID-broadcast, and created a positive MAC-filter (client list), to limit access to my WLAN.  

Is there another way (than WEP) that you would prefer?

Kind regards,

S

---

### Post by jdong on 2005-04-19
Disabling SSID broadcast does nothing to help security (capturing one wireless packet would reveal the AP MAC).

A whitelist will prevent unauthorized users **to a degree**, until people start spoofing MAC's.


Systems in your LAN should be either firewalled or tightened down (no unprotected services running). To determine if your level of security is adequate, imagine that they're all on the internet with a public IP. Obviously, you wouldn't want a Samba printer share without a password (unless you like to start freeprinting.com), and you wouldn't want to offer your home directories without a password.

Sensitive information should be sent securely, via SSL (https) or SSH.

---

