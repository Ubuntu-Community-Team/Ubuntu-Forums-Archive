---
title: "Wifi secure"
date: 2015-08-03
forum: Ubuntu Phone and Tablet
---

### Post by robcar on 2015-08-03
I got a wifi network where I connect to from Android simply by entering the following parameters:

EAP: PEAP
Identity: CarraroR
Password: 12345678
No certificates.

And when it connects I see:
Security 802.1x EAP

When I select the same network with my MX4 and input the parameters the 'Connect' button is disabled.

---

### Post by robcar on 2015-08-05
Seems similar to this bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1241986](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1241986)

But I got prompted for username/password, only 'Connect' is disabled.

---

### Post by fallenshadow on 2015-08-07
I also had this issue on my MX4, couldn't connect to work WiFi using PEAP.

---

### Post by robcar on 2015-09-02
I opened a bug:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-system-settings/+bug/1490417](https://bugs.launchpad.net/ubuntu/+source/ubuntu-system-settings/+bug/1490417)

Got an almost immediate reply (the password has to be >= 8 characters - my password was only 6 chars) and managed to connect.

---

