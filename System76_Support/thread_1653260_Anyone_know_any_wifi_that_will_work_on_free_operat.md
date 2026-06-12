---
title: "Anyone know any wifi that will work on free operating systems"
date: 2010-12-26
forum: System76 Support
---

### Post by OpenOS on 2010-12-26
Hi does anyone know any wifi cards that are compatible with my system76 starling netbook as im trying to put trisquel os onto it and i carnt get the wireless to work because the card is apprently proprietory.

---

### Post by Dave_L on 2010-12-26
Is this helpful?

[http://www.fsf.org/resources/hw/index_html/net/wireless/index_html/cards.html](http://www.fsf.org/resources/hw/index_html/net/wireless/index_html/cards.html)

---

### Post by OpenOS on 2010-12-26
i need links to any site that sells them and need to know if its compatible

---

### Post by jml on 2010-12-26
What Starling do you have?  The current Starling ships with a Realtech wireless card. This card's drivers are already in the Linux kernel that Ubuntu ships.  The first Generation Starling ships with a wireless card that has major issues with the stock Linux kernel and requires tthe System 76 drivers to be usable.  If you search this forum, you should find posts about people swapping out the OEM wireless card with an Intel wireless card that has wider support.

Joe

---

### Post by OpenOS on 2010-12-26
it a recent starling i got it for christmas but im wanting the wifi to work on the trisquel operating system

---

### Post by amsterdamharu on 2010-12-26
Could you post the output of the following command? (press alt + F2, type gnome-terminal and click run. Then paste the command in the black window.)

```
sudo lshw -C network
```

---

### Post by OpenOS on 2010-12-26
trisquel@trisquel:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: JMC260 PCI Express Fast Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:14:00.5
       logical name: eth0
       version: 02
       serial: 00:90:f5:a9:42:be
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi  bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd  autonegotiation
       configuration: autonegotiation=on  broadcast=yes driver=jme driverversion=1.0.5 duplex=full ip=192.168.1.9  latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 memory:f0200000-f0203fff ioport:3400(size=128) ioport:3000(size=256)

---

### Post by amsterdamharu on 2010-12-26
There are several realtek drivers available but not your model as far as I can see.
Your model is: RTL8191SEvB

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:PCI](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:PCI)
Not sure if the ndiswrapper will work for you.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The 8192 is supported by kernel 2.6.32 so no drivers are needed.
The 8187SE has ndiswrapper support but not sure about your model.

You could try to download the driver:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SE-VA2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SE-VA2)
Look under RTL8191SE-VA2 (only Windows drivers)

It's downloading a bit slow here but after you should extract the archive and find the right inf file, then issue the following commands:
```
sudo ndiswrapper -i ~/Desktop/Your_driver/your_inf.inf
```To check if the driver was installed:
```
ndiswrapper -l
```If there are no errors so far you can try the following commands:
```
sudo depmod -a
sudo modprobe ndiswrapper
```See if there were any erros:
```
tail /var/log/messages
```Please post any output you think is an error message.

---

### Post by OpenOS on 2010-12-27
they dont work im off the bed but any more ideas for when i wake up ?

---

### Post by amsterdamharu on 2010-12-27
So when you extract the files from the archive what is the output of the following commands:

```
sudo ndiswrapper ~/Desktop/RTL8191_8192_SE_WindowsDriver_1093.1.1208.2010.F0062_23.P0525_ISS_1.00.0175.L/91_92_SE_Driver/WinXP/net8192se.inf 
```To check if the driver was installed:
```
ndiswrapper -l
```If there are no errors so far you can try the following commands:
```
sudo depmod -a
sudo modprobe ndiswrapper
```See if there were any erros:
```
tail /var/log/messages
```Please post any output you think is an error message.

---

