---
title: "Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)"
date: 2016-12-17
forum: Server Platforms
---

### Post by ja.supernak on 2016-12-17
I can't run wifi card:

Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
Subsystem: Lite-On Communications Inc QCA6174 802.11ac Wireless Network Adapter [11ad:0807]
Kernel driver in use: ath10k_pci

interface is down and:
br-lan: port 2(wlan0) entered disabled state
why?

sudo ifconfig wlan0 up
ok
sudo brctl addif br-lan wlan0
can't add wlan0 to bridge br-lan: Operation not supported

Please help

---

### Post by jeremy31 on 2016-12-17
*Thread moved to **Server Platforms**.*

Welcome to the forums, I hope this subforum is a better fit

---

### Post by ja.supernak on 2016-12-17
Welcome :)
I don't now. Maybe :)

---

### Post by Graham_Willis on 2016-12-17
I don't know if it'll help, but perhaps try this:

[http://askubuntu.com/questions/763080/no-wifi-in-qualcom-atheros-ubuntu-16-04-acer-aspire-e-15](http://askubuntu.com/questions/763080/no-wifi-in-qualcom-atheros-ubuntu-16-04-acer-aspire-e-15) : 

Direct firmware load for ath10k/QCA9377/hw1.0/firmware-5.bin failed with error -2

---

### Post by ja.supernak on 2016-12-17
Nope - no change

---

### Post by Graham_Willis on 2016-12-18
Did you do everything according to the instructions on the page I gave the link to? Did you reboot?
What do the commands presented there yield?

---

### Post by jeremy31 on 2016-12-18
Hi Graham_Willis
I don't think it is firmware related as the linux-firmware package has been updated since chili555's answer was made.  It does appear that wlan0 is down for some reason
```
sudo ifconfig wlan0 up
```
Might get it to work but I wonder if it isn't something in /etc/hostapd/hostapd.conf that is causing wlan0 to be down

---

### Post by ja.supernak on 2016-12-18
Before I wrote here, I test many page, but no effect. Always reboot after change config.
In dmesg is ok:
ath10k_pci 0000:01:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 2 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
but wlan0 is down

---

### Post by ja.supernak on 2016-12-18
@jeremy31
I used Atheros Communications, Inc. AR9271 802.11n (USB) on ath_htc driver in AP mode and it's work ok so hostapd.conf is ok (?)
In ath_htc is limit to 7 clients and I must change driver (and wifi card)

What in hostapd can wlan0 down?

In attachment my hostapd.conf (without ssid and wpa_passphrase)

---

### Post by jeremy31 on 2016-12-18
It may be an issue with powersave as the wikidevi ath10k page shows powersave is not supported in the module
```
sudo iwconfig wlan0 power off
```

And there is some config settings for ath10k for hostapd
[https://wireless.wiki.kernel.org/en/users/drivers/ath10k/configuration#hostapd](https://wireless.wiki.kernel.org/en/users/drivers/ath10k/configuration#hostapd)

---

### Post by ja.supernak on 2016-12-18
sudo iwconfig wlan0 power off
do nothing (no answer on console, no error in logs)
if I use hostapd.conf from [https://wireless.wiki.kernel.org/en/users/drivers/ath10k/configuration#hostapd](https://wireless.wiki.kernel.org/en/users/drivers/ath10k/configuration#hostapd) - no change,
if I delete hostapd.conf and reboot ifconfig show wlan0 is up! but I still can't add wlan0 to br-lan.

---

