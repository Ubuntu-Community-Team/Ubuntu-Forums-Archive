---
title: "Hp Network Card not working"
date: 2010-05-16
forum: Ubuntu Studio
---

### Post by kaig20 on 2010-05-16
Hey I am having issues with my laptop when I am running Ubuntu Studio. No Network connections show up and I have tried everything that I can think of including some things on other posts and nothing works. I am wondering if there is no driver out for my machine. This is the driver info: 
Atheros:       AR5009 802.11a/g/n WiFi Adapter
File Version:  8.0.0.172 built by WinDDK
Or maybe there is something that I am doing wrong
My machine is an HP dv6 2044ca with a touch button WiFi enabler 
Thanks  for any help
:guitar:
:confused:

---

### Post by pytheas22 on 2010-05-16
Please post the output of these commands so we can get a better idea of what might be wrong:
```

dmesg | grep -e ath -e wlan -ie radio
lshw -C Network
sudo iwlist scan
lspci -nn | grep -i atheros
cat /etc/issue
```

---

### Post by kaig20 on 2010-05-16
I am having an issue because I can save the image of the results but than I have to shut down ubuntu studio to run windows in order to get the files to you because I have no internet with ubukntu studio. any suggestions on how to get the files to you?
thanks

---

### Post by kaig20 on 2010-05-16
Here they are, I found a way to get them.

ubuntu@ubuntu:~$ dmesg  grep -e ath -e wlan -ie radio
dmesg: invalid option -- 'e'
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]
ubuntu@ubuntu:~$ 




ubuntu@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan1
       version: 01
       serial: 70:1a:04:3b:9f:15
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f1100000-f110ffff
  *-network DISABLED
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth2
       version: 02
       serial: 00:26:9e:4c:29:c7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:28 ioport:2000(size=256) memory:f1010000-f1010fff(prefetchable) memory:f1000000-f100ffff(prefetchable) memory:f1020000-f102ffff(prefetchable)
ubuntu@ubuntu:~$ 




ubuntu@ubuntu:~$ sudo iwlist scan
[sudo] password for ubuntu: 
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Network is down

ubuntu@ubuntu:~$ 




ubuntu@ubuntu:~$ lspci -nn  grep -i atheros
Usage: lspci [<switches>]

Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of atheros
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file
ubuntu@ubuntu:~$ 




ubuntu@ubuntu:~$ cat /etc/issue
Ubuntu 10.04 LTS \n \l
ubuntu@ubuntu:~$ 



I hope this can help
I found that I didn't have a straight up and down line on my keyboard that I could use when in terminal, or anywhere else for that matter. So I hope that the codes I put in will work.
Thanks for the help

---

### Post by pytheas22 on 2010-05-16
Thanks for the information.  The first (and, if we're lucky, only) issue to deal with is making your card able to see wireless networks.  If you type:
```

sudo rfkill unblock all
sudo ifconfig wlan1 up
```

does the wireless light on your keyboard change from red to blue?

> I found that I didn't have a straight up and down line on my keyboard that I could use when in terminal, or anywhere else for that matter. So I hope that the codes I put in will work.

You should have the | character somewhere--I've never seen a keyboard, in any language, without it.  On my computer it's on the same key as \.  You can also enter it if you go to Applications>Accessories>Character Map; it's under the "Common" section.  Or you can just copy and paste from here.  It would be good to see these commands again, with that character in them:
```

dmesg | grep -e wlan -e ath -ie radio
lspci -nn | grep -i atheros
```
> 
I am having an issue because I can save the image of the results but than I have to shut down ubuntu studio to run windows in order to get the files to you because I have no internet with ubukntu studio. any suggestions on how to get the files to you?

In this situation, I would copy and paste the output into a text editor (Applications>Accessories>Text Editor), then copy that file to a computer with Internet access to post here.  But it looks like you've figured that out.

---

### Post by Bucky Ball on 2010-05-16
Have you plugged in an ethernet cable and gotten updates? That card should be recognised and appropriate drivers and firmware installed or offered.

---

### Post by kaig20 on 2010-05-17
I have plugged in the Ethernet cable but I haven't gotten any updates, I am not sure how I would go about that.

---

### Post by kaig20 on 2010-05-17
I put in the two commands and the wireless light did turn from red to Blue.
I will try to re-put in those other commands and see what we come up with

---

### Post by kaig20 on 2010-05-17
Here they are:



ubuntu@ubuntu:~$ dmesg | grep -e ath -e wlan -ie radio
[    0.775486] device-mapper: multipath: version 1.1.0 loaded
[    0.775488] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.336561] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.336571] ath9k 0000:08:00.0: setting latency timer to 64
[   13.765710] ath: EEPROM regdomain: 0x69
[   13.765712] ath: EEPROM indicates we should expect a direct regpair map
[   13.765715] ath: Country alpha2 being used: 00
[   13.765716] ath: Regpair used: 0x69
[   13.772260] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.772898] Registered led device: ath9k-phy0::radio
[   13.772912] Registered led device: ath9k-phy0::assoc
[   13.772925] Registered led device: ath9k-phy0::tx
[   13.772937] Registered led device: ath9k-phy0::rx
[   13.772947] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xf81a0000, irq=17
[   13.784365] udev: renamed network interface wlan0 to wlan1
ubuntu@ubuntu:~$ 




ubuntu@ubuntu:~$ lspci -nn | grep -i atheros
08:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
ubuntu@ubuntu:~$ 



Thanks a lot

---

### Post by pytheas22 on 2010-05-17
> I put in the two commands and the wireless light did turn from red to Blue.
I will try to re-put in those other commands and see what we come up with

That's a good step.  For now, you may have to reenter those commands manually after each reboot to get the wireless back on.  Later, we can write a script to do this automatically for you.

Once the wireless light turns blue, you should be able to connect to networks.  However, it sounds like you don't have any wireless connection client available to you.  You can install one by typing these commands (you will need to be plugged into the Internet for this to work):
```

sudo apt-get update
sudo apt-get install wicd
```

You can then launch the manager, Wicd, from the Applications>Internet menu.  Are you able to connect to your wireless network that way?

If Wicd won't connect you, please post the output of this command when your wireless light is blue, and let me know the name of the network you're trying to connect to:
```

sudo iwlist scan
```

---

### Post by kaig20 on 2010-05-17
I am still unable to connect to a network even though I have the Ethernet cable plugged in (I tried it on windows and it worked). But I put in those codes anyway to see if they would help anything. Here they are:

ubuntu@ubuntu:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
ubuntu@ubuntu:~$ 




ubuntu@ubuntu:~$ sudo apt-get install wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-iniparse python-wicd wicd-daemon wicd-gtk
The following NEW packages will be installed:
  python-iniparse python-wicd wicd wicd-daemon wicd-gtk
0 upgraded, 5 newly installed, 0 to remove and 2 not upgraded.
Need to get 559kB of archives.
After this operation, 3,117kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe python-wicd 1.7.0+ds1-2
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main python-iniparse 0.3.1-1
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe wicd-daemon 1.7.0+ds1-2
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe wicd-gtk 1.7.0+ds1-2
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe wicd 1.7.0+ds1-2
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/python-wicd_1.7.0+ds1-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/python-wicd_1.7.0+ds1-2_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-iniparse/python-iniparse_0.3.1-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-iniparse/python-iniparse_0.3.1-1_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-daemon_1.7.0+ds1-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-daemon_1.7.0+ds1-2_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-gtk_1.7.0+ds1-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd-gtk_1.7.0+ds1-2_all.deb)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.7.0+ds1-2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/wicd_1.7.0+ds1-2_all.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuntu@ubuntu:~$ 




ubuntu@ubuntu:~$ sudo iwlist scan
[sudo] password for ubuntu: 
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Network is down

ubuntu@ubuntu:~$ 



The Network I am trying to get on is: farm9   which is the wireless and wired network (the cable I am plugged into comes from this one)
The other network is: Farm Cabins     which is a wireless network (No cable plugged into it)

Hope this helps 
Thanks

---

### Post by pytheas22 on 2010-05-18
> I am still unable to connect to a network even though I have the Ethernet cable plugged in (I tried it on windows and it worked).

With the cable plugged in, type this command:
```

sudo dhclient eth2
```

That should connect you.  Once you are online, type:
```

sudo apt-get update
sudo apt-get install wicd
```

That will install wicd (it didn't work before because you had no Internet connection).  With wicd installed, are you able to connect to networks?

Remember that if you can't see networks at all, you probably need to type:
```

sudo rfkill unblock all
sudo ifconfig wlan1 up
```

in order to make the wireless radio work.

---

### Post by myromance123 on 2010-05-18
I can't be certain, but my problem was fixed by purging network manager, like what pytheas22 said in my previous thread:
```
sudo apt-get remove --purge network-manager
```

 That was ONLY to fix my wireless problem. Do NOT attempt this until you have your normal ethernet up and running. (In case it wasn't the problem, and you need to reinstall the network manager)

 Also, in Ubuntu Studio 10.04, it has this really odd option for the ethernet.
 You either choose 'eth0' or 'lo'. 'lo' is basically a self looping network within your computer..

 Make sure that you have eth0 selected from the Ubuntu Studio Network Manager, and NOT 'lo'.

 On the top panel, right click and then click 'Add to Panel'. Then search for Network or Network Manager. Choose it, then once its up in the panel right click it. There should be a drop down menu. Click it and see if you have the option of choosing eth0.

---

### Post by kaig20 on 2010-05-18
Yay!!!!!!!!!!!!!!!!!!!
I got things working all good (wired and wireless)
I will post the codes I got from those two commands in case they tell us anything important
Here they are:



ubuntu@ubuntu:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [189B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [32.5kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [38.5kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [5,309B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [151kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [2,164B]       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]       
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [1,216B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [780B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [14B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [14B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [2,102B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [60.4kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [737B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [23.7kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [5,958B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [632B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [14B]
Fetched 325kB in 4s (77.3kB/s)                     
Reading package lists... Done
ubuntu@ubuntu:~$ 



It seems like I can't find the results from the second command but I hope it doesn't matter.
I will shut down and see if it automatically comes back on when I start up
Thanks again

---

### Post by kaig20 on 2010-05-18
Ok I started it back up and the Internet comes on automatically!!!!!!!!!!!!
Thank you so much for all the support!!!
And the quick responses!!!!!
Good luck
  Kai Grenier:guitar:

---

### Post by pytheas22 on 2010-05-18
Glad to hear you got it sorted out.  Enjoy Ubuntu!

---

