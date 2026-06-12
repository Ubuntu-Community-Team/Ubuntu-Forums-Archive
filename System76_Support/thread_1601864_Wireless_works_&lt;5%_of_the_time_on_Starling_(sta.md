---
title: "Wireless works &lt;5% of the time on Starling (star3) Netbook"
date: 2010-10-20
forum: System76 Support
---

### Post by fearailhold on 2010-10-20
I searched the forums before making this post, and I don't think that any problem like this has been posted before.

I recently purchased a Starling netbook (model star3) and am loving everything about it except for its wireless troubles. I have no problem detecting and connecting to wireless networks, and I always have good reception. However, once connected to a wireless network, my actual internet connectivity works only about 5% of the time. 

When the connection is not working, my Google Chrome browser sits at "Resolving host.." until eventually timing out and giving up. When it does work, I will have full speed connectivity for only a few minutes, and then it will revert back to the same problem. While all of this is happening, the wireless connection is maintained with good reception.

Below is the output of **dmesg | tail** during a time in which the connection is not working:
```
[  269.212061] ====>to send ADDBAREQ!!!!!
[  270.476052] ====>to send ADDBAREQ!!!!!
[  271.476047] ====>to send ADDBAREQ!!!!!
[  272.388108] ====>to send ADDBAREQ!!!!!
[  273.069138] ====>rx ADDBARSP from :68:7f:74:29:5e:6a
[  273.069150] rtllib: OnADDBARsp(): Recv ADDBA Rsp. BA invalid, DELBA! 
[  273.069162] __ratelimit: 4 callbacks suppressed
[  273.374506] ====>rx ADDBARSP from :68:7f:74:29:5e:6a
[  273.374518] rtllib: OnADDBARsp(): Recv ADDBA Rsp. BA invalid, DELBA! 
[  273.572201] ====>to send ADDBAREQ!!!!!
```

I routinely experience this problem on my home and work wireless networks, both of which use WPA. Wired networks work just fine.

I have tried both the *Install* and *Restore* options in the System76 driver software, but to no avail. Help! This has made my netbook unusable.

---

### Post by isantop on 2010-10-20
You might try power cycling your wireless card. 

First, check the status of the indicator light. It's the third one from the left on the front, left edge of the computer. It should be on and green. If it isn't, press Fn+F11 until it comes on.

Now, press Fn+F11 so that the light comes off. Once it does, wait for a few moments (Your wireless connection should disconnect). Then, press it again and wait for the light to come back on.

I've seen this fix issues like this before on this model. I think it might help you out.

---

### Post by fearailhold on 2010-10-20
I just tried this but it didn't seem to make a difference. Here's another clip of **dmesg** from the point I turned the wireless card back on.

```
[ 8352.966046] RX: IEEE802.1X EPAOL frame!
[ 8354.089810] RX: IEEE802.1X EPAOL frame!
[ 8355.338639] RX: IEEE802.1X EPAOL frame!
[ 8356.459064] RX: IEEE802.1X EPAOL frame!
[ 8358.573831] RX: IEEE802.1X EPAOL frame!
[ 8358.874585] RX: IEEE802.1X EPAOL frame!
[ 8360.351851] ==========>received disassoc/deauth(c0) frame, reason code:7
[ 8360.351878] notify_wx_assoc_event(): Tell user space disconnected
[ 8360.351896] ===========>RemovePeerTS,68:7f:74:29:5e:6a
[ 8360.351903] ====>remove Tx_TS_admin_list
[ 8360.352398] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8360.369119] ===>rtllib_associate_procedure_wq(), chan:1
[ 8360.369130] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 8361.922166] Linking with manders,channel:1, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[ 8361.922217] ===>rtllib_associate_procedure_wq(), chan:1
[ 8361.922230] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 8361.932273] Linking with manders,channel:1, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[ 8361.932298] ===>rtllib_associate_procedure_wq(), chan:1
[ 8361.932304] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 8364.440192] Linking with manders,channel:1, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[ 8364.440215] ===>rtllib_associate_procedure_wq(), chan:1
[ 8364.440224] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 8364.475893] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 8364.553778] Associated successfully
[ 8364.553787] normal associate
[ 8364.553815] Using G rates:108
[ 8364.553820] Successfully associated, ht enabled
[ 8364.553829] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[ 8364.559847] ====>rx ADDBAREQ from :68:7f:74:29:5e:6a
[ 8364.559865] ====>to send ADDBARSP
[ 8364.563817] ===>rtl8192se_link_change():ieee->iw_mode is 2
[ 8365.560009] RX: IEEE802.1X EPAOL frame!
[ 8365.650862] RX: IEEE802.1X EPAOL frame!
[ 8365.651183] alg name:CCMP
[ 8365.651219] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[ 8365.651445] alg name:TKIP
[ 8365.651487] ===========>set_swcam():EntryNo is 2,KeyIndex is 2,KeyType is 2,is_mesh is 0
[ 8367.377658] lo: Disabled Privacy Extensions
[ 8367.602987] rtllib: TsStartAddBaProcess()==>BA timer is already added
[ 8367.604187] rtllib: TsStartAddBaProcess()==>BA timer is already added
[ 8367.604348] rtllib: TsStartAddBaProcess()==>BA timer is already added
[ 8367.604720] rtllib: TsStartAddBaProcess()==>BA timer is already added
[ 8367.604863] rtllib: TsStartAddBaProcess()==>BA timer is already added
[ 8367.606470] rtllib: TsStartAddBaProcess()==>BA timer is already added
[ 8367.606618] rtllib: TsStartAddBaProcess()==>BA timer is already added
[ 8367.641046] ====>to send ADDBAREQ!!!!!
[ 8368.349050] ====>to send ADDBAREQ!!!!!
[ 8368.385135] ====>rx ADDBARSP from :68:7f:74:29:5e:6a
[ 8368.385145] rtllib: OnADDBARsp(): Recv ADDBA Rsp. BA invalid, DELBA! 
[ 8368.413949] ====>rx ADDBARSP from :68:7f:74:29:5e:6a
[ 8368.870576] rtl819xSE:Err RX pkt len = 0x15
[ 8368.870582] 
[ 8382.957120] ====>to send ADDBAREQ!!!!!
```

---

### Post by isantop on 2010-10-21
Are the routers set to "N-only" or "G-only" mode? If so, try setting them to "Mixed Mode" instead, as this is usually more reliable. You may need to consult your router's documentation for instructions.

---

### Post by fearailhold on 2010-10-21
My home router is set to mixed. It is a Linksys WRT320N.

I am unsure about the router at work, but I assume that it's also mixed, since it is a university and many people use it with many different systems.

Thanks for your continued help, by the way.

---

### Post by fearailhold on 2010-10-26
My Starling's wireless problem seems to have also caused my system to lock up. I was not running any special or weird programs when it happened (I think I just had a terminal window open). The system would not respond to any keyboard or mouse input commands. I had to hold the power button to force a shutdown.

When I tried to power it back on, it showed the System76 splash screen as usual, but then went blank and sat forever with a flashing cursor at the top left of the screen. Again I had to hold the power button to force a shutdown. The problem continued each time. Out of desperation, I pressed F2 (to enter BIOS) at the System76 splash screen (the system beeped to confirm), and instead of taking me into BIOS, it booted Ubuntu normally. Now my laptop boots normally again (F2 takes me into BIOS, otherwise it will boot Ubuntu as expected).

My wireless problem hasn't changed, but maybe the above incident can shed some light on the problem. Could this be a hardware problem instead of a software problem?

Below are the last twenty lines of **/var/log/syslog**, up until my system froze:

```
Oct 25 17:22:19 matt-netbook kernel: [  849.396988] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Oct 25 17:22:19 matt-netbook kernel: [  849.397141] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 25 17:22:20 matt-netbook kernel: [  850.918094] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 25 17:23:04 matt-netbook kernel: [  894.900172] ====>rx ADDBAREQ from :68:7f:74:29:5e:6a
Oct 25 17:23:04 matt-netbook kernel: [  894.900187] ====>to send ADDBARSP
Oct 25 17:23:04 matt-netbook kernel: [  894.901048] ====>rx ADDBAREQ from :68:7f:74:29:5e:6a
Oct 25 17:23:04 matt-netbook kernel: [  894.901059] ====>to send ADDBARSP
Oct 25 17:23:11 matt-netbook kernel: [  901.675111] lo: Disabled Privacy Extensions
Oct 25 17:23:13 matt-netbook kernel: [  903.684777] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Oct 25 17:23:29 matt-netbook kernel: [  919.428113] ====>to send ADDBAREQ!!!!!
Oct 25 17:23:29 matt-netbook kernel: [  919.430058] ====>rx ADDBARSP from :68:7f:74:29:5e:6a
Oct 25 17:24:19 matt-netbook kernel: [  969.397277] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Oct 25 17:24:19 matt-netbook kernel: [  969.397394] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 25 17:24:20 matt-netbook kernel: [  970.918152] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 25 17:25:21 matt-netbook kernel: [ 1032.182644] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Oct 25 17:26:19 matt-netbook kernel: [ 1089.394557] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Oct 25 17:26:19 matt-netbook kernel: [ 1089.394671] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 25 17:26:20 matt-netbook kernel: [ 1090.922102] ===>rtl8192se_link_change():ieee->iw_mode is 2
Oct 25 17:26:30 matt-netbook kernel: [ 1100.668107] ====>to send ADDBAREQ!!!!!
Oct 25 17:26:30 matt-netbook kernel: [ 1100.670006] ====>rx ADDBARSP from :68:7f:74:29:5e:6a
```
Can anyone help me?

---

### Post by thomasaaron on 2010-10-27
It could be. 

Please find another wireless access point to test with first, if you don't mind. That will rule out a firmware incompatibility with your current AP.

---

