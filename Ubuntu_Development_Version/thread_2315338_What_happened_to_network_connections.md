---
title: "What happened to network connections?"
date: 2016-02-27
forum: Ubuntu Development Version
---

### Post by kurt18947 on 2016-02-27
If this has been discussed i haven't been able to find it. Previous versions of Ubuntu Gnome had an app "network connections" that enabled me to delete connections created by various wifi adapters and hotspots. Deleting unused connections can prevent confusion when connecting to a wifi network. I'm using current 16.04 and can't find that app. Is it another casualty of Gnome's drive to minimalism? It's still possible to delete unused network connections via /etc/NetworkManager/system-connections but having an app is easier and more foolproof.

---

### Post by sammiev on 2016-02-28
Hi,

Select Network --> Wi-Fi --> History --> check mark the one you want to delete and then Forget.

---

### Post by kurt18947 on 2016-02-29
> **sammiev said:**
> Hi,

Select Network --> Wi-Fi --> History --> check mark the one you want to delete and then Forget.

Thanks for your reply. That may work with different SSIDs but it appears to not work using different wifi adapters to connect to the same SSID. I was checking the performance of different USB wifi adapters in 16.04. I've noticed in the past that having more than one 'profile' (I'm not sure of the proper term) for the same SSID can cause connection problems. I can navigate to 
```
/etc/NetworkManager/system-connections 
```
and delete entries for adapters not currently installed but using 'network connections' is quicker and I don't have to open the 'profile' to be sure of deleting the proper entry. 14.04 has the 'network connections' app, I'm not sure about 15.10.

---

### Post by grahammechanical on 2016-02-29
Can you not do it through Network manager icon menu>Edit Connections>Select connection and click delete? Or System Settings>Network>select connection in the left pane and click the minus sign?

Don't either of these methods work?

Regards

---

