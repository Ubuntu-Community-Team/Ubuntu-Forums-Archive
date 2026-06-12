---
title: "No wireless with brand new  oryx pro"
date: 2017-03-06
forum: System76 Support
---

### Post by mpmastroianni on 2017-03-06
Was delivered a month ago. Can connect over wired but no wireless. Running 16.04

Get the following 

```
dmesg | grep iwlwifi
[    2.579664] iwlwifi 0000:6e:00.0: enabling device (0000 -> 0002)
[    2.581450] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8000C-19.ucode failed with error -2
[    2.581605] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8000C-18.ucode failed with error -2
[    2.581671] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8000C-17.ucode failed with error -2
[    2.586286] iwlwifi 0000:6e:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    2.604335] iwlwifi 0000:6e:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[    2.604444] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[    2.604745] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[    2.746989] iwlwifi 0000:6e:00.0 wlp110s0: renamed from wlan0
[16360.568700] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[16360.569137] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[16360.705258] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[16360.705541] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[16404.125410] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[16404.126072] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[16404.261452] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[16404.261737] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365406.812809] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365406.813445] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365406.948800] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365406.949082] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365500.076524] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365500.077165] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365500.212451] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365500.212739] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365673.597742] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365686.232065] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8000C-19.ucode failed with error -2
[365686.232075] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8000C-18.ucode failed with error -2
[365686.232081] iwlwifi 0000:6e:00.0: Direct firmware load for iwlwifi-8000C-17.ucode failed with error -2
[365686.233022] iwlwifi 0000:6e:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[365686.247766] iwlwifi 0000:6e:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[365686.247837] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365686.248128] iwlwifi 0000:6e:00.0: L1 Enabled - LTR Enabled
[365686.387862] iwlwifi 0000:6e:00.0 wlp110s0: renamed from 

lspci | grep Network
6e:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
```



Any ideas?

---

### Post by kc1di on 2017-03-07
Hello mpmastroianni  and welcome to Ubuntu,
would you go to a terminal and enter this command and list the output here Thanks.
```
rfkill list
```

---

### Post by mpmastroianni on 2017-03-07
sure:

&#9584;&#9472;$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by Geoffrey_Arndt on 2017-03-07
1.  If not already done, login to System76 site and open a trouble ticket.
2.  Do you have the latest System76 drivers installed?  (Is their PPA activated)?
3.  You have a later wifi chip than I - but have older firmware (which didn't install).   You have 16.242xxx whereas I have 17.xxxxxx (seems strange).

PS - - did you try installing any wireless drivers manually from Intel by chance?

---

### Post by mpmastroianni on 2017-03-08
Thanks. How can you tell from that what firmware I have? Just curious so I can figure out myself as I try to work through this

Just added the systrem76 ppa, did an apt-get update, and apt-get install -y system76-drivers

Is there anything else I should do?

---

### Post by Geoffrey_Arndt on 2017-03-09
Yes .  .  .  after a reboot, if you still have no wireless . . . create the trouble ticket at Sys76 website.   They will email within with further info and instructions.

---

### Post by Geoffrey_Arndt on 2017-03-09
In your 1st post:   "[COLOR=#000000][FONT=&quot]2.586286] iwlwifi 0000:6e:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm"

My version is [/FONT][/COLOR]17.352738.0

Normally, Intel Wireless just works with no need for loading drivers or adjustment.    Best source of help now is System76.

---

