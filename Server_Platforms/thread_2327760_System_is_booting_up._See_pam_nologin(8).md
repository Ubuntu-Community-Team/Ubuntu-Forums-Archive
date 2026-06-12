---
title: "System is booting up. See pam_nologin(8)"
date: 2016-06-14
forum: Server Platforms
---

### Post by anders20 on 2016-06-14
Hardware:
CPU: Intel i7-5820k
HK: ASRock X99M Extreme
Ram: Corsair Vengeance LPX DDR4 2666MHz 16GB
OS disk: HyperX Fury SSD 120GB 2,5"
OS: Ubuntu server 16.04 LTS

Sometimes when i reboot i get this error when i start up, the error does so I can't login with any credentials.  To solve it i have to manually shutdown\reboot the computer and it starts up normally.

---

### Post by anders20 on 2016-06-20
Insane response, I can't be the only one with this problem. Anyone know a fix? Any recommendation would be appreciated..

---

### Post by robert48 on 2016-07-10
I have the problem too on both AMD and Intel chipped Ubuntu 16.04. The way it works with me is that (sometimes) the "System is booting up. See pam_nologin(8)" error is shown in the login window. I can't log in. I then reboot and up pops a correct log in window but the wi-fi connection is disabled. I reboot again and get a clean login window and wi-fi connects automatically as expected.

You are certainly not alone with this issue.

EDIT
Software Updater>Settings>Developer Options then check box labelled "Pre-released updates..."
That fixed it for me (fingers crossed!)

---

