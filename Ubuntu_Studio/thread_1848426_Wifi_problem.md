---
title: "Wifi problem"
date: 2011-09-22
forum: Ubuntu Studio
---

### Post by ketzelleshelle on 2011-09-22
I installed Ubuntu Studio and I can not access the wifi connection.
I want to clarify that Ubuntu Natty Narwhal previously had no problems.

[http://i689.photobucket.com/albums/v...n/7526182c.jpg](http://i689.photobucket.com/albums/v...n/7526182c.jpg)

I linked an image to see that the options are grayed out can not access them.

Needless to say I set the connection properly.

Thank you in advance!

---

### Post by maul9999 on 2011-09-22
> **ketzelleshelle said:**
> I installed Ubuntu Studio and I can not access the wifi connection.
I want to clarify that Ubuntu Natty Narwhal previously had no problems.

[http://i689.photobucket.com/albums/v...n/7526182c.jpg](http://i689.photobucket.com/albums/v...n/7526182c.jpg)

I linked an image to see that the options are grayed out can not access them.

Needless to say I set the connection properly.

Thank you in advance!

What is model of your wifi?

---

### Post by ketzelleshelle on 2011-09-22
> **maul9999 said:**
> What is model of your wifi?

Dell Wireless 1395 WLAN Mini-Card
Marvell Yukon 88E8040 PCI-E Fast Ethernet Controller

---

### Post by maul9999 on 2011-09-22
> **ketzelleshelle said:**
> Dell Wireless 1395 WLAN Mini-Card
Marvell Yukon 88E8040 PCI-E Fast Ethernet Controller

Hmm... Do your Driver Dell (that's come with your laptop) have wireless driver?  If so, look for .inf (.inf on end of title file.) then let me know.

---

### Post by ketzelleshelle on 2011-09-22
> **maul9999 said:**
> Hmm... Do your Driver Dell (that's come with your laptop) have wireless driver?  If so, look for .inf (.inf on end of title file.) then let me know.

Sorry but i don't know what a .inf is or what exactly do you want me to do.

Anyway, i never had problems with previously Ubuntu versions or Windows and the network connections,,,

---

### Post by maul9999 on 2011-09-22
> **ketzelleshelle said:**
> Sorry but i don't know what a .inf is or what exactly do you want me to do.

Anyway, i never had problems with previously Ubuntu versions or Windows and the network connections,,,

Do you mean you never have problem with network connections on previously Ubuntu versions and Windows?  I'm try to understand English.

---

### Post by jejeman on 2011-09-22
ketzelleshelle, give us the output from 
```
sudo lshw -C network
```

---

### Post by ketzelleshelle on 2011-09-22
> **jejeman said:**
> ketzelleshelle, give us the output from 
```
sudo lshw -C network
```

[http://i689.photobucket.com/albums/vv259/linkimagen/8d38cf45.jpg](http://i689.photobucket.com/albums/vv259/linkimagen/8d38cf45.jpg)

[http://i689.photobucket.com/albums/vv259/linkimagen/0b15a866.jpg](http://i689.photobucket.com/albums/vv259/linkimagen/0b15a866.jpg)

---

### Post by jejeman on 2011-09-23
Isn't it easier to just copy/paste text from terminal, than to take pictures with camera?
You should never post pictures just to show text. You should always copy text from terminal and put it in the CODE tags. That way its much more easier for us to see, and also it is searchable.

You don't have firmware installed for your broadcom wifi card. Use jockey-gtk to install driver for this card. It will automaticly install driver and firmware.

---

### Post by ketzelleshelle on 2011-09-23
I have to install jockey-gtk from terminal or...?
Just in case, remember i have not internet access. 

Sorry for the pictures, i guess i learned a new lesson here...

Thanks jejeman!

---

### Post by jejeman on 2011-09-23
The best way is if you can get internet acess, because the proces is automated.
jockey-gtk is already installed.
If you can't have internet access on linux, manuall instalation can be tricky, personally I didn't have sucess with it.

You need to download a firmware, and install b43-fwcutter package.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43)

read the part: b43 - No Internet access

If you can't find the package on install cd, you can find it on package servers.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by briandeyoung on 2011-09-23
I am also having a problem getting my wireless to work.  I have an HP Pavilion dual boot Windows 7 / Ubuntu_Studio.  I tried jockey-gtk   "no proprietary drivers are in use on this system."  
I tried network-admin  to enable the wireless, but it still doesn't work.  Any idea what I am missing?  
Thanks,
Brian

---

### Post by maul9999 on 2011-09-24
> **briandeyoung said:**
> I am also having a problem getting my wireless to work.  I have an HP Pavilion dual boot Windows 7 / Ubuntu_Studio.  I tried jockey-gtk   "no proprietary drivers are in use on this system."  
I tried network-admin  to enable the wireless, but it still doesn't work.  Any idea what I am missing?  
Thanks,
Brian

You will have to get driver from website.  That driver should be folder or zip, then look for .inf.  Then use your Ubuntu CD to installing NDSI.  That program is a driver finder and it use .inf.  You need have .inf file to make wireless working.

---

### Post by jejeman on 2011-09-24
briandeyoung, you need to say which card you have. Give us the output from
```
sudo lshw -C network
```

---

### Post by ketzelleshelle on 2011-09-24
> **jejeman said:**
> The best way is if you can get internet acess, because the proces is automated.
jockey-gtk is already installed.
If you can't have internet access on linux, manuall instalation can be tricky, personally I didn't have sucess with it.

You need to download a firmware, and install b43-fwcutter package.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43)

read the part: b43 - No Internet access

If you can't find the package on install cd, you can find it on package servers.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Succesful!!!
Thank you so much jejeman!

---

### Post by briandeyoung on 2011-09-24
Centrino Wireless-N 1000

logical name: wlan0

configuration: broadcast=yes
driver=iwlagn
link=yes
wirless=IEEE802.11bg

I am hoping I gave enough information.

Thanks for the help!

---

### Post by jejeman on 2011-09-24
I don't see why you didn't just copy/paste the whole output.

Looks like that you have driver, and that the card is working.
Did you turn on the anthenna on the laptop?
What is the output from
```
iwlist wlan0 scan
```

---

### Post by briandeyoung on 2011-09-24
```
[LIST=1]
[*]  *-network
[*]       description: Ethernet interface
[*]       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
[*]       vendor: Realtek Semiconductor Co., Ltd.
[*]       physical id: 0
[*]       bus info: pci@0000:01:00.0
[*]       logical name: eth0
[*]       version: 06
[*]       serial: 10:1f:74:12:b2:81
[*]       size: 100MB/s
[*]       capacity: 1GB/s
[*]       width: 64 bits
[*]       clock: 33MHz
[*]       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
[*]       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
[*]       resources: irq:44 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
[*]  *-network
[*]       description: Wireless interface
[*]       product: Centrino Wireless-N 1000
[*]       vendor: Intel Corporation
[*]       physical id: 0
[*]       bus info: pci@0000:07:00.0
[*]       logical name: wlan0
[*]       version: 00
[*]       serial: 8c:a9:82:a3:b6:a2
[*]       width: 64 bits
[*]       clock: 33MHz
[*]       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
[*]       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-30-generic firmware=128.50.3.1 build 13488 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
[*]       resources: irq:46 memory:c4500000-c4501fff
[*]brian@ubuntustudiohp:~$ ^C
[*]brian@ubuntustudiohp:~$
[*]brian@ubuntustudiohp:~$ iwlist wlan0 scan
[/LIST]
wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:75:2A:37
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"Is Comcast working?"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000127360c580
                    Extra: Last beacon: 1580ms ago
                    IE: Unknown: 0013497320436F6D6361737420776F726B696E673F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E1003FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070100000000000000000000000000000000000000
          Cell 02 - Address: 00:18:E7:EF:DF:34
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"249"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f55b67bc3a
                    Extra: Last beacon: 1750ms ago
                    IE: Unknown: 0003323439
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD770050F204104A0001101044000102103B00010310470010000000000000100000000018E7EFDF3410210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363535104200046E6F6E651054000800060050F2040001101100074449522D363535100800020084103C000103
          Cell 03 - Address: 68:7F:74:AF:0C:58
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"MyValet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000796c3c129d
                    Extra: Last beacon: 1810ms ago
                    IE: Unknown: 00074D7956616C6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD670050F204104A00011010440001021041000100103B00010310470010FD6D2C363B16F91C0DC151B53DB2D0BD102100074C696E6B737973102300034D3230102400063132333435361042000234321054000800060050F2040001101100034D3230100800020084
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000
          Cell 04 - Address: 00:1E:2A:02:2F:42
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Saturn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c0304b181
                    Extra: Last beacon: 9190ms ago
                    IE: Unknown: 000653617475726E
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0900037F0101000EFF7F
                    IE: Unknown: DD1A00037F0301000000001E2A022F42021E2A022F4264002C010E08

I hope this is more complete.  I am sorely out of date with Linux.  I used to use Unix, but now I guess I am a newbie again... Sorry, if I fail to include something, but some commands have changed (not like I would remember them anyway...)

Thanks again for your expert help!
```

---

### Post by jejeman on 2011-09-25
Youre wifi card is working full.
Driver is loaded. Card is scanning and registers networks.

Did you try to make a new network connection i network manager?

I really don't see the problem here. Please elaborate more, how wifi don't work.

what version of ubuntu are you using?
```
lsb_release -a
```
```
uname -r
```

---

### Post by briandeyoung on 2011-09-25
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

2.6.35-30-generic

 I ran updates though, so I thought I would be natty narwhale...
I guess that didn't take
I started with Ubuntu Studio 10.10 (64 install)

Thanks again for your time!

Brian

---

### Post by briandeyoung on 2011-09-25
I did try to make a new connection in network-admin
I am able to connect "wired" but wireless won't connect.  I added the name of the connection and the password.  I tried adding the static address of the server and that didn't seem to work.  I think it must be something simple that I just somehow am missing ...  the wireless button keeps changing between red and blue (on and off).  So maybe it keeps getting kicked off?  I don't have this problem in Windows.

I just set another laptop (ASUS) dual boot Windows 7 and Ubuntu Studio and that one won't connect wired either...  I just wanted to set them all up the same to avoid subtle issues between systems.

---

### Post by briandeyoung on 2011-09-25
OK, back to the ASUS laptop that won't connect at all.  I keep getting this error when I try to add a connection or enable a type of connection:

(network-admin:2674): Gtk-WARNING  **: Failed to set text from markup due to error parsing markup: Error on line 2 char 33: Element 'b' was closed, the currently open element is 'markup'

I really appreciate all this help and your time.  Thank YOU, jejeman!  and anyone else who wants to help!

Brian

---

### Post by ketzelleshelle on 2011-10-20
> **jejeman said:**
> The best way is if you can get internet acess, because the proces is automated.
jockey-gtk is already installed.
If you can't have internet access on linux, manuall instalation can be tricky, personally I didn't have sucess with it.

You need to download a firmware, and install b43-fwcutter package.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43)

read the part: b43 - No Internet access

If you can't find the package on install cd, you can find it on package servers.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Jejeman, i have the same problem again in 11.10. May i have to proceed in the same way?
Thanks!

---

### Post by jejeman on 2011-10-20
Did you upgraded or installed clean from cd?

---

### Post by ketzelleshelle on 2011-10-20
> **jejeman said:**
> Did you upgraded or installed clean from cd?

Clean.

---

### Post by jejeman on 2011-10-21
If you, again, can't connect thru ethernet, then do the same procedure.

---

### Post by ketzelleshelle on 2011-10-21
> **jejeman said:**
> If you, again, can't connect thru ethernet, then do the same procedure.

But now i have a problem (it didn't happen previously):
The button "install" in b43-fcutter and in patch appears in grey, and i can't click it to install...

---

### Post by jejeman on 2011-10-21
Use the terminal. Run commands
```
sudo dpkg -i b43-fwcutter*
```
```
sudo dpkg -i b43-fwcutter*
```Or whatever the names of the packages are.

---

### Post by ketzelleshelle on 2011-10-21
> **jejeman said:**
> Use the terminal. Run commands
```
sudo dpkg -i b43-fwcutter*
```
```
sudo dpkg -i b43-fwcutter*
```Or whatever the names of the packages are.

It returns me "file or directory doesn't exist"

''''''''''''''''''''''''''''''''''''''''''''''''''''

Done! I made it using the command

```
sudo apt-get install
```

Why this?

---

### Post by jejeman on 2011-10-21
In order for dpkg to work, working directory must be the same as where the file is.
As for the apt, maybe because the cd is one of the repositories. If you had your cd mounted then this could be it.

---

