---
title: "PowerBook G4"
date: 2014-04-29
forum: Utah Team - US
---

### Post by gulmer on 2014-04-29
I just installed Lubuntu on my Apple PowerPc laptop. The install went fine, the OS is usable except no WIFI and I can't get the battery icon on the panel. I ran lspci -nn | grep 0280 in terminal and the internal Broadcom BCM4306 v3 showed up, even the USB WIFI adapter showed up(Ralink). I went to Synaptics and installed the b43 driver, restarted and still no wifi. There seems to be no program to even show the wireless networks. I'm a long time Ubuntu user and I know wifi with Ubuntu but Lubuntu's new to me, at least navigating it's desktop is, so I downloaded Ubuntu for the PowerPc and tried the live cd in the Apple. Unfortunately, the main desktop was a white blank and the network program or any program disappeared behind the white, but the top panel was visible and I could see that Ubuntu could search for wifi networks and connect to my router, but I could not do anything past that. So, I've got Lubuntu installed and want my wife to use this laptop, but she needs the wifi to work. What is my next move to get WIFI to work? :confused:

---

### Post by Lars Noodén on 2014-04-30
What was the full line produced by ' lspci -nn | grep 0280' there?  Does your base station support the same mode?

---

### Post by gulmer on 2014-04-30
lspci -nn | grep 0280 results; 0001:10:12:.0 Network controller [2080]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 3), thats all. What do you mean "base station"? The router supports 802.11b/g/n. The Ubuntu live cd was connecting to the network/router with the Broadcom card.

---

