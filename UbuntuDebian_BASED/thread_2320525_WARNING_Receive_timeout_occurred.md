---
title: "WARNING: Receive timeout occurred"
date: 2016-04-14
forum: Ubuntu/Debian BASED
---

### Post by utnubu4 on 2016-04-14
Hey folks,

I am having trouble with reaver in my Kali operating system. I have been attempting to crack a WPA password with no success. This message keeps repeating after i execute the command "WARNING: Receive timeout occurred", it loops infinitely. I have attempted to update reaver but i already have the latest version.

Very recently i purchased a brand new USB external network card.. this is the make and model: ALFA AWUS051NH, the actual network chip is a Ralink Technology, Corp. RT3572. The USB device seems great and has no issue entering monitor mode. This USB device is also a recommendation for Kali distro.

This is the exact command i have been running

```
reaver -i wlan1mon -c 1 -b X:X:X:11:20:0F -vv -N -S -A
```

and this is the exact result i am receiving

```
Reaver v1.5.2 WiFi Protected Setup Attack Tool
Copyright (c) 2011, Tactical Network Solutions, Craig Heffner <cheffner@tacnetsol.com>
mod by t6_x <t6_x@hotmail.com> & DataHead & Soxrok2212

[+] Switching wlan1mon to channel 1
[?] Restore previous session for X:X:X:11:20:0F? [n/Y] n
[+] Waiting for beacon from X:X:X:11:20:0F
[+] Associated with X:X:X:11:20:0F (ESSID: TNCAP13250F)
[+] Starting Cracking Session. Pin count: 0, Max pin attempts: 11000
[+] Trying pin 12345670.
[+] Sending EAPOL START request
[!] WARNING: Receive timeout occurred
[+] Sending EAPOL START request
[!] WARNING: Receive timeout occurred
[+] Sending EAPOL START request
[!] WARNING: Receive timeout occurred
[+] Sending EAPOL START request
[!] WARNING: Receive timeout occurred
[+] Sending EAPOL START request
```

I have tried many different things to solve this issue but nothing seems to work, i have been searching the internet with zero luck. I feel there may be some expert knowledge here ate the Ubuntu forum that can help and maybe solve this issue.

---

### Post by howefield on 2016-04-15
Thread moved to the "*Ubuntu/Debian BASED*" forum and closed.

---

