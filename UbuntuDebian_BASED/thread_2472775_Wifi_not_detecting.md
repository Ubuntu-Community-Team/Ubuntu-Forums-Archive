---
title: "Wifi not detecting"
date: 2022-03-12
forum: Ubuntu/Debian BASED
---

### Post by devilmaycryyyy on 2022-03-12
So i have pop os installed on my pc.i have an usb adapter which works out of the box but the main problem i am facing is that it doesn't show detect my android tablet hotspot connection.it shows all other wifi my other android phone hotspot but i don't it doesn't show my Lenovo tablet wifi.it sometime show mostly it doesn't show it.so can u help me fix this problem.

---

### Post by jeremy31 on 2022-03-12
Moved to Ububtu/Debian based

---

### Post by mIk3_08 on 2022-03-12
> **devilmaycryyyy said:**
> So i have pop os installed on my pc.i have an usb adapter which works out of the box but the main problem i am facing is that it doesn't show detect my android tablet hotspot connection.it shows all other wifi my other android phone hotspot but i don't it doesn't show my Lenovo tablet wifi.it sometime show mostly it doesn't show it.so can u help me fix this problem.
Try this command below and post the result here in thread.
```
nmcli general
```
```
nmcli dev status
```
```
nmcli dev wifi list
```
```
nmcli dev wifi list
```
```
sudo iwconfig wlp2s0
```

---

### Post by devilmaycryyyy on 2022-03-12
piyush@pop-os:~$ nmcli general
STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
connected  full          enabled  enabled  enabled  enabled


piyush@pop-os:~$ nmcli dev status 
DEVICE           TYPE      STATE        CONNECTION  
wlx7cc2c617d18a  wifi      connected    hackforlulz 
enp2s0           ethernet  unavailable  --          
lo               loopback  unmanaged    --


IN-USE  BSSID              SSID         MODE   CHAN  RATE       SIGNAL  BARS  SECURITY 
*       4C:49:E3:74:20:D5  hackforlulz  Infra  6     44 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2


wlx7cc2c617d18a  IEEE 802.11bgn  ESSID:"hackforlulz"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 4C:49:E3:74:20:D5   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-****-****   Security mode:open
          Power Management:off
          Link Quality=0/100  Signal level=-82 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by mIk3_08 on 2022-03-13
okay disable wifi for 3 minutes. Then enable it, once it started to detect SSID wifi names run again this command below.
```
nmcli dev wifi list
``` Good luck and cheers.

---

