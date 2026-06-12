---
title: "Openvpn won't work on a new network."
date: 2010-01-05
forum: Security
---

### Post by zozza on 2010-01-05
A couple of weeks ago I was using openvpn with a provider of PVNs on a home wifi network with no problems.

I had installed openvpn using apt-get install and downloaded the .opvn PVN files from the organization.  Everything worked fine.

I would type sudo openvpn nameoffile.ovpn and then add my username and password during the installation process.  

However, when I try to do the same on an Ethernet network, the installation work fines (as above) and informs me that everything is connected (same as on the home Wifi network) but Firefox and all other software cannot connect to anything on the Internet.  

I contacted the organization who said the DNS was a problem and I needed to install resolvconf then modify each .opvn file using up /etc/openvpn/update-resolv-conf and down /etc/openvpn/update-resolv-conf

However, this causes the installation to hang because it does not like openvpn pointing to an external file.

Irrespective of the problem I have with this "solution", previously I could use openvpn without modifying the .ovpn files.  It just worked! I wonder if anyone knows why using the exact same configuration on an Ethernet network (which I have not used before with openvpn) is causing problems?

Thanks.

---

### Post by cariboo on 2010-01-05
It does sound like a DNS problem, what does your /etc/resolv.conf file look like? If it is using you routers ip address for DNS, then you definitely have a problem.

---

### Post by zozza on 2010-01-06
/etc/resolv.conf shows my current network's DNS nameservers.

I checked this in XP using ipconfig /all and they are the same (is there a way of using a command in Ubuntu to confirm /etc/resolv.conf is correct?)

---

### Post by zozza on 2010-01-06
Ok, I think I understand better now.

You are saying that if my /etc/resolv.conf file shows my DNS settings for the Ethernet, the problem is that openvpn needs to use the organization's DNS.

This is why they suggested I add up /etc/openvpn/update-resolv-conf and down /etc/openvpn/update-resolv-conf to the .ovpn files because update-resolv-conf is designed to modify /etc/resolv.conf (AIUI) with the organization's DNS settings.

I think that makes sense.

However, I don't understand why this was not an issue when I first used this system on my home Wifi network.

Also, here are the error codes from openvpn when using the up /etc/openvpn/update-resolv-conf and down /etc/openvpn/update-resolv-conf settings.

openvpn_execve: external program may not be called unless '--script-security 2' or higher is enabled.  Use '--script-security 3 system' for backward compatibility with 2.1_rc8 and earlier.  See --help text or man page for detailed info.
Wed Jan  6 10:29:15 2010 script failed: external program fork failed
Wed Jan  6 10:29:15 2010 Exiting

I have played around with this --scrip-security setting but cannot get a configuration that will execute.

Again thanks for your help - do you have any more suggestions?

---

### Post by zozza on 2010-01-08
BUMP!

Sorry for bumping but still cannot get this to work.

---

