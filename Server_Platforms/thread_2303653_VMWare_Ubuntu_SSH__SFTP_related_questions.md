---
title: "VMWare Ubuntu SSH / SFTP related questions"
date: 2015-11-20
forum: Server Platforms
---

### Post by DaMadHatter on 2015-11-20
Alright so let me start by saying I have been looking at a lot of related posts about VMWare and SSH errors regarding "Connection Refused" and after trying a lot of unsuccessful fixes and work a rounds, I have have finally decided to post and ask for help.

I am running a Windows 7 x64 Bit Desktop, with VMWare Workstation 12 and an Ubuntu 12.04 Guest OS, using bridged adapter. (Updated and Upgraded.)
The desktop works flawlessly and I have no trouble accessing the Guest OS via Putty or CoreFTP, I can view the website anytime and upload and download via FTP.

_**The Issue: **_
I have a laptop running Windows 7 x64 bit with Putty and CoreFTP neither of which can connect to the Guest OS. Always that cryptic error message "Connection Refused." I can however visit the site at the LAN IP Address via Browser.

_**My attempts: **_
I have attempted Disabling the CIS firewall (adding rules), disabling firewall and adding rules to the router, adding IPtables (in and out) to the Guest OS for SSH on port 22. Verified the install (SSH) and service is running, changed the conf file for IP, tried both static and dynamic IP's, added iptables to the guest OS, checked the banned list of IP's. I tried purging SSH and reinstalling, I have even deleted the VMWare Guest OS and reinstalled all with the same results. 

Kind of frustrating, any help would be greatly appreciated. **TIA**.

---

