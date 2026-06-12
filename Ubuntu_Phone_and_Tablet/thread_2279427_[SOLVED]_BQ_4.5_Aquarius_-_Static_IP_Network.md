---
title: "[SOLVED] BQ 4.5 Aquarius - Static IP Network"
date: 2015-05-23
forum: Ubuntu Phone and Tablet
---

### Post by ElToro on 2015-05-23
I have a LAN with no DCHP and all devices on the network are set up with a static ip-address. I have followed the receipt here: [http://www.linuxveda.com/2014/09/08/static-ip-wifi-network-ubuntu-touch/](http://www.linuxveda.com/2014/09/08/static-ip-wifi-network-ubuntu-touch/) In addition, I used this as a reference: [https://wiki.ubuntu.com/Touch/Networking](https://wiki.ubuntu.com/Touch/Networking)

I am trying to connect my BQ 4.5 Aquarius (Ubuntu 14.10 r22). After editing the SSID profiles as set out in the links above, I restarted the phone (just to be on the safe side).

Two problems arise:

1) No automatic connection: The phone does not establish a connection automatically to any of the SSIDs.

2) Adds new SSID profiles for existing networks: If I try to connect manually, entering the WIFI-setup and selecting one of the SSIDs, the phone does not use one of the pre-existing profiles. Instead, it makes a new profile in the system-connections folder (the long file names that also contain the UUID are those made by the phone):

[I]wlan1
wlan1-****uuid****
wlan2
wlan2-****uuid****
wlan3[/I]

In the user interface, it prompts me for a network password. Moreover, when looking at Previous Connections in the Network Setup on the phone, the wlan1, wlan2 and wlan3 are not visible. As Network Manager ingnores files that are not chmod 600 (read and write by the owner only). I have checked the file permissions and they seem to be correct:
[I]
-rw------- 1 root root  417 May 23 14:13 wlan1
-rw------- 1 root root  316 May 23 15:03 wlan1-****uuid****
-rw------- 1 root root  425 May 24 12:32 wlan2
-rw------- 1 root root  306 May 24 12:40 wlan2-****uuid****
-rw------- 1 root root  407 May 23 14:12 wlan3[/I]

Two questions:

1) How do I get the phone to use the predefined static profiles.

2) Is this behavior a bug?

Sample profile (wlan2) listing:
```

[connection]
id=wlan3
uuid=****uuid****
type=802-11-wireless

[802-11-wireless]
ssid=wlan3
mode=infrastructure
mac-address=**:**:**:**:**:**
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
auth-alg=open
psk=************

[ipv4]
method=manual
address1=10.0.0.71/255.255.255.0,10.0.0.1
dns=213.60.205.175,213.60.205.173

[ipv6]
method=ignore

```

---

### Post by ElToro on 2015-05-24
Solved it! Steps to fix:

1) Try to connect to the wlan. Fill in password when prompted.
2) Disconnect and switch off wifi in *Settings*.
3) Use *adb shell* and go to */etc/NetworkManager/system-settings*
4) Edit the profile with vi, that is, *sudo vi profile-file-name*
5) Edit the profile to correspond to a static one or, even better, copy in an existing working profile (but changing MAC etc to fit the device). Example:

```

[connection]
id=wlan2
uuid=****uidd***
type=802-11-wireless

type=802-11-wireless

[802-11-wireless]
ssid=wlan2
mode=infrastructure
mac-address=the-mac-address
seen-bssids=eventual-seen-bssids;eventual-other-seen-bssids;
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
psk=your-network-password

[ipv4]
method=manual
dns=your.dns.ip;your.eventual.dns2.ip;
address1=your.static.network.ip/your.network.mask,your-network-gateway
may-fail=false

[ipv6]
method=ignore

```

6) Save the profile (:wq in vi/vim).
7) Restart wifi. The phone connects automatically to the network.

Beats me why this works and the other way doesn't...:p

---

