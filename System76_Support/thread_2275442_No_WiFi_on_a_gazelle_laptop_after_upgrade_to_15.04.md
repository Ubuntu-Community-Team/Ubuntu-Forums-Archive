---
title: "No WiFi on a gazelle laptop after upgrade to 15.04"
date: 2015-04-26
forum: System76 Support
---

### Post by sds57 on 2015-04-26
I just upgraded System76 Gazelle laptop to 15.04 and wifi no longer works.

It sees many network and tries to connect to mine, but fails repeatedly (/var/log/syslog seems to indicate an authentication failure, but the password in the /etc/NetworkManager/.../my-wifi is, of course, correct).

I tried rebooting both the laptop and the wireless model.

I also tried Fn-F11 with weird results: when I hit it once, the LED indicator for wireless goes **on**, but NetworkManager turns WiFi **off**. When I turn WiFi **on** in the NetworkManager, the LED goes **off**.

How do I restore the WiFi?

PS. Same as [http://askubuntu.com/questions/614164/no-wifi-on-a-system76-laptop-after-upgrade-to-15-04](http://askubuntu.com/questions/614164/no-wifi-on-a-system76-laptop-after-upgrade-to-15-04)

---

### Post by racaspercom on 2015-04-26
Did you enable the system76 driver?

sudo apt-add-repository ppa:system76-dev/stable

 		sudo apt-get update
 		sudo apt-get install system76-driver

---

### Post by mtimion on 2015-04-26
having same problem. I have already enabled system76 driver with no luck.

---

### Post by mtimion on 2015-04-26
To anyone reading this in the future, this appears to be an issue with the firmware for the Intel 3160. 

To fix we need to remove the newest firmware and let ubuntu fall back to the older (working) ones.

sudo mv /lib/firmware/iwlwifi-3160-12.ucode /lib/firmware/backup-iwlwifi-3160-12.ucode
sudo mv /lib/firmware/iwlwifi-3160-10.ucode /lib/firmware/backup-iwlwifi-3160-10.ucode

Then reboot.

([https://lists.launchpad.net/kernel-packages/msg114390.html](https://lists.launchpad.net/kernel-packages/msg114390.html))

This has allowed me to connect to my wifi again, but I'll bring my usb connector with me just in case.

---

### Post by Skaperen on 2015-04-27
> **mtimion said:**
> sudo mv /lib/firmware/iwlwifi-3160-12.ucode /lib/firmware/backup-iwlwifi-3160-12.ucode
sudo mv /lib/firmware/iwlwifi-3160-10.ucode /lib/firmware/backup-iwlwifi-3160-10.ucode

did you mean to **mv** to a .bak name? like this ...

```
sudo mv /lib/firmware/iwlwifi-3160-12.ucode{,.bak}
sudo mv /lib/firmware/iwlwifi-3160-10.ucode{,.bak}
```

... ?

---

### Post by jmkowske on 2015-05-15
I believe the poster meant to mv. This effectively removes the file so it will fall back to the default. I had the same problem and that solution worked for me as well.

---

### Post by jlh68 on 2015-06-10
OK what do I do, I just received my new System76 Lemur with 15.04 installed and my WiFi does not work either.  I doubt I have a fall back legacy firmware to go to.
I have tried to duplicate all of the settings from my Acer netbook WiFi to the System76 with no sucess yet in getting the WiFi to connect.  It searches but does not find my WiFi.  It shows my Wifi network and almost a dozen around my home.  So the computer WiFi can find the various wifi networks, it just will not connect.

What gives?

---

### Post by jlh68 on 2015-06-10
I don't know how it happened, but I was using the Ethernet connection and did some new application installs.  I unhooked the cable and tried the WiFi one more time and this time it connected.  The laptop was within 3 feet of the wireless router this time.

---

