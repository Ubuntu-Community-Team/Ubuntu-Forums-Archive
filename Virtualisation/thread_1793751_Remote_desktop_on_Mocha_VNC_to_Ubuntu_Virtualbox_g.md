---
title: "Remote desktop on Mocha VNC to Ubuntu Virtualbox guest.."
date: 2011-06-30
forum: Virtualisation
---

### Post by timtincher on 2011-06-30
Hi! I'm trying to do remote desktop to my guest OS Ubuntu on Virtualbox from the app Mocha VNC Lite from iOS, Android, etc. 
How would I be able to make this work?

---

### Post by lmarmisa on 2011-06-30
Select Bridged Adapter in the network setup. If the NAT mode is selected, you will be not able to connect the guest from host.

---

