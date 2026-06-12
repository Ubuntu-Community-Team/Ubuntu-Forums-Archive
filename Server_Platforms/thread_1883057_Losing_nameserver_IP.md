---
title: "Losing nameserver IP"
date: 2011-11-18
forum: Server Platforms
---

### Post by lightninhopkins on 2011-11-18
After installing ubuntu desktop over 8.04 server, which has been running for a few years without an issue, I lose my nameserver IP after a reboot. 

I have to go back in and set my nameserver each time. 

Anyone else with this issue?

---

### Post by Wayne_V on 2011-11-18
did you change your IP config from static to dhcp?   if it is getting cleared on config it is probably a misconfig with the dhcp server ....

---

### Post by lykwydchykyn on 2011-11-18
Installing the desktop probably also installed network-manager, which obliterates the resolv.conf file whenever it starts up.

There's probably a way to get network-manager to respect static entries, but I usually just remove it instead.

Check if network-manager is installed.

---

### Post by lightninhopkins on 2011-11-18
Thanks for the replies. The IP is static. 

The network-manager was installed, and I removed it. Same behavior. 

Odd.

---

### Post by jonobr on 2011-11-18
Did you do a purge?

sudo apt-get --purge remove network-manager-gnome

How many ethernet interfaces are deinfed?
I ask as [This chap had a similar issue]("http://ubuntuforums.org/showthread.php?t=1882097")

---

### Post by lightninhopkins on 2011-11-18
I'll try to see if the eth0/eth1 is the issue. I'm on eth1 at the moment, with no eth0. I'll reconfigure the IP with eth0 and try again.

---

### Post by jonobr on 2011-11-18
Same as me , Im not sure, but no harm in trying it out!

---

### Post by lightninhopkins on 2011-11-18
changed the .rules file to match one mac address and eth0, so no eth1 involved. 

/etc/udev/rules.d /70-persistent-net.rules

even made sure the resolvconf service is started at boot. 

still, back to an empty nameserver list on reboot.  

I guess the fix is to not reboot :)

---

### Post by jonobr on 2011-11-18
Kind of annoying-

You sir (madam , Mrs , Mr , Dr, sir, mam, pastor, father, rabbi) have stumped me

---

### Post by SeijiSensei on 2011-11-18
Edit /etc/dhcp3/dhclient.conf and remove the "domain-name-servers" and "domain-search" entries from the "request" directive.  

Another simple solution is to make /etc/resolv.conf read-only after you've edited it to your liking ("sudo chmod 444 /etc/resolv.conf").

---

### Post by lightninhopkins on 2011-11-18
Makes sense. I'll try it. Read only is a good idea.

---

### Post by lightninhopkins on 2011-11-18
Unreal. Read only resolv.conf (444), on reboot, permission goes back to 644 and nameservers get wiped out. 

Did the /etc/dhcp3 change too, nothing. 

It's just strange.

---

