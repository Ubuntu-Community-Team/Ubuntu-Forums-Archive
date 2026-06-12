---
title: "help critique/complete wireless troubleshooting guide"
date: 2005-11-18
forum: The Cafe
---

### Post by Lambert on 2005-11-18
As much help as I've received I wanted to give back a little. I've spent some time answering question in the forum and decided to try and write a wirless troubleshooting guide.

This is not any where near complete and I'm not sure if it really offers anything. My intention is to add to the wiki and possibly post somewhere here in the forums if it fits in.

I want to ask though from the community their thoughts/suggestions and also to get some help completing it. I have limited knowledge in areas (such as wpa). [COLOR=Purple]Items in this color are areas I know I need help in[/COLOR]. Other things you see being helpful just recommend. I do want to add as many external links with info about a device/chipset/driver so this can be a one place to solve as many problems as possible, so if you have good links please post them. I will continue to edit this post until it looks like it's pretty complete. I will then transfer it to the wiki. 

Currently it is in a rough draft format so it may be hard to read. It will be cleaned up when posted to the wiki. In section 1 where I list commands there will be link to the command in section where there is more detail. Of course if anyone can recommend a better format to make it easier to use/read, please make a suggestion.

So here it is

-----------------------------

The following is meant to be a self help troubleshooting guide to get wireless working or if already connected solve an annoying problem.

Sections
1. Steps
2. Commands
3. Config files
4. Special circumstances


[SIZE=3]** Steps**[/SIZE]
1. Is device PnP, check
2. What driver for your device and is correct driver loaded
3. Is device recognized as wireless network device
4. Check for access points sudo iwlist <device> scan


1. Most devices are plug and play but it is worth checking first. (Note: Plug and Play is a term used in the computer field to describe a computer's ability to have new devices, normally peripherals, added to it without having to reconfigure or (ideally) restart the computer. This term does not mean it will work as intended immediately. A driver for the device has to be installed or activated in some cases) 
Use the following commands to check 
sudo lshw
lspci
lsusb
If you see your device then move on to step 2

2. When running sudo lshw did you see a driver listed? If so is it loaded (lsmod)? If no driver then you need to find what your card uses. 
You can go to this site to find the driver/chipset of your card.
[http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")
You may find invaluable information about others experience with the same device by searching the forums, the wiki, or google adding linux or ubuntu as a keyword to the phrase.
Some links
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")

If there is a driver written for linux, find instructions for installing it and setting up.
Here is a list of drivers supported in breezy
kernel/drivers/net/wireless/acx    ([http://acx100.sourceforge.net/]("http://acx100.sourceforge.net/"))
kernel/drivers/net/wireless/adm8211  ([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#ADMtek]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#ADMtek"))  
kernel/drivers/net/wireless/prism2     ([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Prism2]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Prism2"))
kernel/drivers/net/wireless/rt2400     ([http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page"))
kernel/drivers/net/wireless/rt2500     ([http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page"))
kernel/drivers/net/wireless/wlan-ng ( [http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Prism2]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Prism2"))
kernel/drivers/net/wireless/ipw2100    ([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Centrino]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Centrino"))
kernel/drivers/net/wireless/ipw2200    ([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#CentrinoAG]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#CentrinoAG")) 
kernel/drivers/net/wireless/prism54    ([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#Prism54]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#Prism54"))
kernel/drivers/usb/net/atmel    ([http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Atmel]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Atmel"))
kernel/drivers/usb/misc/eagle-usb [COLOR=Black]([http://freshmeat.net/projects/eagle-usb/)]("http://freshmeat.net/projects/eagle-usb/%29")[/COLOR]
madwifi (atheros) ([http://madwifi.org/]("http://madwifi.org/"))
[COLOR=Purple](did I miss any??)[/COLOR]

If there are no driver then you can try to use the windows drivers by using a module called ndiswrapper.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") (list of known cards that work with ndiswrapper)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu") (driver installation steps for ndiswrapper)

If you have a internet connection while logged into ubuntu then:
Command
sudo apt-get install ndisgtk (graphical front end to install windows drivers) ([http://lxer.com/module/newswire/view/46385/]("http://lxer.com/module/newswire/view/46385/"))


3. Now with driver loaded is device recognized? Run command.
iwconfig 
If device does not show up then there is a problem with the driver. Go back to step 2 and 
1. Check you're using the correct driver.
2. Check to make sure it's the correct version
3. Check that it's installed and loaded. 

4. Now with driver working and device recognized as a wireless device, 
Command
sudo iwlist <wlan0> scan
This will scan for any access points and identify some general information about the ap. If results bring back an access point then device is working properly and you need to enter your network settings. From the panel System>Admin>network. choose your device, click properties, enter your network settings (note channel can not be set here nor can wpa settings) click ok then click activate. 
Command
iwconfig - This will tell you if you're connected to the ap
If not you will need to check your settings.

If having problem with graphical then enter this command:
sudo iwconfig <device(ath0)> ap xx:xx:xx:xx:xx essid <your_essid> channel <chan> key <key> commit

ap=serial(mac address) of access point. (this can be found using the iwlist <ath0> scan command)
key= wep encryption key (for examples and formats of different wep settings look at man page *man iwconfig*)

[COLOR=Purple]Help using wep setting


[COLOR=Black]Security using WPA[/COLOR]

[/COLOR] If you are using wpa encryption, you will need to install wpa_supplicant to use wpa security.
[I]Link for informatin on wpa which includes a list of what drivers that are supported by wpa_supplicant
[/I][http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/) 
Note: *If having problems connecting and you're using wep or wpa, you will have to seriously consider switching briefly to an open broadcast with no encryption just to cross out the the possibiltiy of the problem being in the type of encryption being used. If you can not do this, you will have to continue troubleshooting with encryption or find a hot spot with an open signal to test.*

If connected to access point then 
Command
ifconfig - This will tell you if you have an ip address assigned to the device.

If no ip address assigned then you need to check on assignment of ip address.

[COLOR=Purple]dhcp

[COLOR=Black]If you receive errors about dhclient not working or something similar try
sudo dpkg-reconfigure dhclient[/COLOR]

static[/COLOR]




[SIZE=3]** Commands**[/SIZE]
(these are brief descriptions, type MAN <COMMAND> for all options and more details)

** iwconfig**
 Running iwconfig shows the recognized wireless network devices. This command can also configure the interface from the command line. Example: sudo iwconfig wlan0 essid router. 
SAMPLE
ath0      IEEE 802.11g  ESSID:"something"  Nickname:"XXXXX"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:25:32:2A:DA:0E
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/94  Signal level=-47 dBm  Noise level=-95 dBm
          Rx invalid nwid:27199  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:3


[COLOR=Blue] KEY POINTS[/COLOR]
If all you see is ath0, lo, eth1, wlan0 or similar and nothing like the above sample, then there is no driver loaded for the device or it's not the correct driver as the os is not communicating with the device and identifying it as a wireless device.
Access point- If you see all zeros this tells you you're not connected to the router
Frequency- This is also known as your channel. Make sure the frequency matches the channel setting on your router.
Channel     
1     2.412     
2     2.417     
3     2.422     
4     2.427     
5     2.432     
6     2.437     
7     2.442     
8     2.447     
9     2.452     
10     2.457     
11     2.462     
12     2.467     
13     2.472     
14     2.484          
You can not set the channel from the gui in system>admin>network. from a command line type sudo iwconfig <wlan0> channel <channel>

** ifconfig**
 This is similar to iwconfig except it gives different information including any wired devices. The benefit on a wireless device is it shows your device's ip address.
SAMPLE
ath0      Link encap:Ethernet  HWaddr 00:33:91:50:HE:22
          inet addr:192.168.1.11  Bcast:192.168.255.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe50:be62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27287 errors:257218 dropped:0 overruns:0 frame:257218
          TX packets:10274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:17317520 (16.5 MiB)  TX bytes:1405653 (1.3 MiB)
          Interrupt:11 Memory:d0c80000-d0c90000

[COLOR=Blue] KEY POINTS[/COLOR]
inet addr: 192.168.1.11 This is the ip assigned to the device. If you are connected to the router and not directly to the modem, this is a private/local ip address assigned from the router, not your public ip address. To find that go to [www.myipaddress.net]("http://www.myipaddress.net")
HWaddr 00:33:91:50:HE:22 This is the serial/mac address of the router.



** iwlist**
    This gives more detailed information from a wireless interface. The sample below shows scanning for an access point.
SAMPLE
sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:33:91:50:HE:22
                    ESSID:"bible"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/94  Signal level=-52 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
Notes
not all interfaces support scanning so you may get a message stating this.

** lshw**
    This command shows information on all hardware. With options we can narrow down to just network devices.
sudo lshw -businfo will show a quick list of all items. Look for your item and the class. Then type sudo lshw -C <class>
 If you do not see it in the list then the device is not plug n play or something happened and the os didn't pick it up. 
SAMPLE
sudo lshw -C network
 *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@03:00.0
       logical name: ath0
       version: 01
       serial: 00:11:95:50:be:62
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) ip=192.168.0.150 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:10800000-1080ffff irq:11

KEY POINTS
Notice the configuration line. It shows you the driver being used for the device and it's version.

** lsusb**
 This is similar to lshw but it gives a little different info. lsusb should be used if you're using a usb device. I don't have a sample but see below on lspci as out put will be similar.


** lspci**
    Same as lsusb but for devices connected via pci.
SAMPLE
sudo lspci -v
0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc D-link DWL-G650 (Rev B5) Wireless cardbus adapter
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 10800000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
KEY POINTS 
If you're looking for chipset information you find it here. If you're looking for what revision your device is, it is where it says rev B5 in this sample, not rev 01.

** dhclient**
 This is the application called upon when using dhcp. If you're connected to the router but not being assigned an ip address, sometimes this can be used to force an ip assignment.
sudo dhclient ath0

** lsmod**
 This lists all modules loaded. After running lshw command and seeing what driver is used, you can run this to make sure the module is loaded.
sudo lsmod | grep <driver> (you can limit the input of driver just to the first few letters)
SAMPLE
sudo lsmod | grep ath
ath_pci                78908  0
ath_rate_sample        16776  1 ath_pci
wlan                  141532  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148432  3 ath_pci,ath_rate_sample


** ping**
    If you're connected to the router and assigned an ip but no internet you can use this command to troubleshoot.
First ping the ip assigned to you device (found by ifconfig)
    ping 192.168.1.11
If success then ping router
ping 192.168.0.1 (you have to know what this is or look up in router documentation. A lot of routers come out of the box with 192.168.0.1 or something real close
If success then try another computer in your network
    ping 192.168.1.10 you can find this by ifconfig on linux or ipconfig on windows by start>run cmd
If success then try an external website
    [COLOR=Purple]ping[/COLOR] 
If success then try using the common name
    ping [www.yahoo.com]("http://www.yahoo.com")
If success then you should be able to access a website via your browser. If success up to external website but can't ping using common name then check /etc/resov.conf to see if anything is there. If not then you need to set up a dns server.



[SIZE=3]** config files worth noting**[/SIZE]

/etc/network/interfaces (interface information such as essid, encryption, etc...)
[COLOR=Purple]want to post sample interfaces and explain what each line means[/COLOR]
/etc/resolv.conf (where dns information is stored)
/etc/dhcp3/dhclient.conf


[B][SIZE=3][COLOR=black] Special circumstances

[/COLOR][/SIZE][/B] Adding channels 13&14 for Ralink chipset. ([http://ubuntuforums.org/showthread.php?t=87274]("http://ubuntuforums.org/showthread.php?t=87274"))
Connections that drop/reconnect frequently
1. If you're using a scanner such as gtkwifi,network manager, or wifi-radar. These can cause this as it drops the connection and re-scans. Best thing to do is submit a bug so your favorite manager gets upgraded and better supports what it's supposed to.
2. Wireless b & g run on the 2.4ghz range along with a miriad of other devices. Sometimes there is signal interferance which causes the signal to drop. Somethings to try.
Commands
sudo iwconfig <ath0> ap xx:xx:xx:xx:xx
-this will force connection (if possible) that that access point. for more info look at [I]man iwconfig
[/I]sudo iwconfig <ath0> sens <-80 to 80>
- if you're picking up weak signals from another device, changing the sensititvity will filter out these weak signals. You will have to play with different settings to find what's best. Many newer cards do this automatically but it's something to look into if you're having problems. (add more info later)

 
Future sections
Networking and bootup help
driver conflicts
[COLOR=Purple]Others?[/COLOR]
(I will add sections based on questions asked on the forum)


Now if you have gone through this and can not get your wireless up and running, here are some other things you can do.

1. Search the forums using keywords such as driver, chipset, device model number. To see if someone else had a similar question and you can find an answer to your problem in their thread.
2. Search google or your favorite search engine using the model number and these various terms. Ubuntu; linux; help;
3. Start a new thread and when you post include the following command output/information.

    a. make and model of device, chipset if you have and driver you're trying to use
    b. outputs of the commands above depending on where you're having trouble
    c. include any steps or what you've tried with best detail possible
    d. any errors you have
    e. where you're at and can't get past

---

### Post by xequence on 2005-11-18
I have little knowledge in wireless anything, but it looks like a good guide. Good work, and good luck making it better :P

---

### Post by Brunellus on 2005-11-18
this definitely belongs on the wiki.

---

### Post by orbinick on 2005-11-20
I wish I'd see a solution to a recurring problem. The wireless lan starting at boot. Sometimes even when configured as auto, it doesn't connect or it connects after a long 5 or seven minutes. My guess is, it may have to do with the WEP key security mode. I always found it Restricted instead of Open, but I Don't know how to make the change stick as it always defaults to Restricted.

---

