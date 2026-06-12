---
title: "lost wireless connection"
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kurja on 2012-03-20
Wireless did work after install (beta 1), but no longer. Connecting with my mobile on usb doesn't work etiher.

Last things I did before it stopped working:
-executed ```
sudo apt-get install gnome-shell gnome-session-fallback
```-installed, from the repositories, GIMP and Chromium BSU (that shooter game)
-clicked on that upper right corner button->check for updates, it found a bunch and offered "partial updates" which I didn't go for, and as far as I can tell it didn't install any updates

Overall performance seemed worse than usual somehow, so I booted, after which no more wireless. It keeps trying to connect, but nothing happens. I did also try another wireless adapter, to no avail.

I was going to boot from the 12.04 live cd, but it hung up on splash screen and when I hit ctrl alt F2 it asked for my password - for the username being used on the installed 12.04, but it was 100% unresponsive.

So now I'm running 10.04 from live cd.

Help?

-edit - forgot to mention, I also got "internal error" messages, so something's definitely amiss there. What would you think I should try? I mean, I'd like to try updating to see if these problems would go away, but how would I do that if I can't get online. 8-[

---

### Post by kaldor on 2012-03-20
> **kurja said:**
> Wireless did work after install (beta 1), but no longer. Connecting with my mobile on usb doesn't work etiher.

Last things I did before it stopped working:
-executed ```
sudo apt-get install gnome-shell gnome-session-fallback
```-installed, from the repositories, GIMP and Chromium BSU (that shooter game)
-clicked on that upper right corner button->check for updates, it found a bunch and offered "partial updates" which I didn't go for, and as far as I can tell it didn't install any updates

Overall performance seemed worse than usual somehow, so I booted, after which no more wireless. It keeps trying to connect, but nothing happens. I did also try another wireless adapter, to no avail.

I was going to boot from the 12.04 live cd, but it hung up on splash screen and when I hit ctrl alt F2 it asked for my password - for the username being used on the installed 12.04, but it was 100% unresponsive.

So now I'm running 10.04 from live cd.

Help?

-edit - forgot to mention, I also got "internal error" messages, so something's definitely amiss there. What would you think I should try? I mean, I'd like to try updating to see if these problems would go away, but how would I do that if I can't get online. 8-[

Not a solution, but a word of advice for testing development releases: Never do a partial update unless you are 100% sure of what it does. For this reason, using the graphical update manager is never recommended during the cycle. Use the command "sudo apt-get update && sudo apt-get upgrade" instead. Partial upgrades can haul out packages, potentially damaging the system as you're now experiencing.

I'll let someone more knowledgeable than myself figure out how to restore the wireless. My guess is that in the partial upgrade a wireless package was removed.

Joys of testing, eh? :)

---

### Post by grahammechanical on 2012-03-20
Do you have another install of Ubuntu on this machine, such as 10.04? I guess not otherwise you would not now be using the 10.04 live CD.

Were you able to get a wireless connection with this live CD without installing any wireless drivers?

This is a link to the wireless trouble shooting guide..

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Boot into 12.04 and run some of the commands to collect information and maybe work out what is wrong.

Trouble shooting connection problems is the same whether we are running 12.04 Beta 1 or 11.10 or 10.04. We do not have special ways of fixing these problems in 12.04.

It would also be helpful if you told us the messages that Network Manager gives when it tries to connect. And also what you see when you click the Network Manager icon. And when you open System Settings>Network.

You need to explain what you mean by "nothing happens." This does not give us enough information to advise you. It maybe that this could simply be fixed by you needing to put in your wireless router pass phrase. Who knows?

Regards.

---

### Post by kurja on 2012-03-20
> **kaldor said:**
> Not a solution, but a word of advice for testing development releases: Never do a partial update unless you are 100% sure of what it does. For this reason, using the graphical update manager is never recommended during the cycle. Use the command "sudo apt-get update && sudo apt-get upgrade" instead. Partial upgrades can haul out packages, potentially damaging the system as you're now experiencing.

I'll let someone more knowledgeable than myself figure out how to restore the wireless. My guess is that in the partial upgrade a wireless package was removed.

Joys of testing, eh? :)
Having read a word of caution about the partial updates on these very forums, I didn't click on "partial upgrade" when it was offered, so afaik I didn't upgrade anything.

---

### Post by kurja on 2012-03-20
> **grahammechanical said:**
> Do you have another install of Ubuntu on this machine, such as 10.04? I guess not otherwise you would not now be using the 10.04 live CD.

Were you able to get a wireless connection with this live CD without installing any wireless drivers?

This is a link to the wireless trouble shooting guide..

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Boot into 12.04 and run some of the commands to collect information and maybe work out what is wrong.

Trouble shooting connection problems is the same whether we are running 12.04 Beta 1 or 11.10 or 10.04. We do not have special ways of fixing these problems in 12.04.

It would also be helpful if you told us the messages that Network Manager gives when it tries to connect. And also what you see when you click the Network Manager icon. And when you open System Settings>Network.

You need to explain what you mean by "nothing happens." This does not give us enough information to advise you. It maybe that this could simply be fixed by you needing to put in your wireless router pass phrase. Who knows?

Regards.

Wireless did work "out of the box" in 12.04.  When it's trying to connect, I just get "connecting" with an occasional "disconnected", this goes on and on. Oh, and I have entered the wlan password.

As you guessed I'll have to boot back to 12.04 and then back to 10.04 live cd to report on further findings, as I don't have another version/os installed.

---

### Post by kurja on 2012-03-20
After booting 12.04, I could see my wlan name when clicking on the connection icon near the upper right corner, and it was trying to connect. After a while of trying, I got a disconnected- notification and then the icon disappeared. My wlan router thingy showed a connection on it`s display though.

It did not occur to me before - during install, it asked if I wanted it to update during install, and I chose yes.

```
nm-tool

NetworkManager Tool

State: connecting

- Device: wlan0  [E5832-52ed] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:08:A1:A3:BC:B1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    E5832-52ed:      Infra, 30:87:30:FD:52:ED, Freq 2412 MHz, Rate 54 Mb/s, Strength 97 WPA

```

```
sudo lshw -C network
[sudo] password for k: 
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: Ralink corp.
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: wlan0
       version: 00
       serial: 00:08:a1:a3:bc:b1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=3.2.0-17-generic-pae firmware=0.8 latency=32 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fdcf0000-fdcf7fff
  *-network:1
       description: Ethernet interface
       product: IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY
       vendor: Sundance Technology Inc / IC Plus Corp
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 31
       serial: 00:50:8d:7b:72:c4
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sundance driverversion=1.2 duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:ee00(size=128) memory:fdcfe000-fdcfe1ff memory:fde00000-fde0ffff

```

```
lspci -v

02:06.0 Network controller: Ralink corp. RT2561/RT61 rev B 802.11g
    Subsystem: Ralink corp. Device 2561
    Flags: bus master, slow devsel, latency 32, IRQ 17
    Memory at fdcf0000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: rt61pci
    Kernel modules: rt61pci

```

```
lsmod | grep rt61pci
rt61pci                27493  0 
rt2x00pci              14202  1 rt61pci
rt2x00lib              48858  2 rt61pci,rt2x00pci
eeprom_93cx6           12653  1 rt61pci
crc_itu_t              12627  2 rt61pci,firewire_core
```

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
sudo iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"E5832-52ed"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 30:87:30:FD:52:ED   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

eth0      no wireless extensions.

```

---

### Post by kurja on 2012-03-20
> **grahammechanical said:**
> 

Were you able to get a wireless connection with this live CD without installing any wireless drivers?


Yes, wireless has worked without first installing any drivers. Only now with installed 12.04 it does not work.

---

### Post by kurja on 2012-03-20
Did a reinstall, wireless works. Now I'm not only afraid to update the system, but also to install any programs on it....

edit--did dare to update (apt-get update/upgrade), still works. I'll mark this as solved.

---

