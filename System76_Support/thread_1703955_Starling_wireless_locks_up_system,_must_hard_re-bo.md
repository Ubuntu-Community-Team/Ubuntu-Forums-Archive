---
title: "Starling wireless locks up system, must hard re-boot"
date: 2011-03-09
forum: System76 Support
---

### Post by why on 2011-03-09
I have a star1 netbook. I did a full-upgrade to 10.04 some time back and WiFi stopped (got wpa_supplicant[1138] messages that the authentication timed-out). I have been looking for a solution - but nothing. Then I found out I did not have the latest system76 driver (2.6.1), so I upgraded to it. Now it just locks up my netbook (screen goes black except for the cursor which is frozen - must hard re-boot after turning off the WiFi using the switch under the WiFi light). The log files does not help much (included the last few lines below).

Mar  9 19:46:26 Lily NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar  9 19:46:26 Lily NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Mar  9 19:46:26 Lily NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Mar  9 19:46:26 Lily NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar  9 19:46:26 Lily NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar  9 19:46:26 Lily NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Mar  9 19:46:26 Lily NetworkManager: <info>  Config: set interface ap_scan to 1
Mar  9 19:46:26 Lily NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Mar  9Mar  9 19:59:49 Lily rpc.statd[898]: Version 1.1.6 Starting

Any idea's on how to fix this - a real pain not having WiFi when traveling?

-Graeme

---

### Post by isantop on 2011-03-10
Does it lock up immediately after boot, or is it after you do something in particular? Like, if you boot with WiFi disabled, then enable it.

---

### Post by why on 2011-03-10
It locks up as soon as I log into the user account - due to the "connect automaticlly" button being checked in the NetworkManger after asking to connect to an wireless SSID the first time around (by killing the WiFi I then can go in and delete the wireless entry or at least uncheck the "connect automatically" button then can turn the WiFi ON again).

-Graeme

---

### Post by isantop on 2011-03-11
Does it do this if you boot it from an Ubuntu LiveCD as well?

---

### Post by smurphy_it on 2011-03-11
```
It locks up as soon as I log into the user account - due to the "connect automaticlly" button being checked in the NetworkManger after asking to connect to an wireless SSID the first time around (by killing the WiFi I then can go in and delete the wireless entry or at least uncheck the "connect automatically" button then can turn the WiFi ON again).
```

Does this mean if wireless is disabled, you can login successfully and the system won't lock up ?  Or that it will lock up regardless ?

You could try Ctrl-Alt-F1, and create a new user, give them appropriate rights, then login to x-windows with that account and see what happens.

---

### Post by why on 2011-03-14
> **isantop said:**
> Does it do this if you boot it from an Ubuntu LiveCD as well?

The Live CD has the old problem when trying to connect to a WPA wireless AP of forever asking for the wireless password (back to the original wireless problem I had of wlan0: link timed out)

---

### Post by why on 2011-03-14
> **smurphy_it said:**
> ```
It locks up as soon as I log into the user account - due to the "connect automaticlly" button being checked in the NetworkManger after asking to connect to an wireless SSID the first time around (by killing the WiFi I then can go in and delete the wireless entry or at least uncheck the "connect automatically" button then can turn the WiFi ON again).
```

Does this mean if wireless is disabled, you can login successfully and the system won't lock up ?  Or that it will lock up regardless ?

You could try Ctrl-Alt-F1, and create a new user, give them appropriate rights, then login to x-windows with that account and see what happens.

It means as soon as the WiFi tries to connect to the wireless AP that is now in the networkManger list with the "auto connect to" button ticked of it will lock up the netbook. As long as I have the WiFi OFF so I can delete the info in the NetworkManager to auto connect to a wireless AP then the netbook works just fine. After than I can turn the WiFi ON, and as long as I don't try and connect to a wireless AP everything is OK.

Creating a new account would only work if when I tried to connect to the wireless AP the first time the "available to all user" button is not ticked off.

Note the NetworkManager is creating this profile the first time I try to connect to the wireless AP (as far as I can tell I have no control over this).

-Graeme

---

### Post by smurphy_it on 2011-03-15
Sounds like the wireless drive should be replaced.  That should fix your issue.  If you said same problem on the Live CD, then you must be using a linux driver for the wifi.

As this was an upgrade, it might be pertinent to remove wpa_supplicant, and put it back in clean.

What wireless care are you using ?

```
lspci | grep [Ww]ireless
```

---

### Post by why on 2011-03-15
Some progress

0) WiFi is a Realtek RTL8187B WLAN Adapter 00e04c000001
1) 9.10 Live CD, using the Linux default driver, the WiFi works but the range is very limited (what the System76 driver was to have fixed)
2) 10.04 Live CD, using the Linux default driver, WiFi does NOT work, time out issues
3) 10.04 disk version using 2.6.1 system76 driver, locks up must hard re-boot
4) 10.10 Live CD, using the Linux default driver, the WiFi works but the range is very limited (what the System76 driver was to have fixed)

Next step is to upgrade to 10.10 so I can install the system76 driver (hopefully the 2.6.1 driver is compatible with 10.10) to make sure WiFi works over a reasonable range

-Graeme

---

### Post by why on 2011-03-18
> **why said:**
> Next step is to upgrade to 10.10 so I can install the system76 driver (hopefully the 2.6.1 driver is compatible with 10.10) to make sure WiFi works over a reasonable range

It appears that the system76 driver is not yet coded for 10.10, so I hacked the /opt/system76/system76-driver/src/misc.py file & ran system76-driver from the terminal. This compiled the r8187b module & blacklisted the rtl8187 module (see [http://ubuntuforums.org/showthread.php?t=1455704&page=2]("http://ubuntuforums.org/showthread.php?t=1455704&page=2")). However it gives the same outcome as it did in 10.04 (black screen expect for the cursor & completely locked up requiring a hard boot). So while I can at least get the WiFi to work using the default rtl8187 module, the distance it works over is rather short....with very low bit rates.

-Graeme

---

### Post by Flyers2391 on 2011-03-21
> **why said:**
> It appears that the system76 driver is not yet coded for 10.10, so I hacked the /opt/system76/system76-driver/src/misc.py file & ran system76-driver from the terminal. This compiled the r8187b module & blacklisted the rtl8187 module (see [http://ubuntuforums.org/showthread.php?t=1455704&page=2]("http://ubuntuforums.org/showthread.php?t=1455704&page=2")). However it gives the same outcome as it did in 10.04 (black screen expect for the cursor & completely locked up requiring a hard boot). So while I can at least get the WiFi to work using the default rtl8187 module, the distance it works over is rather short....with very low bit rates.

-Graeme

Are you using the latest driver from [http://planet76.com/repositories/](http://planet76.com/repositories/) ?  The second from the bottom ([http://planet76.com/repositories/system76-driver-2.6.1.deb](http://planet76.com/repositories/system76-driver-2.6.1.deb)) has a modified date of 2/11/11 so it would seem like a major oversight to not work on 10.10, on more than one driver version too.

---

### Post by why on 2011-03-28
> **Flyers2391 said:**
> Are you using the latest driver from [http://planet76.com/repositories/](http://planet76.com/repositories/) ?  The second from the bottom ([http://planet76.com/repositories/system76-driver-2.6.1.deb](http://planet76.com/repositories/system76-driver-2.6.1.deb)) has a modified date of 2/11/11 so it would seem like a major oversight to not work on 10.10, on more than one driver version too.

Yes I have the latest driver

---

### Post by why on 2011-06-07
natty (11.04) has the correct driver by default - so system76 no longer requires any special driver

---

