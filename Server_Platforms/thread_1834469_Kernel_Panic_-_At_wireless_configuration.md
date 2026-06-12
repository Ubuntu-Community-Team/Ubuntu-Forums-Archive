---
title: "Kernel Panic - At wireless configuration"
date: 2011-08-27
forum: Server Platforms
---

### Post by Mashashi on 2011-08-27
Not sure if this is some kind of bug I was trying to play around with ubuntu server 11.04 and configuring wireless through a usb pen. For the following wpa_supplicant configuration:

ctrl_insterface=/var/run/wpa_supplicant

network={
    ssid="MyID"
    psk="MyPassword"
    key_mgmt=WPA-PSK
    proto=RSN WPA
    pairwise=CCMP TKIP
}

When executing the command: 

wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 

It seems to happen some kind of bug and I am forced to restart. It is presented to me the following screen.

[http://postimage.org/image/4l6m5pac/](http://postimage.org/image/4l6m5pac/)

Thanks I would apreciate if someone could tell me what I'm doing wrong.

My network is detected by:

sudo iwlist wlan0 scan
Note: I decided to open a new thread becouse of the bug sorry I have seen similar issues but I think it is justified, by the issue extension.

---

