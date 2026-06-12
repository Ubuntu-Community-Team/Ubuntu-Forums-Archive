---
title: "Kxstudio Network-Manager dependencies issue"
date: 2011-05-19
forum: Ubuntu Studio
---

### Post by Friedrich_Nietzsche on 2011-05-19
I am having issues installing kxstudio, because it keeps installing network manager. Network-Manager was giving me suspend/restore problems, so I switched to wicd instead (works a thousand times better for me), however installing kxstudio reinstalls network-manager which prevents wicd from working at all and breaks my restore suspend (Most likely due to hardware incompatibility). If I remove network-manager again it uninstalls kxstudio entirely. 

I am new to Linux/Ubuntu, and am unable to find a solution via google or the search function? Any tips on taming the beast which is Network-Manager?

---

### Post by jejeman on 2011-05-19
You don't need to deinstall it, just turn it off.
Move the following file: /etc/init/network-manager.conf
somewhere safe.

---

