---
title: "network manager not displaying Cisco Anyconnect VPN"
date: 2015-06-04
forum: Virtualisation
---

### Post by au10tic on 2015-06-04
new to linux here, but i managed to install openconnect via: apt-get install openconnect network-manager-openconnect the package gets installed but the network manager is not showing the option to create a vpn connection as that via the gui.. see screenshot below, which is running on Lubuntu 15.04
[ATTACH=CONFIG]262412[/ATTACH]

This works on ver: Lubuntu 14.04.2 LTS. 
[ATTACH=CONFIG]262413[/ATTACH]

I've tried restarting the manager or rebooting but same results, I am running Lubuntu as a VM on VMWare Player. Any help is appreciated.

---

### Post by au10tic on 2015-06-05
anyone? is there a way to uninstall network-manager and install an earlier version?

---

### Post by au10tic on 2015-06-10
nevermind, i've managed to fix this.. How can i solve/close this thread?

---

### Post by Bucky Ball on 2015-06-10
Thanks for marking as solved. That is all that is required. It serves to help others but leaves the thread open for further discussion. 

Would be nice to share with the community how you fixed your problem. Good luck. :)

---

### Post by au10tic on 2015-06-11
i managed to get it to show by installing openconnect like this: sudo apt-get install openconnect network-manager-openconnect-gnome then restart network-manager like so: sudo /etc/init.d/network-manager restart

---

