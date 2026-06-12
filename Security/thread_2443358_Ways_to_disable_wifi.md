---
title: "Ways to disable wifi"
date: 2020-05-14
forum: Security
---

### Post by smith73 on 2020-05-14
I have wi-fi disabled in BIOS on both ASUS and HP notebooks (with Ubuntu 16-18.04), so iwconfig shows no wireless extensions and <rfkill list/block all> outputs nothing. (Though a UNIX security tool Tiger gave a "fail" for rfkill having read premissions for other.)

What are any other ways to disable wifi reception on top of that?

---

### Post by ajgreeny on 2020-05-14
Using Xubuntu wityh the network-manager icon in panel you can click on that icon and choose "Disable wifi" if I remember correctly; I'm on an ethernet connected machine at present with no wifi available so can not check right now, but will look later and report back.

EDIT:
I'm now back on my laptop with wifi and I was almost correct; it's a tick-box with "Enable Wi-Fi" so remove the tick selection.
I'm not sure if this deselection will survive a reboot, so try it out.

I suspect there are other ways to stop wifi, but I have never needed to do so and it's therefore not something I've ever investigated.

---

### Post by EuclideanCoffee on 2020-05-14
This is how you would turn it off from terminal.

```

nmcli radio wifi off


```

Then try disabling the modprobe permanently in this file configuration.

in: 
**/etc/modprobe.d/wifi-blacklist.conf**
```

blacklist brcmfmac
blacklist brcmutil

```

Reboot and see if wifi is still flagged in your tool.

---

### Post by smith73 on 2020-05-15
After disabling wifi and wwan from nmcli there are still enabled HW devices:

WIFI-HW  WIFI      WWAN-HW  WWAN     
enabled  disabled     enabled      disabled 

There is no such file **wifi-blacklist.conf **in this directory. And <nmcli device wifi> outputs no wifi devices active.

Why does this happen even after I disabled wireless and bluetooth in BIOS?

---

### Post by EuclideanCoffee on 2020-05-15
I don't have enough information on why it is detectable after you disabled from BIOS. You could try removing it physically. 

First try disabling wifi from kernel module.

You must add that file before you can test.

[B]/etc/modprobe.d/wifi-blacklist.conf

Try running this command and then reboot.

```


[/B][FONT=Arial]sudo systemctl restart systemd-modules-load.service

[/FONT]
```[FONT=Arial]

[/FONT]
[FONT=inherit]
[/FONT]

---

