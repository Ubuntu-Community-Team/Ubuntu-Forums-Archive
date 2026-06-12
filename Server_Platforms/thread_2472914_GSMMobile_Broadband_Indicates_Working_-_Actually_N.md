---
title: "GSM/Mobile Broadband Indicates Working - Actually No Internet"
date: 2022-03-16
forum: Server Platforms
---

### Post by tbnrc on 2022-03-16
Hello folks,

I'm working with some SBCs (multiple of the same model). I've installed Ubuntu Server 20.04 LTS. I'm using a Telit LE910C4-NF LTE modem over USB (and mPCIe on USB rails).

Following initial setup, I install network-manager and modemmanager.

I setup a new gsm connection with nmcli named "LTE", and set the appropriate gsm.apn. Lastly, "nmcli con up LTE".

"nmcli device status" shows my gsm connection active, green, connected on cdc-wdm0.

"nmcli r" indicates all radios are active.

"ip a" & "ifconfig" both indicate the correct IP (static from the ISP end), DNS servers, etc.

"mmcli -m 0" indicates the modem is working, connected, signal is good at 60%.

But I get no internet. 

"ping 8.8.8.8" results in "Host unreachable". "ping google.com" results in Temporary resolve failure.

I attempt to set "ipv4.dns" to 1.1.1.1 1.0.0.1 in the LTE profile on network manager, with no change.

In Ubuntu Desktop, the modem works without any trouble. What is happening on Server?

---

### Post by volkswagner on 2022-03-20
Try some other tools like traceroute and post your routing table.

---

