---
title: "Dansguardian corrrupted my intertnet"
date: 2009-08-15
forum: Ubuntu Christian Edition
---

### Post by Orlsend on 2009-08-15
Hi I am running the latest Ubuntu CE, the other day I unistalled Danguardians and since then my Internet connection is acting funky only VoIP and apt-get installers work (NO browser). I think dansguardian messed it up when leaving my system.

---

### Post by david_kt on 2009-08-15
> **Orlsend said:**
> Hi I am running the latest Ubuntu CE, the other day I unistalled Danguardians and since then my Internet connection is acting funky only VoIP and apt-get installers work (NO browser). I think dansguardian messed it up when leaving my system.

Do you mean you uninstall dansguardians from ubuntu ce? If yes, you must uninstall tinyproxy and firehol as well.

DK

---

### Post by Orlsend on 2009-08-16
Yaeh that didnt't work either so I typed "network" on my synaptic and purged all the installed conponents showing there. rebooted and it worked.

---

### Post by david_kt on 2009-08-16
> **Orlsend said:**
> Yaeh that didnt't work either so I typed "network" on my synaptic and purged all the installed conponents showing there. rebooted and it worked.

After uninstall firehol and tinyproxy, you must reboot to clear the iptables.

Anyway, you don't really need network-manager for desktop. But make sure you edit /etc/network/interfaces properly.

If you are using laptop, you should re-install network-manager and remove setting from /etc/network/interfaces.

DK

---

