---
title: "QNAP Finder From VirtualBox"
date: 2008-10-20
forum: Virtualisation
---

### Post by con on 2008-10-20
I installed Windows XP SP3 under VirtualBox just so I could set up my new TS-109 NAS. It has to be "initialised" with the QNAP application "Finder", which only works on Windows/Mac.

The problem is the app' reports back that it can't find the NAS on the network. This is a little frustrating as finding it manually is no problem. Getting the IP address from my router I can connect to the NAS and bring up a holding page which says "This device has not being initialised". It then gives instructions on using Finder to initialise it.

The common reason for Finder not being able to detect a NAS is a problem with Firewall/Virus software. What I have is a clean install of XP with the built in firewall disabled so there shouldn't be any problem there. Otherwise networking seems to work fine under the virtual machine.

So finally to my question, is there anything about networking on a virtual machine which would cause an app to be blocked from a network, like a firewall might do. Very broad and general I know, but I'm kinda stuck.

---

### Post by frokki on 2009-09-24
--
EDIT: SOLVED!

I just married the virtual NIC to my host interface (wlan0) from the VirtualBox machine settings, and that did the trick!
--


I am suffering the same problem with TS-209 Pro II!

The IP of the NAS device is by default 169.254.100.100. I configured my router's LAN to 169.254.100.1 /16 and Ubuntu laptop to 169.254.100.101. I installed the finder software on clean XP SP3 VirtualBox OSE install, but it won't find the QNAP. Even though the web interface [SIZE="1"](saying "The system is not configured. Please refer to the Quick Installation Guide or user manual for software configuration.")[/SIZE] works from both operating systems.

---

