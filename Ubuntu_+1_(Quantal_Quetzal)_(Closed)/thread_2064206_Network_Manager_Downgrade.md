---
title: "Network Manager Downgrade?"
date: 2012-09-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-09-28
Hidden wireless WPA security 
Precise network manager 0.9.4.1-0ubuntu2 
works fine on my Acer Aspire 1 netbook and this Ascer Aspire 5253 widescreen notebook

Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

The Aspire 1 netbook with a lot of fuss I can connect with QQ rarely connects automatically instead Disconnects automatically.

The netbook will connect manyually if I do a 
sudo dhclient wlan0
wait 5 seconds do a Ctrl-c.

QQ network manager drop down menu's very slow, sometimes up to a minute to respond to keying in the network name.

Yes there's a launchpad bug no suggestions from them.

Beta 2 I cnn't get the Aspire 5253 notebook to connect at all to the hidden wireless WPa.  Beta 2 runs fine wired but I'm nowhere near the wire right now.

Is there any way to downgrade QQ network manager to the Precise one or am I stuck with Precise no QQ?

Can't do a ubuntu-bug since there's no network connection to report it on.

Thanks for any suggestions.

---

### Post by cariboo on 2012-09-28
> **jerrylamos said:**
> Hidden wireless WPA security 
Precise network manager 0.9.4.1-0ubuntu2 
works fine on my Acer Aspire 1 netbook and this Ascer Aspire 5253 widescreen notebook

Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

The Aspire 1 netbook with a lot of fuss I can connect with QQ rarely connects automatically instead Disconnects automatically.

The netbook will connect manyually if I do a 
sudo dhclient wlan0
wait 5 seconds do a Ctrl-c.

QQ network manager drop down menu's very slow, sometimes up to a minute to respond to keying in the network name.

Yes there's a launchpad bug no suggestions from them.

Beta 2 I cnn't get the Aspire 5253 notebook to connect at all to the hidden wireless WPa.  Beta 2 runs fine wired but I'm nowhere near the wire right now.

Is there any way to downgrade QQ network manager to the Precise one or am I stuck with Precise no QQ?

Can't do a ubuntu-bug since there's no network connection to report it on.

Thanks for any suggestions.

What driver are you using? If you aren't sure, open a terminal and type:

```
sudo lshw -C network
```

Then look near the bottom of the output for the word driver.

---

### Post by jerrylamos on 2012-09-28
> **cariboo907 said:**
> What driver are you using? If you aren't sure, open a terminal and type:

```
sudo lshw -C network
```

Then look near the bottom of the output for the word driver. Thanks for the reply.  With a whole lot of thrash, 6 reboots, filled out network manager (sluggish!) menu drop downs, finally got up.  Had to authenticate something like 4 times in a row.  

sudo -C network [/CODE]
broadcast=yes driver=brcmsmac driverversion=3.5.0-15-generic firmware=N/A ip=192.168.0.6 link=yes multicast=yes wireless=IEEE 802.11bgn

network-manager 0.9.6.0-0ubuntu7

I could check the driver Precise uses.

Precise uses 
broadcast=yes driver=brcmsmac driverversion=3.2.0-29-generic firmware=N/A ip=192.168.0.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn

Any way to try either the Precise network manater or the driver from precise on QQ?

---

### Post by cariboo on 2012-09-28
> **jerrylamos said:**
> Thanks for the reply.  With a whole lot of thrash, 6 reboots, filled out network manager (sluggish!) menu drop downs, finally got up.  Had to authenticate something like 4 times in a row.  

sudo -C network [/CODE]
broadcast=yes driver=brcmsmac driverversion=3.5.0-15-generic firmware=N/A ip=192.168.0.6 link=yes multicast=yes wireless=IEEE 802.11bgn

network-manager 0.9.6.0-0ubuntu7

I could check the driver Precise uses.

Precise uses 
broadcast=yes driver=brcmsmac driverversion=3.2.0-29-generic firmware=N/A ip=192.168.0.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn

Any way to try either the Precise network manater or the driver from precise on QQ?

The first thing I'd suggest is to see if you can connect without WPA enabled. If that doesn't work, can you try connecting manually using the instructions [here]("http://ubuntuforums.org/showthread.php?t=571188")

If you can connect manually, then I'd say the problem is NetworkManager, 

If you don't want to try connecting manually, have you tried [wicd]("http://packages.ubuntu.com/quantal/wicd"), many of those that had problems with network connections during the last development cycle solved their problem using it. Wicd is in the repositories. Remember to remove NetworkManager completely before trying it.

---

### Post by jerrylamos on 2012-09-28
Rebooted again, this time wlan0 disconnected then connected here's a portion of syslog.  Since I know nothing about this I'd think some script sequences have gotten out of order?:

Log shows wlan0 ready
then disconnected??

Sep 28 17:13:24 Aspire-5253 NetworkManager[786]: <info> (wlan0): supplicant interface state: starting -> ready
Sep 28 17:13:24 Aspire-5253 NetworkManager[786]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Sep 28 17:13:24 Aspire-5253 NetworkManager[786]: <warn> Trying to remove a non-existant call id.
Sep 28 17:13:24 Aspire-5253 NetworkManager[786]: <info> (wlan0): supplicant interface state: ready -> inactive
......
some lines later connected??
......
Sep 28 17:13:52 Aspire-5253 wpa_supplicant[990]: wlan0: WPA: Key negotiation completed with 00:0f:b3:b0:d6:3c [PTK=TKIP GTK=TKIP]
Sep 28 17:13:52 Aspire-5253 wpa_supplicant[990]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:0f:b3:b0:d6:3c completed (auth) [id=0 id_str=]

Thanks for the pointers to more ways to get running.

---

