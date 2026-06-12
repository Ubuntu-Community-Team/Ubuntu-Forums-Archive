---
title: "Vmware Server breaks internet"
date: 2008-05-17
forum: Virtualisation
---

### Post by theRightNee on 2008-05-17
hey all,
when i start my virtualized windows xp (home edition) my internet stops working...the wireless manager shows i am still connected, but i cannot access any webpages
this also affects my virtualized machine (NAT networking)
since i use a usb wireless device, could that be the issue? i have also been experiencing issues with connecting my printer to the computer, and i feel that this is the source of the problem

---

### Post by SKiDRoX on 2008-05-23
> **theRightNee said:**
> hey all,
when i start my virtualized windows xp (home edition) my internet stops working...the wireless manager shows i am still connected, but i cannot access any webpages
this also affects my virtualized machine (NAT networking)
since i use a usb wireless device, could that be the issue? i have also been experiencing issues with connecting my printer to the computer, and i feel that this is the source of the problem

I'm having similar problem.  I haven't had the time to play much with it but I saw this morning that I can't access internet on my wireless network anymore on my Ubuntu 8.04.  I've installed VMWare workstation 6 last night, which I guess it's the one that broke it.  I'll look around if this is a known issue!?!

---

### Post by Alteisen on 2008-06-09
Hi Same thing here my details:

== First occurance Gentoo 2.6.12 amd64 ==
Vmware-Player installed the amd64 version, configured bridge to wireless lan. Guest was a 64 bit Windows Server 2008. After about 12 hours the wireless did not work anymore. Meaning I was still connected, had an IP but nothing would load not even webpages and also pinging did not work anyomre (not even the gateway or DNS only myself)

I thougt it resulted from installing some masked packages so I installed a new linux

== Second occurance Ubuntu (Hardy)amd64 ==
Vmware-player installed amd64 (most recent), configured bridge to wireless lan. Guest again Windows Server 208 6 bit. Everything was perfect and again after about 12 hours it broke my host connection. Again nothing except pinging myself worked. 

Every help would be very appreciated as I only have a wireless connection were I currently stay, thus this is realy bad.

Edit: sorry forgot, I am using a T61p with the Intel 4965AGN card.

---

### Post by Alteisen on 2008-06-13
Well seems to be a hot topic ;)

I reinstalled my Ubuntu and updated it before installing VMware. This helped, my Linux with VMware and the wireless bridge is now running fine.

---

