---
title: "ubuntu wlan adhoc network with Nokia N800"
date: 2008-05-27
forum: The Cafe
---

### Post by mtron on 2008-05-27
Hi guys! 

This is a easy way of getting the D-link DWL G122 USB Stick to work with the N800.

The objective is to create a very cheap WLAN Network (total costs are 20 &#8364;) and share the internet connection of the ubuntu box the stick is plugged in to the N800 Linux internet tablet (or any other wlan device).

**1. First here is the hardware you will need**
1.1 D-link DWL G122 H/W Ver:C1 (WLAN USB Stick) [some photos]("http://images.google.co.nz/images?q=D-Link%20DWL-G122") of the stick. The Revision C1 is important! Take care on this detail when you buy it!
[INDENT]The Stick is one of the few wlan usb devices which has open source drivers. Based on the rt73 Ralink Chipset the [serialmonkey project]("http://rt2x00.serialmonkey.com/") develops the OSS driver.[/INDENT]
1.2 A PC running ubuntu & has I-Net access

**2. Software**
2.1 latest drivers for the stick (serialmonkey)
 [INDENT]Before we plug in the stick, Follow the instructions in the [rt73 readme]("http://rt2400.cvs.sourceforge.net/rt2400/source/rt73/README?revision=1.10&view=markup") on your ubuntu box to install the driver. Pretty much as easy as make & sudo make install.  Download drivers here: [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz]("http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz")
to blacklist the shipped ubuntu modules run "sudo gedit /etc/modprobe.d/blacklist" and add this to the end of it, then save and close:

> # Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib

[/INDENT] 

2.2 a management gui (written in gtk, called "rutilt")

[INDENT]it's in the ubuntu repositories, just run "sudo apt-get install rutilt"[/INDENT]

2.3 firestarter (a fronted for iptables to configure internet connection sharing

[INDENT]it's in the ubuntu repositories, just run "sudo apt-get install firestarter"[/INDENT]

**3. Configuration**

[INDENT]The current serialmonkey Drivers don't allow the Stick to operate in Managed Mode (as access point), so we must use Ad-Hoc mode for it. The Disadvantage of this: In ad-hoc mode there is no power saving so the wi-fi chip on the client device must be on all the time. In managed mode the chip can sleep most of the time and is waked up by AP only when needed. Except from this drawback Ad-hoc mode supports also 54Mbit/s and is fairly easy to configure. 

As soon as the serialmonkey driver supports managed mode, i will update this howto accordingly[/INDENT]

**3.1 Configure Wlan Network**

[INDENT]After installing the driver, we configure now our ad-hoc network. For this we will assign our ubuntu box a local IP adress for the Wlan Interface. 
"sudo gedit /etc/network/interfaces"

add: 
> auto wlan0
	iface wlan0 inet static
	pre-up iwconfig wlan0 mode Ad-Hoc
	address 192.168.1.100
	netmask 255.255.255.0
	broadcast 192.168.0.255
	wireless-mode ad-hoc
	wireless-essid *your-essid*
	wireless-key 1234567890

Line-by-Line :
this brings up the interface wlan0 with a stratic IP
preconfigures it to ad-hoc mode
sets this IP for the ubuntu Wlan stick
sets this netmask for the wlan network
sets this broadcast for the wlan network
sets the wireless-mode to ad-hoc
set the Wlan network ID. replace your-essid with your own
set the wireless-key to 1234567890 (replace this with a 10 digit password)

now plug in your stick and restart your wlan with

```
sudo ifdown wlan0
sudo ifup wlan0
```

Check "dmesg" if the stick got recognized. You should see one of the led's flashing if it worked.[/INDENT]


**3.2 configure Firestarter**

[INDENT]open the firestarter gui and click on Preferences button, go to Network Settings tab and change the Local Network Connected Device to wlan0. Now enable the checkbox next to "internet connection Sharing" and you are ready. Click on Apply and close firestarter[/INDENT]

**3.3 rutilt**

[INDENT]open rutilt, and go to "options" tab. Bring the interface down and change the Maximum TX rate to 54 Mbps. now click on the RT73WLAN tab and enable the check boxes next to TX bust , Turbo Rate & OFDM in Ad-Hoc mode.

Now change to the profile tab and add a new profile:

> *Wireless Settings Tab:*
Name: set a name of your choice
SSID: use the same SSID as in /etc/network/interfaces
Mode: Ad-Hoc
Channel: 10
Authentication: Open
Encyption: WEP
Key: use the same Key as in /etc/network/interfaces

*IP settings Tab:*
set the radio box to "disabled" (we have configured this in /etc/network/interfaces already)

Now click on OK. Back in rutilt, Click on the "Apply" button, and on the options tab, bring the interface back up. you should see your IP address 192.168.1.100 in the rutilt status tab now.

more about this app at the rutilt [readme]("http://rt2400.cvs.sourceforge.net/rt2400/source/rutilt/README?view=markup")
[/INDENT]


**3.4 configure N800 / Wlan client**

[INDENT]to make a connection with a wlan client, you need to create a custom wlan profile at the client. This example is for a N800 Linux Internet Tablet Running latest OS2008:

Click on the wlan status icon and choose "connection Settings" 
Clock on the the "Connections" button & on "New"
> 
Name: set a name for your Wlan Network profile of your choice
Connection Type: Wlan
Network Name: use the same SSID as in /etc/network/interfaces on the ubuntu box
Network is hidden: enable checkbox 
Network Mode: Ad-Hoc
Security Method WEP


click on continue

> Standard WEP Key: 1
WEP Key 1: use the same Key as in /etc/network/interfaces on the ubuntu box

click on "continue" & at the next screen click on the "advanced" button

change to the second tab called "IP Adress" 

> get IP Adress automatically: uncheck
IP: 192.168.1.101
Subnet: 255.255.255.0
Router: 192.168.1.100

Primary DNS: set your ISP's real DNS server IP here (same as on the ubuntu box!) 

change to the 3rd tab called "other":
> WLAN Energy: 100mW
Ad-Hoc Channel: Automatic
Save Energy: ON (Maximum)

That's it. click on OK and close the wlan manager. [/INDENT]

You should be able to connect via the usual way on the N800 to your ad-hoc Wlan now. Internet connection sharing should also work as expected.

Have fun!

---

### Post by master5o1 on 2008-05-27
should this become a how to?

---

### Post by mtron on 2008-05-27
dunno. the last howto i wrote was not accepted in the howto section, and was deleted. I don't want to risk it again, so i posted it in this section in the hope it will stay online and help sb ;)

---

