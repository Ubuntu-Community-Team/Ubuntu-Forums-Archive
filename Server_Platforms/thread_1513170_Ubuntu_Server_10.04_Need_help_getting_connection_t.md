---
title: "Ubuntu Server 10.04 Need help getting connection to router/modem"
date: 2010-06-19
forum: Server Platforms
---

### Post by Kizerkaze on 2010-06-19
I've just started to bring up a server and chose Ubuntu, I have set everything up from the installation process and that when I try to connect to the server through Firefox it doesn't show up. I have come to the conclusion that it must be the router/modem password in which is WPA2-PSK. Please tell me what to do to input that password into the server so it can access my network. An updated tutorial will be appreciated.

Just a heads-up, I cannot re-configure the router/modem due to it being used 24/7 (near to limit of processes). But there is enough processes to be used by the server and nothing else.


Kind Regards


KizerKaze

---

### Post by volkswagner on 2010-06-19
Are you asking how to set up a wireless connection on your server?

If the server is setup, did you ever have internet connection.

If you only have a wireless card run the following and post output.

```
lspci
```

If the wireless adapter is USB connected run:

```
lsusb
```

Then:

```
iwconfig
```

If no wireless extentions are found, you need to get the drivers loaded for your adapter.

and

```
ifconfig
```

The wireless setting go in /etc/network/interfaces:

Sample assuming your adapter is at eth0 maybe wlan0 in your case:

```
auto eth0
iface eth0 inet static
network 192.168.1.1
address 192.168.1.99
netmask 255.255.255.128
wireless-essid nameofyourRouterID
mode managed
channel 8
wireless-key WPAorWEPheyHERE
```

---

### Post by Kizerkaze on 2010-06-19
(Day 1) Thank you Volkswagner for replying, I've done the following two commands: lspci and iwconfig. It has displayed the wireless driver and showed that is it not active meaning not used. 

(Day 2) I am running Ubuntu server 10.04 in a desktop from a USB (Didn't want to effect the C: drive in any way(Boot record)). Also I have followed your instructions and the server has "seen" the router/modem but it has not connected to it. If you would like a small video of my situation shout me out and I will provide you with one.


Kind Regards


KizerKaze

---

### Post by volkswagner on 2010-06-20
To help diagnose a process of elimination is in order.

Perhaps setting the NIC in /etc/network/interfaces to dhcp will help eliminate any errors with ip addressing.  You can do this by commenting out the ip, network, and subnet.  Change the word static to dhcp.

You will need to restart networking after making changes.

```
sudo /etc/init.d/networking restart
```

You may also want to temporarily disable wireless security to see if that is an issue.  Some drivers may not support you mode of security.

---

### Post by Kizerkaze on 2010-06-21
There seems to be nothing really happening with the packets that it's sending out through the intervals 6, 13, 17, 7, 15 and 3. "No working leases in persistent databases - sleeping". Again I've followed the instructions and I have released the security from the router/modem but I cannot do that again, If you give me your email address I can provide you with screenshots of what's happening with the server.


Kind Regards


KizerKaze

---

### Post by volkswagner on 2010-06-21
You can post screen shots here for all to see.

Are you using a GUI on your server?

---

### Post by Kizerkaze on 2010-06-21
If you call a terminal a GUI, *laughs*, nah I'm not, I don't even know how to "activate" it on the server but I know you can use one in a web browser from another computer but I need it to connect to the network first to do that. Considering that I'm running this on a seperate system (Not Virtual) and I have a webcam that is not good enough to sharpen the text, I'll just have to write all the details down like you were looking straight at the screen next to me:

Server@Server:~$ iwconfig
lo:                        no wireless extensions.
eth0:        no wireless extensions.
wlan0:          IEEE 802.11bg   ESSID: "My router/modem"
               Mode:Managed   Access Point: Not-Associated   Tx-Power=20 dBm
               Retry long  limit :7    RTS  thr:off    Fragment thr:off
               Power Management :off

virbr0:     no wireless extensions.

Server@Server:~$ sudo /etc/init.d/networking restart
[sudo] password for Server:
 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1107
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All Rights Reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:11:99:c1:2j:31
Sending on  LPF/wlan0/00:11:99:c1:2j:31
Sending on  Socket/fallback
Error for wireless request "Set Encode" (8B2A)  :
        invalid arguement "My router/modem password"
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All Rights Reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:11:99:c1:2j:31
Sending on  LPF/wlan0/00:11:99:c1:2j:31
Sending on  Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 internal 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 internal 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 internal 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 internal 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 internal 13
No DHCPOFFERS received.
No working leases in persistent databases - sleeping.
ssh stop/waiting
ssh start/running, process 1404

Server@Server:~$

---

### Post by wojox on 2010-06-21
You can't connect with Firefox.
open a terminal and use this

```
aah ###########
```
remove the pond signs and put your Lan IP.

Then comes the password and your a set

---

### Post by Kizerkaze on 2010-06-21
> You can't connect with Firefox.
open a terminal and use this

     Code:
     aah ########### 
remove the pond signs and put your Lan IP.

Then comes the password and your a setHave you even read my comments? 1. It's wireless 2.You can connect to a server with ANY browser if you install an application like myphpaddress

Please re-read my comments and reply until you understand it first.



Kind Regards


KizerKaze

---

### Post by Leppie on 2010-06-21
could you post your dhcpd.conf?

---

### Post by Kizerkaze on 2010-06-21
I've went through the installation process of the connection to the wireless but it appears that I don't have one created, is it essential towards the connection issue?



Kind Regards


KizerKaze

---

### Post by Leppie on 2010-06-21
sorry, i may have misunderstood the first time.
what make/model is the wifi adapter your server is equipped with?

---

### Post by Kizerkaze on 2010-06-21
I has a Atheros AR5001X+ Wireless Network Adapter



Kind Regards


KizerKaze

---

### Post by Leppie on 2010-06-22
could you post the output of the following commands?
```
lshw -c network
lsmod
```

---

### Post by Kizerkaze on 2010-06-22
Sorry guys, I'm a bit busy right now, I will get to the server in a moment, probably tonight.



Kind Regards


KizerKaze

---

### Post by Kizerkaze on 2010-06-24
It's pretty much the same information I've given out beforehand.



Kind Regards


KizerKaze

---

### Post by volkswagner on 2010-06-24
Sorry, but I don't see any output for:

```
lsmod
```

It looks like you may have some errors in you network interfaces file.

```
Error for wireless request "Set Encode" (8B2A) :
invalid arguement "My router/modem password"
```

255.255.255.255 does not seem to me as a correct ip.

```
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 internal 7
```

Where did you get the information to fill out /etc/network/interfaces file?

If you have a second linux box on your lan run 

```
ifconfig
```

This should give you the needed information to fill out the interfaces file.

---

### Post by Kizerkaze on 2010-06-24
Once again, this is ONLY through wireless not LAN. The problem is to connect to the router/modem called OPTUSVA03F32, all the commands you have requested are:

Server@Server:~$ iwconfig
lo:                        no wireless extensions.
eth0:        no wireless extensions.
wlan0:          IEEE 802.11bg   ESSID: "My router/modem"
               Mode:Managed   Access Point: Not-Associated   Tx-Power=20  dBm
               Retry long  limit :7    RTS  thr:eek:ff    Fragment thr:eek:ff
               Power Management :eek:ff

virbr0:     no wireless extensions.

Server@Server:~$ sudo /etc/init.d/networking restart
[sudo] password for Server:
 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1107
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All Rights Reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:11:99:c1:2j:31
Sending on  LPF/wlan0/00:11:99:c1:2j:31
Sending on  Socket/fallback
Error for wireless request "Set Encode" (8B2A)  :
        invalid arguement "My router/modem password"
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All Rights Reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:11:99:c1:2j:31
Sending on  LPF/wlan0/00:11:99:c1:2j:31
Sending on  Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 internal 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 internal 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 internal 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 internal 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 internal 13
No DHCPOFFERS received.
No working leases in persistent databases - sleeping.
ssh stop/waiting
ssh start/running, process 1404

Server@Server:~$

I has a Atheros AR5001X+ Wireless Network Adapter

sudo lshw -c network
*-network:0 DISABLED
description: Wireless Interface
product: Atheros AR5001X+ Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id:0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 01
serial: 00:11:XX:XX:XX:XX (Don't want to spoil it)
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 80211bg
resources: irq:21 memory:fcfe0000-fcfeffff

sudo lsmod
(I'm not going to type them all down so I'll just give the essentials)
mac80211  204922 1 ath5k
ath           7611    1 ath5k
cfg80211   126517  3 ath5k, mac80211, ath
led_class    2864    1 ath5k
mii           4381    1 e100

If you need a specific line please ask, specifically tell me what line you want in a command of the list is too long for me type in.



Kind Regards


KizerKaze

---

### Post by Leppie on 2010-06-24
> **Kizerkaze said:**
> If you need a specific line please ask, specifically tell me what line you want in a command of the list is too long for me type in.
you do realize that if you ssh into your server, you can just use copy and paste?

---

### Post by volkswagner on 2010-06-24
> **Leppie said:**
> you do realize that if you ssh into your server, you can just use copy and paste?


It will be difficult for the OP to ssh into a box without a working NIC.

However there are several other methods to reduce the typing.

Use a usb drive and copy output to text files on the USB drive.  Or, perhaps setup a direct LAN connection with a second PC/Laptop with static IP's so the two can communicate via peer to peer networking.  Provided your wired NIC (eth0) is supported.

kizerkaze,

LAN=local area network...this can be wired or wireless, yes to be more specific WLAN=wireless local area network.

What does this mean? 
```
"My router/modem password"
```

Are you masking the actual content?  I don't think you want "/" character in this field.  I don't think this will work with the passphrase, you may need the actual key.

Perhaps we can try something a little different.

Comment out the specific lines in /etc/network/interfaces, so that wlan0 only had the following two lines.

```
auto wlan0
iface wlan0 inet dhcp
```

Then restart networking:

```
sudo /etc/init.d/networking/ restart
```

```
sudo ifup wlan0
```

```
sudo iwconfig wlan0 essid YOURESSID key YOURKEY channel #
```
Change YOURESSID, YOURKEY and # to match your setup for essid, key and wireless channel number.

```
sudo dhclient wlan0
```

---

### Post by Leppie on 2010-06-25
> **volkswagner said:**
> It will be difficult for the OP to ssh into a box without a working NIC.
maybe i've understood wrong, but i can see an eth0 and from what the op stated i get that he's got wireless issues, so wired is working.

---

### Post by Kizerkaze on 2010-06-25
Volkswagner I'm not a moron, I know what LAN means, secondly, OF COURSE I've masked my personal information such a the password to my network, I don't want excuses, I want answers to whether the problem may lie, even if it's masked, I have put in the correct information in the server towards the network.

Yes, I could connect to the server directly from peer2peer but what good would that do if I want to connect to the network through wireless. Another point is that NOTHING is connected too in ethernet even though you see a eth0 or eth1 and so on.


Kind Regards


KizerKaze

---

### Post by volkswagner on 2010-06-25
> **Kizerkaze said:**
> Once again, this is ONLY through wireless not LAN. 

KizerKaze

From the above lead me to believe you did not understand my post about LAN settings.

I only posted about peer to peer as a tool to reduce typing.  I am only trying to help, and never called you a moron.  I'll shut up now since you are way too smart for me to help.

---

### Post by Kizerkaze on 2010-06-26
> However there are several other methods to reduce the typing.

Use a usb drive and copy output to text files on the USB drive. Or, perhaps setup a direct LAN connection with a second PC/Laptop with static IP's so the two can communicate via peer to peer networking. Provided your wired NIC (eth0) is supported.
 
You don't have to be a smart a$$, I have fully understood your method but it will only be static through the p2p connection instead of using the address through wireless plus if I do that it will use the settings in the LAN and not the WLAN.
 
If you want to help me, then help me. Do not waste my time arguening with me with small talk. If no one is able to help me with connecting the server to my wireless network then I'm closing this post down and erase the server. If the response is what I expect then I will move back to Windows.
 
 
 
Kind Regards
 
 
KizerKaze

---

