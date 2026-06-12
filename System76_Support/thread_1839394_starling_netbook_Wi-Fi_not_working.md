---
title: "starling netbook Wi-Fi not working"
date: 2011-09-05
forum: System76 Support
---

### Post by nyx14850 on 2011-09-05
Hi, I am running 10.04 lucid lynx on my starling netbook. I am connected  the internet via wired ethernet. I would like to be able to use  wireless networks but my machine will not detect any of them. The wi-fi  LED is lit up. 

ifconfig returns this for the wlan0 :

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:91:bc:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig returns:

wlan0     802.11b/g  Mode:Managed  Frequency=2.417 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Also, no wireless icon appears on my toolbar. Why does it not  automatically detect the wireless networks? I only have an icon with an  up and down arrow which shows the wired ethernet connection. Am I  missing drivers?

Thanks,
Adam

---

