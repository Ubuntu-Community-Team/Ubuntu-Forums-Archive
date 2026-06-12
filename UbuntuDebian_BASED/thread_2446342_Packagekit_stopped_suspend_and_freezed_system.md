---
title: "Packagekit stopped suspend and freezed system"
date: 2020-06-29
forum: Ubuntu/Debian BASED
---

### Post by haytham-med on 2020-06-29
Hi guys

Auto Suspend in kde neon was interrupted by packagekit and system freezed , Only hard reboot works.
Logs's here [https://pastebin.com/UXxU0pfV](https://pastebin.com/UXxU0pfV)

This happened in ubuntu 18.04 too many times, but i don't have logs from ubuntu to assure that.
I'm only left with dark screen that won't respond to anything but system hasnot entered sleep mode, 2 LED lights still on.


Edit, log when suspend started: [https://pastebin.com/uxLd9uqS](https://pastebin.com/uxLd9uqS)
Kernel log show 2 lines at this time 

Jun 29 09:36:07 hay207-Lenovo-G50-70 kernel: [108503.502862] wlp2s0: deauthenticating from 1c:59:9b:8c:40:4c by local choice (Reason: 3=DEAUTH_LEAVING)
Jun 29 09:36:08 hay207-Lenovo-G50-70 kernel: [108504.514549] PM: suspend entry (deep)

---

