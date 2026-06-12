---
title: "firewall uable to start..."
date: 2008-07-17
forum: Security
---

### Post by waggingwabbit on 2008-07-17
When i open firestart I get this message:

"Failed to start the firewall

The device eth0 is not ready.

Please check your network device settings and make sure your internet connection is active."

I've just recently upgraded my computer because my old hardware was failing on me. I have a new motherboard, PSU, and processor using my other old parts. Could this hardware change be the reason why my firewall isn't starting? or am i being attacked or watched in anyway?

---

### Post by brian_p on 2008-07-17
> **waggingwabbit said:**
> 

I've just recently upgraded my computer because my old hardware was failing on me. I have a new motherboard, PSU, and processor using my other old parts. Could this hardware change be the reason why my firewall isn't starting? or am i being attacked or watched in anyway?

Firestarter doesn't think you have chosen the correct interface and wants you to look at its network settings.

---

### Post by Keeters on 2008-07-17
Just curiosity but try running 'ifconfig' (in the terminal) and then after that run 'ifconfig -a' and see if the interface that you are trying to use didn't show up in the first one but showed up in the second one. The '-a' argument tells ifconfig to list all interfaces weather they're up or down. If its down then its just a matter of enabling it.

---

### Post by waggingwabbit on 2008-07-18
thats strange...i typed in ifconfig and then with the -a, they both say the same thing. eth1 and lo. but now my firewall is active....

when i started ubuntu though, one of my gnome applets (the trash can) didn't show up. i got a pop up error message telling me something and asked if i wanted to keep or delete my configuration. this happened to me with my firefox shortcut on avant bar also...whats with all the errors?

---

