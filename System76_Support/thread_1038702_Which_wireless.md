---
title: "Which wireless?"
date: 2009-01-13
forum: System76 Support
---

### Post by chez17 on 2009-01-13
I installed ubuntu studio on my Pangolin mdoel panp4n and it didn't include the wireless. I know there are a couple options out there for Ubuntu, I was wondering what the "right" one if for my computer. I don't any help on setting it up, I just want to make sure I'm getting the right one.

---

### Post by Lee_Machine on 2009-01-13
well the best thing to do is instal the S76 drivers.

[http://planet76.com/repositories/](http://planet76.com/repositories/)

scroll all the down to the newest one and install the .deb package.

Then go to System > Administration > System76 Driver 

click on restore system and then reboot

Im not sure if the wireless is supported out of the box. It should be as it works with a live CD.


The only difference with ubuntu studio is the GTK theme and programs installed....that is when I tried it when it first came out.

---

### Post by chez17 on 2009-01-14
I tried doing that and it is still not working. So after poking around, I found this. When I run:

sudo lshw -C network

```

*-network DISABLED      
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:74:a7:40
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:8d:1b:10
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.103 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0e:b5:9d:78:28:c2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

It seems it can detect the wireless, but for some reason it is disabled. I'm not sure what to do next.

---

### Post by Lee_Machine on 2009-01-14
Ok, so to enable it click on the network monitor applet. It will be on the upper right corner where the screen brightness and battery charge applets are.

Right click it and it will say enable networking and enable wireless. Just click on the check-box for enable networking.

it should then detect all wireless networks. To see them left click the same applet and select yours.

The applet will be there by default, but if not you add it by right clicking the top panel and select add to panel. Network Monitor will be one of the choices. 


That should fix it.

---

### Post by thomasaaron on 2009-01-14
Lee Machine is correct. Wireless is supported out of the box with Ubuntu. We don't do anything to it. It should be the same in Ubuntu studio.

Also, you may need to reboot after enabling the wireless per Lee Machine's instructions.

If your version of Ubuntu studio isn't 8.10, that might be the problem. I'm pretty sure the Intel 5100 card doesn't work under Hardy. It's a newer card and didn't gain support until Intrepid.

---

### Post by chez17 on 2009-01-14
Yes, this is Studio 8.10. 

When I right click the Network Monitor, the only options I get are:

Properties
Help
About
Remove From Panel
Move
Lock to Panel

When I open it up, the only connections I see are eth0 and lo. The system doesn't seem to see the wireless at all.

Edit: When I goto System -> Admin -> Network Tools, the default network device is the Loopback Interface, not the Ethernet Interface. Does this mean anything?

---

### Post by thomasaaron on 2009-01-14
It sounds like you might not be right-clicking the right thing.
It is the little icon that looks like a computer monitor (or maybe two monitors). 

The sub-menu you are talking about occurs on most icons, but not on Ubuntu's network manager icon.

---

### Post by chez17 on 2009-01-14
I'm clicking the Network Monitor icon, I am pretty sure of that. When I click About, this is what I get:

gnome-netstatus-applet 2.12.2
The Network Monitor displays the status of a network device.

I don't know why it's not getting the options I need. 

After more digging, I came across a site that said to check this file:

/etc/udev/rules.d/70-persistent-net.rules 

Here is the entry for wireless:

# PCI device 0x8086:0x4232 (iwlagn)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:21:5d:74:a7:40", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

There is nothing in the drivers section. The site suggested I change it to something from the output of the above lshw -C network. It said take the module and put it in the drivers. So from above, module=iwlagn, would it make sense to put iwlagn in the drivers section there?

---

### Post by thomasaaron on 2009-01-14
That's definitely not the network manager icon. Evidently, Ubuntu Studio is using something else.

The Network Manager Icon's About gives this:

> Network Manager Applet 0.7.0
Notification area applet for monitoring your network devices and connections.


A couple more things to try:

1. Press Fn-F11 and give it a minute or two to see if it detects your wireless card.

2. Go to System > Admin > Software Sources and enable backports. It should be the third checkbox down (if it's the same as Ubuntu), and then run updates to see if there's a fix for whatever's ailing whatever Ubuntu Studio is using.

3. Try installing network manager with...
sudo apt-get install network-manager network-manager-gnome

---

### Post by thomasaaron on 2009-01-14
You know, I was thinking...

I'm not finding any posts saying that Ubuntu studio doesn't work with the 5100 card, and that card *should* be supported by the 8.10 kernel (unless Ubuntu Studio somehow left the support out). My gut feeling is that it is a configuration problem.

---

### Post by chez17 on 2009-01-14
Tom,

it was the network manager that did it. It wasn't installed. Thanks so much. As usual, you are the man.

Dave

---

### Post by thomasaaron on 2009-01-14
Goes to show, even a broken clock is right twice a day. :confused:

---

### Post by chez17 on 2009-01-15
For anyone in the future that is reading this thread. After installing network manager, my computer wouldn't shut down. I had to add the lines

```

ifconfig wlan0 down
ifconfig eth0 down

```

to the file: /etc/init.d/alsa-utils

right after the "stop)" on line 354. Hope that helps.

---

