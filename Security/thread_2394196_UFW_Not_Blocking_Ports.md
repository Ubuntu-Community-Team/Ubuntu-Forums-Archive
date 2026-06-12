---
title: "UFW Not Blocking Ports?"
date: 2018-06-13
forum: Security
---

### Post by Altin on 2018-06-13
I have an Ubuntu 14.04 server which has a file server installed. I ran an Nmap scan against it today and got an unexpected result. Ports which I have not permitted through UFW are showing up on the port scan. I dont have 139/tcp allowed in my UFW rules, yet it appears in the Nmap scan. Port 21 was also showing up in the scan, which I had not permitted, until I uninstalled vsftpd. Why arent these ports being blocked by UFW?

[IMG]https://cdn.pbrd.co/images/HpL7SH1.png[/IMG]

---

### Post by TheFu on 2018-06-14
a) please don't post images. Use text.
b) run the scan from a different IP.

---

