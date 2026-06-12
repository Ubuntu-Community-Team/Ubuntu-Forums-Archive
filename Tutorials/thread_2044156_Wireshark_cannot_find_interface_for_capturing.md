---
title: "Wireshark cannot find interface for capturing"
date: 2012-08-18
forum: Tutorials
---

### Post by BilliardX on 2012-08-18
So I am using an Alfa AWUS036H (RTL8187), which supports monitoring and injection. I am running Ubuntu, and Wireshark and Airodump were working just fine up until today. I was screwing around a bit with ettercap and driftnet doing some MITM on my virtual machine and now my interface isnt listed in Wireshark. When I try to run Airodump, I get this error.

"ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan1 <#>'
Sysfs injection support was not found either."

I had enabled ip forwarding and turned on dhcp, so I don't know if either of those things could be the source of the issue...

Here is my iwconfig:

lo        no wireless extensions.

mon0      IEEE 802.11bg  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wlan1     IEEE 802.11bg  ESSID:"Days Inn"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 58:93:96:0B:7C:D8   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:20  Invalid misc:80   Missed beacon:0

eth0      no wireless extensions.

Thanks!

---

