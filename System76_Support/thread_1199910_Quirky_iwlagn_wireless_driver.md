---
title: "Quirky iwlagn wireless driver"
date: 2009-06-29
forum: System76 Support
---

### Post by akwala on 2009-06-29
Serval Performance, bought in May 2008.

Current system:

[LIST]
[*]Ubuntu 9.04 amd64
[*]Kernel 2.6.28.13-generic w/ linux-backports-modules-jaunty & linux-restricted-modules-generic
[*]System76 driver 2.3.6
[/LIST]
# lspci | grep -i network
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

Problem: "Wireless disabled by radio killswitch" -- I tried to turn the killswitch OFF (i.e., enable wireless) by [following this]("http://knowledge76.com/index.php/Hand-configuring_wireless_networking"), but it didn't work...[INDENT]# iwconfig wlan0                                                                
wlan0     IEEE 802.11abg  ESSID:""                                              
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated       
          Tx-Power=14 dBm                                                       
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B                 
          Encryption key:off                                                    
          Power Management:off                                                  
          Link Quality:0  Signal level:0  Noise level:0                         
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0              
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0              


# iwconfig wlan0 essid "mySSID"                                              

# iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"mySSID"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm                                                   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B             
          Encryption key:off                                                
          Power Management:off                                              
          Link Quality:0  Signal level:0  Noise level:0                     
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0          


# iwlist wlan0 scan                                                             
wlan0     Interface doesn't support scanning : Network is down                  


# ifconfig wlan0 up                                                             

# iwlist wlan0 scan                                                             
wlan0     Failed to read scan data : Resource temporarily unavailable

[/INDENT]I've attached an excerpt of the syslog after startup, showing what happens when NetworkManager tries to activate wlan0.

Any ideas, anyone?

---

### Post by akwala on 2009-06-29
This and other quirks have been reported by many folks, see links below.

I fixed it, I believe, by installing the latest [stable compat-wireless]("http://wireless.kernel.org/en/users/Download/stable/") drivers.

[https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/348275](https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/348275)
[http://ubuntuforums.org/showthread.php?t=1176117](http://ubuntuforums.org/showthread.php?t=1176117)
[http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)
[https://bugs.launchpad.net/ubuntu/jaunty/+source/hal/+bug/193970](https://bugs.launchpad.net/ubuntu/jaunty/+source/hal/+bug/193970)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/313854](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/313854)

---

### Post by thomasaaron on 2009-06-30
Do you have, or have you ever had Windows installed on this machine, dual-booted or otherwise?

If so, you need to go into Windows and enable the wireless switch. Then it will be enabled in Ubuntu. Windows seems to actually modify some settings in the wireless switch's firmware.

---

### Post by Futurian on 2009-07-08
Where in Windows is the wireless switch? I'm traveling, installed XP Pro in Virtualbox 2.2.4, and can't connect wirelessly.

Thanks!

---

### Post by thomasaaron on 2009-07-08
Futurian, based on our email exchange, you're good to go, right? Range problem?

Akwala, I don't think Windows in VBox would do this, as it would not need the wireless switch driver or touch the firmware. Could you please send me an email (support-at-system76-dot-com) with your order number? I need to have a look at your configuration.

---

### Post by Futurian on 2009-07-08
Yes, thanks to your help, I've got wireless connectivity now. Thanks!

---

