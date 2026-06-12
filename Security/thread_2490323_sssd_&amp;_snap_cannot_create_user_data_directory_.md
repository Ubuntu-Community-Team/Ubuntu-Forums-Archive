---
title: "sssd &amp; snap: cannot create user data directory: /home/aaaa.bbbb.be/u0xxxxxx/snap/v"
date: 2023-08-30
forum: Security
---

### Post by oliware69 on 2023-08-30
Hi,

Since about a week all snap installs (firefox/chromium/vlc/...) won't start anymore with our AD users. (firefox with repo install is a workarround for some)
--> cannot create user data directory: /home/aaaa.bbbb.be/u0xxxxxx/snap/vlc/3078: Permission denied

With a local user (our standard admin= ict2), the programs still can start.

When I manually change the homedir in sssd.conf, the homedirectory is recreated and the programs are starting again.
For new installs this 'solution' is acceptable, but not for the existing desktops/laptops, then the users will need to copy/move their old homedirectory, which causes a lot of manual work.

I have about 90 desktops & 40 laptops with this problem. All machines are configured with puppet (so scripts to join the domain and such are distributed via puppet).

I've tried the 'apparmor' trick, but this is ok: /etc/apparmor.d/tunables/home.d/ubuntu contains the /home/ &  /home/aaaa.bbbb.be/ directories

Any hints/tricks ?

Thx,

Oliver

---

### Post by oliware69 on 2023-08-30
colleague posted a bugreport as well:

[https://bugs.launchpad.net/snapd/+bug/2033404](https://bugs.launchpad.net/snapd/+bug/2033404)

---

### Post by oliware69 on 2023-09-01
Confirmed bug:

[https://forum.snapcraft.io/t/upgrade-snapd-from-2-59-5-to-2-60-2-gives-apparmor-denied-on-app-launch-for-every-app/36492/14](https://forum.snapcraft.io/t/upgrade-snapd-from-2-59-5-to-2-60-2-gives-apparmor-denied-on-app-launch-for-every-app/36492/14)

---

