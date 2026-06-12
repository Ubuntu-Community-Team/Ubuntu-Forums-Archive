---
title: "Broadcom wireless disabled when waking up"
date: 2012-01-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TheNessus on 2012-01-25
Is my broadcom 4313 sleepy or what?
Let's solve this. What should I provide?
accompanied symptoms include applications not starting when I click on them, anything from system apps to terminal. i have to hard reboot, but this doesn't always happen when I lose wireless on wake-up.
Once I reboot and log on, usually I still have no wireless, but then at least i have the option to switch it to "on" where it is on "off". (when waking up without wireless, before rebooting, I have neither options, i have only "disabled".)

Also it hangs for 20-30 seconds when switching to different wireless networks.

did not happen in 11.10

---

### Post by linux6994 on 2012-02-01
I have a BCM4318 that worked fine using the ndiswrapper on oneiric. I got the ole' upgrade itch and pushed it up to precise. Now ndiswrapper fails to load even with b43 AND SSB blacklisted, ndiswrapper in modules and bcml5 driver installed hw present =yes.

punting going back down, nice try while it lasted :)

---

