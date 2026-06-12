---
title: "How can I prevent Desktop Users from viewing the wireless password?"
date: 2010-12-03
forum: Security
---

### Post by emurad on 2010-12-03
Hi,

The title says it; I want to prevent users from viewing the wireless network password.

Please help. Thanks.

---

### Post by teejaybee on 2010-12-03
Where do you think they are going to view it?

---

### Post by emurad on 2010-12-03
seahorse.

---

### Post by mathgeek2000 on 2010-12-03
Why would you want to? If you have a desktop with a wired connection, you won't need to use it. If a laptop user loses his or her wireless connection, they would have to retype it.

Some routers also allow a guest vpn, which provides an unencrypted Hotspot,and an authorization screen -- (Cisco E3000 is one)

---

### Post by uRock on 2010-12-03
Network Manager requires a password in order to see the profile.
I have never used seahorse, so I have no clue how it works.

---

### Post by gradinaruvasile on 2010-12-03
> **uRock said:**
> Network Manager requires a password in order to see the profile.
I have never used seahorse, so I have no clue how it works.

By default, it does not require a password.
But if you tick the "Available to all users" checkbox, it should ask for your users password if you want to modify the profile. I am not sure if it does if you tick the "show passwords" checkbox though.

---

### Post by uRock on 2010-12-03
> **gradinaruvasile said:**
> By default, it does not require a password.
But if you tick the "Available to all users" checkbox, it should ask for your users password if you want to modify the profile. I am not sure if it does if you tick the "show passwords" checkbox though.
That is how mine is set up.

---

### Post by gradinaruvasile on 2010-12-03
> **uRock said:**
> That is how mine is set up.

But it is not the default behaviour, thats why i mentioned it.

---

### Post by teejaybee on 2010-12-06
Ok.

Then don't set up your wireless connection via the GUI.

Here is how you can do it:

A sample entry from /etc/network/interfaces:

```
auto wlan0
iface wlan0 inet dhcp
    wpa-conf /etc/wpa_supplicant.conf
```A sample /etc/wpa_supplicant.conf:

```
network={
    ssid="YOUR_SSID_HERE"
    scan_ssid=1
    key_mgmt=WPA-PSK
    psk="YOUR_WLAN_PASSWORD_HERE"
}
```Make sure wpa_supplicant.conf is owned by root and chmod 600.

Hope this helps.

---

### Post by emurad on 2010-12-17
> **uRock said:**
> Network Manager requires a password in order to see the profile.
I have never used seahorse, so I have no clue how it works.

Where can I find this app?

Thanks.

---

### Post by emurad on 2010-12-17
> **teejaybee said:**
> Ok.

Then don't set up your wireless connection via the GUI.

Here is how you can do it:

A sample entry from /etc/network/interfaces:

```
auto wlan0
iface wlan0 inet dhcp
    wpa-conf /etc/wpa_supplicant.conf
```A sample /etc/wpa_supplicant.conf:

```
network={
    ssid="YOUR_SSID_HERE"
    scan_ssid=1
    key_mgmt=WPA-PSK
    psk="YOUR_WLAN_PASSWORD_HERE"
}
```Make sure wpa_supplicant.conf is owned by root and chmod 600.

Hope this helps.

This didn't work for me at all. I made it and it was like nothing was changed.

---

### Post by uRock on 2010-12-17
> **emurad said:**
> Where can I find this app?

Thanks.
Right-click the network manager icon shown in the screen shot(it may look different if you are using wireless), then select **Edit Connections...**, then click on the **Wireless Tab**, then double click your current profile, then you will see a box in the bottom left of this window for **Availible to all users**, check that box, click** apply**, then your users will be able to use the wireless without logging into the network and they will not be able to see the password without your admin/root password.

---

### Post by emurad on 2010-12-17
> **uRock said:**
> Right-click the network manager icon shown in the screen shot(it may look different if you are using wireless), then select **Edit Connections...**, then click on the **Wireless Tab**, then double click your current profile, then you will see a box in the bottom left of this window for **Availible to all users**, check that box, click** apply**, then your users will be able to use the wireless without logging into the network and they will not be able to see the password without your admin/root password.

No, YOU rock. Thanks you very much that's exactly what I wanted and more (setting the connection once instead of creating it for each user).

1. Do I have to set the permission for any files/folders or I'm all set now?

2. How can I prevent the same desktop users from connecting to other wireless networks?

Thanks again.

---

### Post by gn0m3boy on 2010-12-17
> Where can I find this app?

Thanks.

If you were previously referring to Seahorse:

Seahorse is already installed.  Click on  Applications --> Accessories -->  "Passwords and Encryption Keys" settings.  That is the 'Seahorse' module.

---

