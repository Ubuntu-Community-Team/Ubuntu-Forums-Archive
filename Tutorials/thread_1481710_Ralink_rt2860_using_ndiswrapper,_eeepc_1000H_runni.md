---
title: "Ralink rt2860 using ndiswrapper, eeepc 1000H running ubuntu netbook remix 10.04"
date: 2010-05-12
forum: Tutorials
---

### Post by nucleuskore on 2010-05-12
[size=5]**I would like to point out to all visitors that Ubuntu 10.10 supports visible and hidden WPA2-PSK encrypted wireless networks on the eeepc 1000H, out of the box. There is no need to download the backports or any drivers, or fiddle around with ndiswrapper as described in this post.**[/size]

**Background:**
Getting your Ralink rt2860 card to work using ndiswrapper on your eeepc 1000H running ubuntu netbook remix 10.04

I tried various tricks to get my card to work, installed a new kernel, compiled the driver from source. Nothing worked for me. My network is as follows: SSID hidden, WPA, AES encryption
So as a lost resort I tried ndiswrapper and it worked for me, so here goes !

Now this method works with the default kernel you have installed. Mine is 2.6.32-22-generic. And a word of caution before you use this method. I have to disconnect and reconnect 2-3 times through the network applet to initiate the connection, but once it is established it is rock stable. In case it does not connect, you have to right click on the network connection icon, click edit connections and delete the connection listed form the wireless networks, and add it again. I have browsed on this connection for upto an hour without it dropping even once. I have even rebooted my system and can verify that you do not have to do any voodoo to get it working, except for the fact that 2-3 repeat connect/disconnect attempts may be required.

----------------------------------------------------------------------------------
**Update:** Alternate to the above: After the desktop loads disconnect from any wireless network and wait for 3-4 minutes. Then attempt the WPA or WPA2 connection, the wireless card connects IMMEDIATELY, without the need for repeat connection attempts or deleting/reading the station.
----------------------------------------------------------------------------------

**Methodology:**
Connect through a wired connection and open synaptic. Mark, download and install 

[b]ndisgtk
ndiswrapper-utils
ndiswrapper-common[/b]

Download the driver for gigabyte ws30n from [here](http://download.cnet.com/comm-driver-gigabyte-mimobility-v-1-3-1-0-15-zip/3000-2112_4-195830.html) or [here](ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/comm_driver_gigabyte_mimobility_v.1.3.1.0.15.zip). It uses the same chipset. Extract all the files to a folder.

**Click on the network manager applet and disconnect any active wireless connection.** 

On your desktop, click on Accessories->Terminal and run these two commands

[b]sudo ifconfig wlan0 down
sudo rmmod rt2860sta
sudo depmod -a[/b]

On your desktop, click on System, and under administration click on Windows wireless drivers. A nice graphical interface opens up. Click on install a new driver and browse to the folder you extracted the downloaded driver files, and in that folder browse to **drivers/GN-WI30N_WP30N_WS30N_WS30HN_WS31N/WINXP2K** and select the inf file. The driver will then be automatically installed.

You can now click on the network applet icon and configure your wireless network as normal.

**References:**
Thanks to all these great guys for sharing their experience

[list=1][*][http://ubuntuforums.org/showthread.php?t=1086165](http://ubuntuforums.org/showthread.php?t=1086165)[*][http://www.wireless-driver.com/download/gigabyte/gigabyte-gn-ws30n-windows-drivers-utility.htm](http://www.wireless-driver.com/download/gigabyte/gigabyte-gn-ws30n-windows-drivers-utility.htm)[*][https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)[/list]

---

### Post by andreionutz on 2010-05-14
IT JUST WORKS!
I'm a bit disappointed it didn't work out of the box. I tried disabling the ipv6 and installing the native driver from ralinktech but nothing worked. I have wasted a lot of time trying to fix the network after update to 10.04. What's a netbook without net...
Thank you so much for gathering the informations and making this easy and functional howto!
Regards,
Andrei

---

### Post by nucleuskore on 2010-05-15
Thank you for your feedback.

---

### Post by olalaaa on 2010-05-17
Please explain me if that happens with a x64 system, too.

I tried to set my card with Linux driver from Ralink website at no result. Also, using the original CD from my notebook, I tried to use Vista drivers, but I received the message that the drivers are only for 32 bit distribution, not 64 .

Any suggestions ?

Thank you.

One more question : if I try to use the drivers from Win7, where are they located ? (I have dual boot system, Win7 plus Ubuntu 10.04 now)

---

### Post by nucleuskore on 2010-05-17
I suggest you follow my tutorial upto **sudo depmod -a**

**Then...as follows for 64 bit**

On your desktop, click on System, and under administration click on Windows wireless drivers. A nice graphical interface opens up. Click on install a new driver and browse to the folder you extracted the downloaded driver files, and in that folder browse to **drivers/GN-WI30N_WP30N_WS30N_WS30HN_WS31N/WINX64**  and select the inf file. The driver will then be automatically installed.

You can now click on the network applet icon and configure your wireless network as normal.

I am eagerly awaiting your feedback!

---

### Post by kenpbuck on 2010-05-29
Thank you for making my netbook useful again! Your directions were easy to follow and complete. :KS

---

### Post by jkildea on 2010-07-03
Just a note to say thank you very much. Your instructions brought my eeepc back to life :-)

---

### Post by x-shaney-x on 2010-07-04
Did you try using the backport modules?
I noticed mine worked out of the box on my meerkat testing install so I tried installing the meerkat kernel on lucid and internet worked fine (not the recommended way of doing it).

Just thought the backport module might work also.

---

### Post by macakinho on 2010-08-18
Just wanted to let out a big THANK YOU!

Worked perfectly on my 901! :p :D

---

### Post by giantiger on 2010-09-17
> **nucleuskore said:**
> **Background:**
Getting your Ralink rt2860 card to work using ndiswrapper on your eeepc 1000H running ubuntu netbook remix 10.04

I tried various tricks to get my card to work, installed a new kernel, compiled the driver from source. Nothing worked for me. My network is as follows: SSID hidden, WPA, AES encryption
So as a lost resort I tried ndiswrapper and it worked for me, so here goes !

Now this method works with the default kernel you have installed. Mine is 2.6.32-22-generic. And a word of caution before you use this method. I have to disconnect and reconnect 2-3 times through the network applet to initiate the connection, but once it is established it is rock stable. In case it does not connect, you have to right click on the network connection icon, click edit connections and delete the connection listed form the wireless networks, and add it again. I have browsed on this connection for upto an hour without it dropping even once. I have even rebooted my system and can verify that you do not have to do any voodoo to get it working, except for the fact that 2-3 repeat connect/disconnect attempts may be required.

----------------------------------------------------------------------------------
**Update:** Alternate to the above: After the desktop loads disconnect from any wireless network and wait for 3-4 minutes. Then attempt the WPA or WPA2 connection, the wireless card connects IMMEDIATELY, without the need for repeat connection attempts or deleting/reading the station.
----------------------------------------------------------------------------------

**Methodology:**
Connect through a wired connection and open synaptic. Mark, download and install 

[B]ndisgtk
ndiswrapper-utils
ndiswrapper-common[/B]

Download the driver for gigabyte ws30n from [here]("http://download.cnet.com/comm-driver-gigabyte-mimobility-v-1-3-1-0-15-zip/3000-2112_4-195830.html") or [here]("ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/comm_driver_gigabyte_mimobility_v.1.3.1.0.15.zip"). It uses the same chipset. Extract all the files to a folder.

**Click on the network manager applet and disconnect any active wireless connection.** 

On your desktop, click on Accessories->Terminal and run these two commands

[B]sudo ifconfig wlan0 down
sudo rmmod rt2860sta
sudo depmod -a[/B]

On your desktop, click on System, and under administration click on Windows wireless drivers. A nice graphical interface opens up. Click on install a new driver and browse to the folder you extracted the downloaded driver files, and in that folder browse to **drivers/GN-WI30N_WP30N_WS30N_WS30HN_WS31N/WINXP2K** and select the inf file. The driver will then be automatically installed.

You can now click on the network applet icon and configure your wireless network as normal.

**References:**
Thanks to all these great guys for sharing their experience

[LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=1086165](http://ubuntuforums.org/showthread.php?t=1086165)
[*][http://www.wireless-driver.com/download/gigabyte/gigabyte-gn-ws30n-windows-drivers-utility.htm](http://www.wireless-driver.com/download/gigabyte/gigabyte-gn-ws30n-windows-drivers-utility.htm)
[*][https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[/LIST]


THANK YOU, it worked for me.

I have a Hanspree netbook installed Ubuntu netremix. The network adapter is RaLink RT2860. The wireless worked fine until an software update. I didn't realize that it is a driver problem, assumed the newer version should continue to support what has been supported. I tried to fix it for months without success. 

Fortunately, I found your solution from [http://ubuntuforums.org/showthread.php?t=1476007&page=4](http://ubuntuforums.org/showthread.php?t=1476007&page=4). The instruction is very clear.

Again, THANK YOU for the solution.

---

### Post by tincrowdor on 2010-10-23
> **nucleuskore said:**
> **Background:**
Getting your Ralink rt2860 card to work using ndiswrapper on your eeepc 1000H running ubuntu netbook remix 10.04

I tried various tricks to get my card to work, installed a new kernel, compiled the driver from source. Nothing worked for me. My network is as follows: SSID hidden, WPA, AES encryption
So as a lost resort I tried ndiswrapper and it worked for me, so here goes !

Now this method works with the default kernel you have installed. Mine is 2.6.32-22-generic. And a word of caution before you use this method. I have to disconnect and reconnect 2-3 times through the network applet to initiate the connection, but once it is established it is rock stable. In case it does not connect, you have to right click on the network connection icon, click edit connections and delete the connection listed form the wireless networks, and add it again. I have browsed on this connection for upto an hour without it dropping even once. I have even rebooted my system and can verify that you do not have to do any voodoo to get it working, except for the fact that 2-3 repeat connect/disconnect attempts may be required.

----------------------------------------------------------------------------------
**Update:** Alternate to the above: After the desktop loads disconnect from any wireless network and wait for 3-4 minutes. Then attempt the WPA or WPA2 connection, the wireless card connects IMMEDIATELY, without the need for repeat connection attempts or deleting/reading the station.
----------------------------------------------------------------------------------

**Methodology:**
Connect through a wired connection and open synaptic. Mark, download and install 

[B]ndisgtk
ndiswrapper-utils
ndiswrapper-common[/B]

Download the driver for gigabyte ws30n from [here]("http://download.cnet.com/comm-driver-gigabyte-mimobility-v-1-3-1-0-15-zip/3000-2112_4-195830.html") or [here]("ftp://nucleuskore1:EllarigE@dart.ftpcontrol.net/ubuntu/comm_driver_gigabyte_mimobility_v.1.3.1.0.15.zip"). It uses the same chipset. Extract all the files to a folder.

**Click on the network manager applet and disconnect any active wireless connection.** 

On your desktop, click on Accessories->Terminal and run these two commands

[B]sudo ifconfig wlan0 down
sudo rmmod rt2860sta
sudo depmod -a[/B]

On your desktop, click on System, and under administration click on Windows wireless drivers. A nice graphical interface opens up. Click on install a new driver and browse to the folder you extracted the downloaded driver files, and in that folder browse to **drivers/GN-WI30N_WP30N_WS30N_WS30HN_WS31N/WINXP2K** and select the inf file. The driver will then be automatically installed.

You can now click on the network applet icon and configure your wireless network as normal.

**References:**
Thanks to all these great guys for sharing their experience

[LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=1086165](http://ubuntuforums.org/showthread.php?t=1086165)
[*][http://www.wireless-driver.com/download/gigabyte/gigabyte-gn-ws30n-windows-drivers-utility.htm](http://www.wireless-driver.com/download/gigabyte/gigabyte-gn-ws30n-windows-drivers-utility.htm)
[*][https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[/LIST]

a big big thank you for this post as it seems to have resolved my erratic  wifi connection using Ubuntu Netbook remix and Medion Akoya E1210 netbook

---

### Post by cpw919 on 2011-01-23
Thank you Nucleuskore!! I was never going to figure that out. My computer can now work.

---

### Post by unaskedwriter on 2011-07-18
Worked well on my 901. Thank you. You've saved me a lot of time and headaches.

---

### Post by poikiloid on 2011-07-31
Thank you so much for posting this tutorial!!! it worked, and was easier and better than a different one I was trying.

To anyone who has any ubuntu flavor 10.10 or above, I found I DID STILL need this tutorial even though the instructions say it is no longer needed: I have EEE PC 1000 16GB SSD which came with XP, but I installed Lubuntu 11.04, which is snappier than XP on this machine. Wireless worked for a little while, then just would not anymore, until I followed these instructions.

THANKS!!

---

### Post by nucleuskore on 2011-08-01
Hi

Thanks for your feedback. I said that this tutorial is redundant as the card works  fine with the new kernel; I have Ubuntu 11.04 on my eeepc 1000H and I am not using ndiswrapper. However I do note that it takes time too connect to hidden wireless networks, like my network at home, sometimes up to a minute. Anyway you use what works best for you :) Cheers

---

### Post by nowifi on 2012-02-13
Same problem on my machine (HP mini 110).

**1.** Ralink wireless driver (RT3090) does not function with Ubuntu UNR 10.04. (run from Live CD - actually from a Live SD  write locked SD card created as Live USB)
**2.** Once driver is functioning, connections to non-broadcasting SSID routers fail.

These steps **[COLOR=Blue]will make[/COLOR]** the connection ...

**1.** requires:
```

[COLOR=Navy][B]sudo su
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart
exit[/B][/COLOR]
```and
**2.** requires forcing NM (**N**etwork **M**anager) to see the "hidden" network service (it helps to right click NM and  toggle the **Enable Wireless** option off (to disable) & then on again) using```

[COLOR=Blue]**sudo iwconfig wlan0 essid <non-broadcast SSID> key s:<ASCII passcode string>**[/COLOR]
```[B]

1.[/B] The first command sequence fixes: 
 ```

[COLOR=Blue]**dmesg | grep RT**[/COLOR]
[   35.973068] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   35.973078] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[   36.297303] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   36.297312] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[  200.006646] Read file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed(errCode=0)! 
```[B]

2.[/B] The second terminal command is needed in Ubuntu to coerce the protocol connection from Network Manager while Dis/En-abling Wireless Networking.

ref:
*[Re: How To: Manual Network Configuration without the need for Network Manager]("http://ubuntuforums.org/showthread.php?p=11686257#post11686257")*
*[Ubuntu can not connect a wireless RaLink RT3090 to a hidden network]("http://ubuntuforums.org/showthread.php?p=11662679#post11662679")*
*[Re: Can't connect to hidden wireless in Ubuntu 10.10]("http://ubuntuforums.org/showthread.php?p=11664194#post11664194")*

---

