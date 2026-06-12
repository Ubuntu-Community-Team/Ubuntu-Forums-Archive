---
title: "Installing Lubuntu 16.04 on Lenovo IdeaPad S10 Model 11G3G, boots to black screen"
date: 2016-02-17
forum: Ubuntu Development Version
---

### Post by Justin_Driver on 2016-02-17
So I recently decided to bring back an old Netbook from the dead. Windows was corrupt and that left me deciding a Linux install was a good idea. I have installed Lubuntu 16.04 from a USB boot stick. When i attempt to boot up the machine I wind up going straight to a black screen with a functional cursor, nothing else is visible. If I boot up in recovery mode, everything appears to be fine. I have no internet connectivity at this time, so I need to fix whatever display error I am having, and then straighten out my wireless drivers. Or vice versa. What is my problem here?

---

### Post by Justin_Driver on 2016-02-17
I have followed some other information I found regarding this problem and have setup the nomodeset option, but when I boot up I still have the same issue.

---

### Post by Bucky Ball on 2016-02-17
*Thread moved to **Ubuntu Development Version**.*

16.04 LTS is not released until April. All threads concerning it go here. I'm unsure why 16.04 LTS is where you've started as a new user. I recommend you install a supported release, 14.04 LTS or 15.10, and start again unless you are willing to test and report any oddities in this area. 

Expect the unexpected. We do not guarantee that 16.04 will be or remain stable at this point (although it's working fine for me at the moment, that might not be the case tomorrow or a week from now) and you should update/upgrade daily. You should not be using it in work or production scenarios where breakage could be critical.

Good luck, however you choose to fly.

---

### Post by SurfaceUnits on 2016-02-18
Find out what GPU is in the laptop and whilst in recovery mode install the driver for that GPU. I had the same issue on an old eMachines PC

---

### Post by Clifford_Sarokoff on 2016-02-27
> **SurfaceUnits said:**
> Find out what GPU is in the laptop and whilst in recovery mode install the driver for that GPU. I had the same issue on an old eMachines PC

What a good suggestion!  I had the problem of booting to a dark screen, read your post and solved my problem.  On my Ubuntu 16.04 setup, I went to System Settings, Software and Updates, Additional Drivers.  I let it search for proprietary drivers.  I chose it, when I rebooted the problem was gone. 
Thanks for an easy fix, thanks for posting it! \\:D/
CliffordS

---

