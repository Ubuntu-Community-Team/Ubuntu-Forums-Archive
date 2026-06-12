---
title: "After dual booting Ubuntu and Windows 10, Windows can no longer find WiFi networks."
date: 2018-03-04
forum: Windows
---

### Post by mikepd213 on 2018-03-04
My laptop is a Lenovo Ideapad 500-15acz. My wireless adapter is a Qualcomm Atheros QCA61x4.

When I boot Windows, it says "No WiFi networks found." I've followed every step on the Microsoft support site in fixing connectivity problems, but nothing worked. My guess is that I did something in Ubuntu/Kali that has now made my network card unusable in Windows. I had had Ubuntu installed for a few weeks and had been doing some experimenting with nmap and wireshark. I'm not sure exactly when the problem started. Wireless works perfectly on Ubuntu and on Kali live USB.

I've even cleaned my drive and reinstalled Windows from a recovery DVD, but my wireless card still will not show networks. I can view my card in Device Manager and it shows it to be working fine.

Is it possible that I unknowingly messed with my wireless card in Linux that has now made it unusable on Windows? Any help is greatly appreciated, and I'll give any more information you might need.

Thank you!

---

### Post by jeremy31 on 2018-03-04
*Thread moved to **Windows**.*

Try going into UEFI/BIOS and reset to defaults, also check to see if WLAN is enabled there.  I know if my WLAN isn't enable in UEFI on my Lenovo, it isn't even detected in Ubuntu

---

### Post by mikepd213 on 2018-03-04
I just did what you said, but nothing changed. WLAN was enabled already in the UEFI, and I'm pretty sure the UEFI settings were already at the default since I cleaned my drive and reinstalled Windows last night out of desperation. I no longer have Ubuntu dual booted at the moment but WiFi works fine on my Kali USB. Anything else I could try? I'm almost certain I did something in the Linux terminal that caused this. Thanks

---

### Post by mikepd213 on 2018-03-04
Also I just noticed when I run ipconfig on Windows it says "Media disconnected" under Wireless LAN. I don't know if that means the wireless adapter is disconnected or just that I'm not connected to WiFi which is obvious.

---

### Post by theaccountant on 2018-09-06
Check the wireless network card driver under device manager. Uninstall and restart the computer and it will automatically install. See if there will be any changes.

---

