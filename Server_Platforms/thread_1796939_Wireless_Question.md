---
title: "Wireless Question"
date: 2011-07-04
forum: Server Platforms
---

### Post by adam35413 on 2011-07-04
I am trying to setup wireless for an old box I reclaimed recently.  I just installed 11.04 Server, and everything works except the wireless (which is common from what I can read on forums).  I am going through the process of installing ndiswrapper using this [guide]("http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/").  

I am not able to get any scan results when I try to find my access point.  I have noticed that my iwconfig output is different than most guides I have seen, namely that it is missing information about the link quality:


```
wlan0     IEEE 802.11bg  ESSID:"myssid"
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

I have a D-Link AirPlus G DWL-G510 and have installed the neta3ab driver; ndiswrapper -l output looks like:

```
neta3ab : driver installed
        device (168C:001A) present (alternate driver: ath5k)
```

Edit: I have been able to get my wireless to work, but I have to do an ifdown/ifup on the wireless interface everytime I reboot.  I followed the following guide: [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide)

---

