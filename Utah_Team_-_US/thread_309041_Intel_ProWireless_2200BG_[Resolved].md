---
title: "Intel Pro/Wireless 2200BG [Resolved]"
date: 2006-11-29
forum: Utah Team - US
---

### Post by Frijolie on 2006-11-29
Hey all,

I'm new to this forum and didn't even know a Utah LUG existed! Well, that's good news for all of us. 

I'm a Linux newbie (today is my Linux debut) and am experiencing my first roadblock.

I'm having difficulty getting my Ubuntu (Eggy) box to connect to the 'net with my Intel Pro/Wireless 2200BG wifi card. I've googled and read numerous HOW-TOs without any success. There's so much information out there that it's hard to tell which is the right one to go with. 

I don't know where to start or what information you'll need to help me fix this speedbump, so please be patient.

Where do we start?

Thanks in advance for all of your help.

Frijolie
Holladay, UT

---

### Post by Frijolie on 2006-11-29
with some more googling, I found some frequently requested outputs. Here they are and hope they help...

```

brian@brian-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

and

```

brian@brian-laptop:~$ sudo lshw -C network
Password:
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:5a:c2:1f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.105 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:4000-40ff iomemory:d0201800-d02018ff irq:217
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:c9:05:db
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=unassociated
       resources: iomemory:d0200000-d0200fff irq:225


```

Hope this has helped..

---

### Post by drr422 on 2006-11-29
Well, first of all welcome to the Ubuntu community!

Are you trying to connect to a WEP secured router or a WPA secured router?  If you are trying to connect to a WEP secured router, then you should go to System->Administration->Networking, where you should see your 'wireless connection.'  It should be there, since your eth1 connection is showing wireless stuff.  There you can click properties and enter your router info ( SSID, and ASCII passphrase ( or Hex 64 or 128 key ) and it should configure it for you.  A program i like to use is wifi-radar, it makes automatic switching between wireless profiles a very easy task.  You should give it a try after you get everything working.
I'm not totally sure how to connect to WPA with edgy, but i just got it working tonight on dapper, so you might need to look around a little.  

I hope this helps, and let me know if i can help out anymore.

---

### Post by Frijolie on 2006-11-29
thanks for trying to help...

I'm using WPA+PSK 128bit security. I installed gtkwifi-1.09 and when I mouse over the icon in the 'notification area' it says "X amount of networks" (where  X is the amount of wireless networks available) but when I click on the icon it doesn't show any wireless networks in the window.

I've typed in my SSID and passkey manually in System --> Administration --> Networking and it doesn't connect. Hmmmm..I don't know where to go from here..

---

### Post by peanut butter on 2006-11-29
I dont live in Utah, but i use wifi-radar for my wifi. I dont know if it supports WPA-PSK though.

---

### Post by llamashoes on 2006-11-29
Edgy does not support WPA out of the box, however it is an easy fix. Here is the link that I used to get it working. I have the same card in my laptop.
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Let us know how it goes.

---

### Post by Frijolie on 2006-11-29
thanks llamashoes! that worked! I swear I tried that same tutorial before and it didn't do anything for me..however, now that I remember when I commented out the previous lines in /etc/network/interfaces I used double slashes ('//') instead of pound signs ('#'). I guess that's what made the difference this time. Thanks for everyone's help on this one..Hurray!

---

### Post by drr422 on 2006-11-30
I'm glad that it worked out for you, when I get around to solving a vmware issue I'm having with Edgy, then ill upgrade and probably use that nice tutorial.

---

### Post by llamashoes on 2006-11-30
I'm glad it worked!

---

### Post by rubykj on 2007-03-09
> **llamashoes said:**
> Edgy does not support WPA out of the box, however it is an easy fix. Here is the link that I used to get it working. I have the same card in my laptop.
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Let us know how it goes.


I tried this method in the link. I also have the same card and problem. However when I tried to install network-manager-gnome i got an error: Dependency is not satisfiable : libnm-util0
DO you know anything about this?
Thanks

---

### Post by RottenMutt on 2007-12-03
> **llamashoes said:**
> Edgy does not support WPA out of the box, however it is an easy fix. Here is the link that I used to get it working. I have the same card in my laptop.
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Let us know how it goes.
:)
thanks for the link, it worked for me on my iwill dpmax with a Intel wireless 2200BG running Ubuntu 7.1 64bit.

---

### Post by munishvit on 2009-05-03
bump

---

### Post by albertz on 2009-05-11
Is this up-to-date? I have the same network card, just did a clean installation of Ubuntu 9 and the WLAN interface is just not available.

The network manager says that wireless networks are not activated. When I rightclick it, the option to activate the wireless network is grey and not clickable. Why?

In console, I see the eth1 interface with iwconfig.

---

### Post by theonhighgod on 2009-07-17
I have a similar problem to you albertz in 8.10 so I upgraded to 9.04 still having a similar problem,

It is found in ifconfig, when i run "iwlist scan" it says no scan results, but it is working. 

To make things a little more complex i got this card out an old dead dell and put it in my packard bell (not that brands are important) and i think that the enable wireless button in the dell sends a message to it and tells it to turn on and obviously i don't have one (well not one that works), Now i have seen a hack around this a year or so back i will go on a search and if i figure out repost.

If you happen to ever sorted this problem please let me know....

---

### Post by hub_cap on 2009-07-19
> **albertz said:**
> Is this up-to-date? I have the same network card, just did a clean installation of Ubuntu 9 and the WLAN interface is just not available.

The network manager says that wireless networks are not activated. When I rightclick it, the option to activate the wireless network is grey and not clickable. Why?

In console, I see the eth1 interface with iwconfig.

My wireless connection is identified as eth1.

---

### Post by theonhighgod on 2009-07-21
I black listed the driver with the intention of trying ndiswrapper. fiddled with a few other cards. Tryied a few things with loading the driver with various options like "radio=1" etc and made a file /etc/modprobe.d/ipw2200.conf, went to bed, woke up turn on the laptop then loaded it manually and it worked! I updated ubuntu, I removed the black listing rebooted and it has worked ever since 

As I write this post I thought I'd just check the file I made (/etc/modprobe.d/ipw2200.conf)

I left it reading as
```

options radio=0

```

So anyway it seems like this issue is indeed resolved...

---

### Post by theonhighgod on 2009-08-11
The problem i had with this card is "iwconfig" was showing my radio was off and "dmesg" reviled my radio frequency kill switch was enabled and pressing the wireless switch did nothing (well it said to set keycode... blah blah which can be summarised to this button doesn't work)

The only work around i could figure was rebooting to windows, always a low point, so I glanced at [http://sourceforge.net/projects/rfswitch/](http://sourceforge.net/projects/rfswitch/) downloaded the tar, and found in the readme just the thing i need! (always read them Readme files before you reply!)

the pbe module!

to turn off wireless run:
```
sudo modprobe pbe5 radio=0
```

But more importantly to turn on
```
sudo modprobe pbe5 radio=1
```

One may need first to remove the module first
```
sudo modprobe -r pbe5
```

Hope this help some one!

To summarise If you have a Packard Bell Laptop and can't tick the enable wireless box then check out this module, sorry its not free from having to type in the terminal

---

### Post by brookie on 2009-08-11
Hi guys. I have this same card and I'm running Intrepid. The wifi worked out of the box, but I have a question kind of related to something mentioned above. 

When I was running winxp on this machine, I could open the wireless driver and it had all kinds of settings, like turn wifi on, power mgmt for the wireless card, also something like a sleep when idle or something. 

What commands can I run (or what config file are they in) to see what all those settings are set to without making any changes. I just want to learn and check it out. 

Cheers,
brookie

---

### Post by theonhighgod on 2009-08-13
to get in these details there's not a handy gui i know of, but if you open the terminal or konsole in kde, there's various commands that can help u with wireless configuration, they start "iw" so type iw then hit "tab" and will show you a list.

The two most useful are ```
iwlist scan
``` that gives details of what signals your computer can connect to and ```
iwconfig
``` which configures your wireless card and shows current setting.

If you want to change things you may have to close a program running in the background called "NetworkManager" this program takes care of all these fiddly little commands, remember that in unix based systems capitals are important unlike in Micro$oft programs. so too kill NetworkManager type:

```
sudo service NetworkManager stop
```

when your done and want to sort it out run :

```
sudo service NetworkManager start
```

If you want to learn more about wireless have a look in synaptic though be careful i once installed a package that uninstalled the NetworkManger package and found i was stuck offline for a bit....

happy hacking!

---

### Post by fevemo on 2010-03-25
Hi, 
some weeks ago my wireless stopped working and I fixed it by adding a # to [COLOR=Red]/etc/modprobe.d/blacklist-ath_pci.conf[/COLOR]

I don't know if that had something to do but today my wireless stopped working and when I restarted my computer it said that wireless was disabled and when I right click the enable wireless option is grey and I can't click it, 

when I run iwlist scan I get this:

```
felipe@felipe-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down
```when I run iwconfig i get this
```

felipe@felipe-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```[COLOR=Navy]
[COLOR=Black]does somebody know what I can do

ps: I'm have Ubuntu 9.10 and my wireless car is Atheros Communications Inc. AR5001 Wireless Network Adapter :(

[/COLOR][/COLOR]

---

### Post by theonhighgod on 2010-04-17
hey, sorry i haven't been replied quicker have you tried:

```
 sudo iwconfig ath0 auto 
```

i noticed your transmission power is set to off and that bit of code would set it to auto

hope this still is'nt bugginh you,

---

