---
title: "Landscape - reboot automatically after package upgrade"
date: 2017-11-21
forum: Server Platforms
---

### Post by adamlmark on 2017-11-21
We configured a Landscape profile to automatically upgrade our servers on Monday nights. I received an alert from Landscape that this server required a reboot, but unfortunately our users noticed the VPN was down before I had my morning coffee.

Is there a way to automatically reboot servers after a package upgrade that requires a reboot? I don't see a way to do this from Landscape. I suppose I could set a weekly cron job after the Landscape upgrades, but that seems unnecessary.

I am new to Landscape, so I may be missing something obvious.
Thanks in advance!

---

### Post by slickymaster on 2017-11-21
Thread moved to **Server Platforms** for a better fit

---

### Post by adamlmark on 2017-11-28
This happened again after last night's upgrades, only this time it did not indicate a reboot was required. I guess my best option is to set up a cron job to reboot after weekly upgrades.

FYI the VPN server is Pritunl.

---

