---
title: "Cisco anyconnect on Pop OS"
date: 2022-08-08
forum: Ubuntu/Debian BASED
---

### Post by hardeep2022 on 2022-08-08
Hi All,

Cisco annyconnect vpn seems to drop ever 15 minutes or so. I had a similar issue on Ubuntu and the fix was to run:
[COLOR=#000000][FONT=Arial]
sudo apt-get remove network-manager-config-connectivity-ubuntu[/FONT][/COLOR]

This doesnt apply to Pop OS as this package is not installed. Has anyone come across this problem and what is the fix?

thanks
Hardeep

---

### Post by ActionParsnip on 2022-08-08
If you use openvpn client in the terminal, is it better?

---

### Post by hardeep2022 on 2022-08-09
Hi there, i wasnt able to figure out how to configure access using  anyconnect, i tried the GUI version under Network, i do have a gateway  address, username and password but it seems i need a CA certificate to  finish the setup which isnt something i have. Is there a way to connect  via anyconnect without the certificate?

---

### Post by ActionParsnip on 2022-08-09
You'll need the certificate otherwise you won't trust the certificates given by the end point. It completes the chain

---

### Post by hardeep2022 on 2022-08-12
Thanks for that, i do connect to various VPNs via Cisco Anyconnect and i wont always have the certificate, i'm only given username and password. I'm sure there's some vpn or network related program or config which is causing anyconnect to drop. Would be interested to know if anyone has come across that and what they've done to get around it. On Ubuntu it was just a simple case of removing the package mentioned and no more vpn drops.

---

### Post by hardeep2022 on 2022-08-12
In case it is Network manager related this is what i have installed, not sure which one i could get away uninstalling to see if it helps:

apt list --installed | grep network-manager

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

network-manager-config-connectivity-pop/jammy,jammy,now 1~1526005491~22.04~fd4f44d all [installed,automatic]
network-manager-gnome/jammy,now 1.24.0-1ubuntu3 amd64 [installed,automatic]
network-manager-openvpn-gnome/jammy,now 1.8.18-1 amd64 [installed,automatic]
network-manager-openvpn/jammy,now 1.8.18-1 amd64 [installed,automatic]
network-manager-pptp-gnome/jammy,now 1.2.10-1 amd64 [installed,automatic]
network-manager-pptp/jammy,now 1.2.10-1 amd64 [installed,automatic]
network-manager/jammy-updates,now 1.36.6-0ubuntu2 amd64 [installed,automatic]

---

### Post by hardeep2022 on 2022-08-13
This seems to have done the trick

[COLOR=#000000][FONT=Arial]sudo apt-get remove network-manager-config-connectivity-pop[/FONT][/COLOR]

---

