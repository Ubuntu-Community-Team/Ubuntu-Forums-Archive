---
title: "Did I just get ninja 'd"
date: 2012-01-27
forum: Security
---

### Post by stellarsky on 2012-01-27
I have a samsung galaxy s continuum that i rooted and installed linux ubuntu 9.04
last night i checked fing network monitor and saw a apple iphone sync 'ing , we have a apple i pad in the house but not a i phone ,our wifi router is set up for mac address only filtering, i checked the sync service on my phone and the iphone was sync ing my phone.
i see now that there is a option to make the mac addresses on network in fing private , for this reason i guess. also the ipad we have has a assigned name the iphone just said i phone . so could sombody have been monitoring my network via my phone got the mac address for the ipad and came back with a i phone and cloned my phone ?
I did shut down the router and all devices to try and stop the sync
is there a way to see what was done
here is some log files but my guess is there vague and look legit:

from overlook fing:
62078/iphone-sync iPhone synchronizing

from system monitor on my phone:
sync
vm application process
excluded no
pid 2671
process name sync.service

---

### Post by MadsRC on 2012-01-28
You should not use MAC filtering for your network. The only persons it might keep out are the non tech savy. Any determined attacker will easily be able to clone a mac addresse. This is because mac addresses isn't encrypted in a wireless network, and thus can easily be sniffed and cloned.

So, I'll suggest changing to WPA2-PSK (Preferable WPA2-Enterprise if available) and deactivate WPS (if you own a Cisco/Linksys router your out of luck... WPS can be disable in the menu, but will still be enabled due to a bug in the firmware.)

---

### Post by Rob_H on 2012-01-28
> **MadsRC said:**
> You should not use MAC filtering for your network. The only persons it might keep out are the non tech savy. Any determined attacker will easily be able to clone a mac addresse. This is because mac addresses isn't encrypted in a wireless network, and thus can easily be sniffed and cloned.

So, I'll suggest changing to WPA2-PSK (Preferable WPA2-Enterprise if available) and deactivate WPS (if you own a Cisco/Linksys router your out of luck... WPS can be disable in the menu, but will still be enabled due to a bug in the firmware.)

+1. Stellarsky, you didn't say if your network is protected with WPA or not, but that is the only effective way to protect a wireless network. MAC address filtering does nothing except prevent someone from accidentally connecting to your network. It's easy to circumvent.

---

### Post by stellarsky on 2012-01-28
thank you for the quick replies. I read in another post about some problems with ubuntu 11.04 and wpa /2 and it was suggested to use the mac address filtering and I did have a problem when I tryed to activate the security on my router its a belkin and once it was activated my lap top could not connect to the internet or to the routers home page I tried hardline to the router and wifi  the only way we could get in is through my wifes netbook hardlined to the router using windoze ( probably experience was errored on my part ) we want the extra security though and are willing to try again ( it was a painstaking experience ), also the amount of wifi devices we have compatibility was a concern ( wii on wifi for netflix is the primary concern )
The linux on the phone is in the process of the build so ( I dont know why ) but commands like last and history apparently are not working yet but I'm currently upgrading to a newer and more stable distro of linux for the phone.

---

### Post by Rob_H on 2012-01-28
> **stellarsky said:**
> I read in another post about some problems with ubuntu 11.04 and wpa /2 and it was suggested to use the mac address filtering

Whomever said that was giving out bad advice, I'm afraid. Ubuntu works fine with WPA in general, but some wireless devices work better than others "out-of-the-box". For example, some Broadcom chipsets require closed-source drivers that need to be installed explicitly using the "Additional Drivers" utility in Ubuntu.

If your laptop doesn't work right away, try posting details about your wireless hardware on the Networking & Wireless forum and someone there might be able to help.

---

### Post by OpSecShellshock on 2012-01-28
To put your mind at ease on one score anyway: yes, the Wii does support WPA2.

---

