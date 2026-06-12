---
title: "howto: ubuntu 16.04 Tvheadend DVB-C/S(2)/T &amp; non-DVB (ipcam/DV) rotate recording"
date: 2016-09-09
forum: Tutorials
---

### Post by walterav on 2016-09-09
**[size=+2]part1: Tvheadend server with DVB-C/S(2)/T & non-DVB (ipcam/DV) tuners on Ubuntu 16.04[/size]**
[post="13542232"]part2: Tvheadend client integration (Kodi pvr-hts) Ubuntu/Raspbian/Windows/Mac OS/Libreelec[/post]
[post="13825784"]part3: Tvheadend mpegts recordings lossless cut, split, trim and remuxing using ffmpeg[/post]

TODO improvements:
*pros/cons easy install tvheadend from ubuntu snapcraft (usb support?)
*add screenshots (wait for Kodi18)
*add sources/credits

**[size=+2]Requirements:[/size]**
[LIST]
[*]Skills
Installing ubuntu linux/understand Processor/CPU architectures/distro-release names/differences
Using terminal (bash) 
[*]Internet
For downloading ubuntu packages during install!

[*]Software:
ubuntu linux 16.04.1 amd64(i686 not addressed, but probably works) minimal cli & desktop optional head(less)
[http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/mini.iso)
updated mini.iso overcomes "libc6-udeb failed"
[http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/installer-amd64/current/images/netboot/mini.iso)
Tvheadend 4.x
[https://tvheadend.org/projects/tvheadend](https://tvheadend.org/projects/tvheadend)

[*]Hardware:
[LIST]
[*]spare pc/notebook/server/vm 
RAM 512MB 
CPU i686(pae) / amd64 architecture (custom builds for arm/mips etc possible)
STORAGE 8GB HDD (OS) /  1TB HDD(MEDIA)
USB2 / PCI(E) / FW / Ethernet interfaces 
[*]DVB tuners: DVB-C/S(2)/T(2)  USB2/PCI(E)/Ethernet/SAT>IP based
[table="width: 720"]
[tr]
	[td]interface[/td]
	[td]lsusb / lspci[/td]
	[td]productname[/td]
	[td]works ootb[/td]
	[td]DVB-capable[/td]
	[td]DVB-working[/td]
	[td]DiSEqC-tested[/td]
	[td]info[/td]
[/tr]
[tr]  			 
	[td]USB 2.0[/td]
	[td]0fd9:0018 Elgato Systems GmbH EyeTV Hybrid[/td]
	[td]Elgato EyeTV hybrid[/td]
	[td]yes[/td]
	[td]DVB-C DVB-T[/td]
	[td]DVB-C DVB-T[/td]
	[td][/td]
	[td][https://www.linuxtv.org/wiki/index.php/Elgato_EyeTV_hybrid](https://www.linuxtv.org/wiki/index.php/Elgato_EyeTV_hybrid)[/td]
[/tr]
[tr] 	 						
	[td]USB 2.0[/td]
	[td]2040:1605 Hauppauge[/td]
	[td]Hauppauge WinTV-HVR 930C-HD[/td]
	[td]no, firmware[/td]
	[td]DVB-C DVB-T[/td]
	[td]DVB-C[/td]
	[td][/td]
	[td][https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-930C](https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-930C)[/td]
[/tr]
[tr] 	 						
	[td]USB 2.0[/td]
	[td]2040:0265 Hauppauge[/td]
	[td]Hauppauge WinTV-DualHD 01590[/td]
	[td]no, firmware & linux kernel 4.17[/td]
	[td]DVB-C DVB-T2[/td]
	[td]DVB-C DVB-T2[/td]
	[td][/td]
	[td][https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-dualHD#Model_01590_.28USB_device_ID_2040:0265.29](https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-dualHD#Model_01590_.28USB_device_ID_2040:0265.29)[/td]
[/tr]
[tr]
	[td]USB 2.0[/td]
	[td]15f4:0131 HanfTek[/td]
	[td]Astrometa dvb-t2[/td]
	[td]no, firmware(load assist/highfrequency patch)[/td]
	[td]DVB-C DVB-T(2)[/td]
	[td]DVB-C DVB-T(2)[/td]
	[td][/td]
	[td]2014 revision [https://www.linuxtv.org/wiki/index.php/Astrometa_DVB-T2](https://www.linuxtv.org/wiki/index.php/Astrometa_DVB-T2)[/td]
[/tr]
[tr]
	[td]USB 2.0[/td]
	[td]15f4:0135 HanfTek[/td]
	[td]T2hybrid[/td]
	[td]no, firmware & linux kernel 4.14 module[/td]
	[td]DVB-T DVB-T2 DVB-C[/td]
	[td]DVB-T, DVB-C[/td]
	[td][/td]
	[td]2015 revision [https://www.linuxtv.org/wiki/index.php/Astrometa_DVB-T2](https://www.linuxtv.org/wiki/index.php/Astrometa_DVB-T2) [https://patchwork.kernel.org/patch/9694443/](https://patchwork.kernel.org/patch/9694443/)[/td]
[/tr]
[tr]  			 
	[td]USB 2.0[/td]
	[td]045e:02d5 Microsoft Corp. Xbox One Digital TV Tuner[/td]
	[td]Digital TV Tuner XBOX ONE[/td]
	[td]no, firmware & build linux kernel 4.16.x module[/td]
	[td]DVB-C DVB-T(2)[/td]
	[td]DVB-C DVB-T(2)[/td]
	[td][/td]
	[td][https://www.linuxtv.org/wiki/index.php/Xbox_One_Digital_TV_Tuner](https://www.linuxtv.org/wiki/index.php/Xbox_One_Digital_TV_Tuner) [https://tvheadend.org/boards/5/topics/13685](https://tvheadend.org/boards/5/topics/13685)[/td]
[/tr]
[tr]
	[td]ETHERNET (HDHomeRun)[/td]
	[td]firmware [2018-08-17]("https://www.silicondust.com/support/downloads/firmware-changelog") network-id support[/td]
	[td]HDHR3-4DC[/td]
	[td]no,requires Tvheadend to be compiled with libhdhr client[/td]
	[td]DVB-C[/td]
	[td]DVB-C[/td]
	[td][/td]
	[td][HDHomeRun Expand / Silicondust ]("https://www.silicondust.com/product/hdhomerun-expand-eu")[/td]
[/tr]
[tr]
	[td]ETHERNET (sat>IP)[/td]
	[td][Inverto IDL-400s V1_25_0_157]("http://www.inverto.tv/download/file/59b8e808a50e7-1505290248.rar") / [satip-axe-201810211549-15.fw"]("https://github.com/perexg/satip-axe/tree/master/dist") [/td]
	[td]Digibit Telestar R1[/td]
	[td]no,firmware update/satip-axe[/td]
	[td]DVB-S DVB-S2[/td]
	[td]DVB-S DVB-S2[/td]
	[td]1.0+4lnb's[/td]
	[td]Inverto IDL-400s / Grundig GSS.BOX / Digibit Telestar R / share same firmware[/td]
[/tr]
[tr]
	[td]PCIE 1x[/td]
	[td]14f1:8852 (rev 04)Subsystem: 6981:8888[/td]
	[td]TBS 6981 DVB-S2 Dual Tuner Card[/td]
	[td]no,firmware[/td]
	[td]DVB-S DVB-S2[/td]
	[td]DVB-S DVB-S2[/td]
	[td]1.1+5lnb's[/td]
	[td][https://www.linuxtv.org/wiki/index.php/TBS6981](https://www.linuxtv.org/wiki/index.php/TBS6981) Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)[/td]
[/tr]
[tr]
	[td]PCI[/td]
	[td]1131:7146 (rev 01)Subsystem: 13c2:1019[/td]
	[td]Technotrend s2-3200 (CI)[/td]
	[td]yes[/td]
	[td]DVB-S DVB-S2[/td]
	[td]DVB-S DVB-S2[/td]
	[td]1.1+5lnb's[/td]
	[td][https://www.linuxtv.org/wiki/index.php/TechnoTrend_TT-budget_S2-3200](https://www.linuxtv.org/wiki/index.php/TechnoTrend_TT-budget_S2-3200) Multimedia controller: Philips Semiconductors SAA7146 (rev 01)[/td]
[/tr]
[tr]
	[td]PCI[/td]
	[td]1131:7146 (rev 01)Subsystem: 13c2:1003[/td]
	[td]Hauppauge WinTV-NOVA-S DVB card (budget)[/td]
	[td]yes[/td]
	[td]DVB-S[/td]
	[td]DVB-S[/td]
	[td]1.1+5lnb's[/td]
	[td][https://www.linuxtv.org/wiki/index.php/Supported_DVB_cards#Hauppauge.2FTT_Nova_budget](https://www.linuxtv.org/wiki/index.php/Supported_DVB_cards#Hauppauge.2FTT_Nova_budget) Multimedia controller: Philips Semiconductors SAA7146 (rev 01)[/td]
[/tr]
[tr]
	[td]PCI[/td]
	[td]1131:7133 (rev d1) Subsystem: 16be:0010[/td]
	[td]Asus/Medion tv capturecard?[/td]
	[td]no,firmware[/td]
	[td]DVB-T[/td]
	[td]DVB-T[/td]
	[td][/td]
	[td][https://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007](https://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007) Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)[/td]
[/tr]
[/table]

[*]non-DVB sources:
[table="width: 720"]
[tr]
	[td]interface[/td]
	[td]protocol[/td]
	[td]productname[/td]
	[td][/td]
	[td][/td]
[/tr]
[tr]
	[td]ethernet[/td]
	[td]rtsp/rtmp/udp[/td]
	[td]Ubiquity Aircam v1.2[/td]
	[td][/td]
	[td][/td]
[/tr]
[tr]
	[td]FireWire[/td]
	[td]dv/hdv[/td]
	[td]Camcorder/AD-converter[/td]
	[td][/td]
	[td][/td]
[/tr]
[tr]
	[td]RCA Stereo Plugs[/td]
	[td]alsa[/td]
	[td]Behringer UCA200 external usb soundcard[/td]
	[td][/td]
	[td][/td]
[/tr]
[tr]
	[td]SDI/HDMI/COMPONENT COMPOSITE/S-VIDEO[/td]
	[td]decklink api[/td]
	[td]Blackmagicdesign Decklink Intensity series[/td]
	[td][/td]
	[td][/td]
[/tr]
[tr]
	[td]PCI/USB[/td]
	[td]V4L2[/td]
	[td]Hauppauge WinTV PVR-150[/td]
	[td][/td]
	[td][/td]
[/tr]
[/table]

[/LIST]

[*]DVB networks Service Providers:
The following European/Dutch DVB cable / terrestrial / satellite service providers with FTA services will be addressed:
[LIST]
[*]DVB-C "Dutch: Ziggo (Cable) and KPN/Telfort (Fiber+DVB-C module!)"
[*]DVB-T2 "Dutch: digitenne"
[*]DVB-S(2) "European satellites: Eutelsat/Hotbird 13.0°E, Astra 1 19.2°E, Astra 3 23.5°E, Astra 2 28.2°E, Turksat 3A 42.0°E"
[/LIST]

[/LIST]

**[size=+2]Introduction:[/size]**
Tvheadend is a software based TV/Radio streaming and recording server that runs on Linux/*BSD/[WSL]("https://tvheadend.org/boards/5/topics/38600")based Operating Systems that can be setup, used and maintained from a Web-interface. Its able to deliver simple media streams to any thinkable client platform or extend KODI based mediacenters with advanced PVR(Personal Video Recording) features like live TV watching/timeshift/schedule/recording using a pvr-hts (Tvheadend HTSP client) addon. However before the Web-interface of Tvheadend gives you all this easy access and control to all these media types we may have to get our hands dirty by jumping back and forward from "Terminal Bash" command-line to Tvheadend "Web-interface" to debug/test/verify diverse Tuners options and quirks, but finally if all DVB tuners / non-DVB sources are setup correctly easy Web-interface or PVR based controle is the end result!

Although Tvheadend is not region/country limited, the scope of this howto will be limited to TV/Radio broadcast technologies available in Europe specifically The Netherlands which are mainly DVB based. That means users from ATSC/ISDB technology based countries like USA/JAPAN have limited benefit of this howto. Another important limiting/extending factor in Tvheadend its experience is the "role/quality" of the Tuner "driver(s)" mostly bound to its Operating System "hardware architecture" and "kernel version" they are running on! Sounds extremely complicated, these 4 factors! I will try to explain and please try to take notice of the following paragraph(read it multiple times)!

Tuner hardware using USB/PCI-E connections needs to be initialized and driven by the system on which they are connected /installed/used on. If these tuners were intended to be run on Microsoft Windows accompanied by drivers and TV software from the manufacturer meant to be run on that same Operating System it may all behave... as expected. Well only if you indeed use specific software XP/7/8.1/10 /driver versions on specific but still common x86/amd64 hardware(not arm based Microsoft Surface tablet) all is still fine. 
But what if the manufacturer of your Tuner hardware won't deliver a Linux/BSD driver also not even talking about x86 architecture but MIPS/ARM based enigma SetopBOX or Synology NAS or Raspberry Pi's? Than your last/only hope is the so called "mediatree" driver development section of the Linux Kernel, which contain manufacturer supported but also reverse engineered drivers. Good news is that new Tuner drivers are constantly added and improved and that its design is mostly not limited to x86 CPU only, it may just work fine on a Arm/Mips CPU based machine which also happens to have a USB port or PCI(E) interface and runs Tvheadend. 
But now comes the hard part... "I'm having this Synology NAS which runs Tvheadend running Linux kernel 2.6.xxx and want to run my XBOX USB Tuner(which got supported by the mediatree of Linux Version 4.16)". Here comes another one... "I have a VU Solo engima based Satellite receiver which runs linux kernel 3.3 and wan't to add USB Hauppauge WinTv DualHD tuner supported by manufacturer since Linux Kernel 4.17". Well you just say update the Synology or VUsolo box to a recent kernel ship them with compiled kernel modules(drivers) for these wonderfull USB tuners and we are all happy!
The truth is more like this... The Synology or Vu device may use a closed source important driver for their built-in Harddisk/Network/tuner hardware which only works on older linux kernel not the new linux kernels(which may be required for exotic tuner support)... in other words these devices will almost never see a updated Linux kernel (except for the Raspberry Pi)! This is the main reason to start using Tvheadend first on systems that gets updated linux kernel easily or backported media drivers than you might learn/discover which kernel modules actually are needed to make a tuner working and finally gain the insight if its possible to use a backported kernel on your specific embedded exotic Arm/Mips based NAS/SetopBOX hardware running Tvheadend. 
I'm not saying you must use a PC with Ubuntu to use Tvheadend but it can be a quite a good step stone to understand /debug linux behaviour and than go to embedded hardware. Its a lot faster and easier to install/compile recent kernels(with tuner support) on x86/amd64 hardware than inside your Synology NAS! Also most people will have (PC/Notebook/Server) and is easy to interact/debug by keyboard*mouse/monitor with USB/PCI-(E) tuner hardware, while the embedded devices miss these accessible debug features.

People (who do not understand the limitations of the previous paragraph) may always use exterrnal Ethernet based tuner hardware like "SAT>IP" or "HDHomeRun" solutions which helps running Tvheadend on a lot of closed/limited embedded hardware that will only run old linux kernels and are not hindered by the requirement of kernel drivers. 

When the Tvheadend server is working with a single USB DVB-C tuner, a example for 24/14 continuous (rotate) recording for a single DVB-C channel will be given. Other DVB-S(2)/T(2) their diverse antenna configurations (cable / terrestrial / satellite Universal LNB+diseqc 1.0&1.1) and non-DVB tuner sources like ipcam/DV/HDV/webstreams/Alsa/Decklink/V4L2 will follow. Only parts of the Tvheadend Web-interface and Bash terminal interaction/scripts necessary to complete these goals are addressed. Initially a simple client for testing core Tvheadend functionality (tuning / streaming / recording) like Videolan(VLC) is used. Finally a complex and advanced LAN based PVR client integration of which Tvheadend is also capable of with XBMC/Kodi/otherPVR/NAS etc tablet/smart-phone/htpc features are of a second interest but will be limited addressed in part2.

**[size=+2]Installation:[/size]**
Get ubuntu linux 16.04.1:
Multiple variations of ubuntu are available, for older hardware with less supported graphics cards I advice to use ubuntu-mate desktop if you need graphical GUI based ubuntu install. You may also use the default ubuntu desktop / server / minimal as a base for this howto, but the focus will be on minimal. Remember that ubuntu 16.04 LTS comes with linux kernel 4.4.x, this is the default I assume you to use if you used the mini-iso installer. If you used updated/desktop installers like 16.04.2/16.04.3 you'll be running linux kernel 4.8.x / 4.10.x which the latter opens up possibilities for fixing USB DVB-C tuners detection for Astrometa with high frequencies patch and Microsoft Xbox tuner! Right now it is possible to stay on kernel 4.4.x and use backported drivers for both Xboxtuner and Hanftek T2Hybrid including high frequency patches. If you already run a linux distro open up a terminal and get started for downloading and preparing a installer(macOS/Windows users may need certain tools to write the iso file to a USB thumbdrive or CD/DVD):

```

#download ubuntu mini iso amd64
wget http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/mini.iso

#burn iso to USB stick/thumbdrive, warning choosing wrong drive may destroy data!
sudo dd if=mini.iso of=/dev/sdX #change 'X' with the block device letter that corresponds with your usb disk

```

Install ubuntu linux:
At this point you probably have a USB thumbdrive with Ubuntu Linux installer, make sure your new Tvheadend server/pc will boot from USB otherwise burn the ISO to a CD/DVD and start from DVD for Ubuntu linux install! Albeit this type of advanced mini install can be accomplished by mostly pressing "enter" you have to keep focus on the following 5 configuration steps!

```

#remember the username/password you setup

#setup network automatically by dhcp, no function internet means no function ubuntu install

#setup harddisk partition in Guided way using entire disk(erases al data) and remember device name aka /dev/sdb /dev/sdc!

#near the end of the install in TaskSEL choose with SPACEBAR not ENTER:
*standard system utilities
*Ubuntu MATE minimal installation #if you want a Desktop/GUI
*OpenSSH-server

#at the end install Grub bootloader on the disk you selected earlier for ubuntu install, not the USB drive you started the install from!
/dev/sdb #for instance


```

Post Install:
If you rebooted after install and you only see a Ubuntu logo or terminal with some bootlog messages, try pressing CTRL+ALT+(F1-F7) and see if you get a tty login to! If you see a login screen enter the username and password you setup during ubuntu install and continue the following steps from the terminal.

Setup Networking:
After install of Ubuntu Linux on your server, my advise is to setup your network connectivity with static parameters in case this machine needs to be remotely accessible without a Monitor, you can do this in GUI (network manager applet) or CLI (overrules) open terminal and type:
```

sudo ifconfig #lookup ethernet interface name, mine is enp0s10
sudo nano /etc/network/interfaces
###copy paste following codeblock and adjust according to your network
auto lo
iface lo inet loopback

auto enp0s10
iface enp0s10 inet static
address 10.100.1.100
netmask 255.255.255.0
gateway 10.100.1.1 
dns-nameservers 10.100.1.1
### press CTRL + X than Y than Enter will save changes to /etc/network/interfaces textfile

#if you have not installed ssh during ubuntu install, install it now so remote administration is possible
sudo apt-get install openssh-server

```

Local/Remote administration:
From now on I assume you are able to login on a terminal on this new Ubuntu Linux Tvheadend server albeit local from its desktop (if it is running one), or remote using ssh to further complete the upcomping terminal hacking parts from this howto!

Install Tvheadend 4.2:
We will install [Tvheadend]("https://tvheadend.org/projects/tvheadend/wiki/AptRepositories") before "plugging in" the tuner hardware, because TVheadend probes/starts the tuner devices in a way we are able to detect/debug specific tuner shortcomings and fix them like missing firmware or wrong device id's. Remember, we are just installing Tvheadend, not yet configuring its tuners/network/muxes/services/channels etc, this will be addressed later. For this howto on ubuntu 16.04.1 xenial amd64 we still have choice for "unstable" & "stable" 4.2 builds from the Tvheadend repository. To keep up with development choose "unstable", otherwise choose "stable". Open a terminal and type:

```

sudo apt-get -y install coreutils wget apt-transport-https lsb-release ca-certificates
sudo wget -qO- https://doozer.io/keys/tvheadend/tvheadend/pgp | sudo apt-key add -

sudo sh -c 'echo "deb https://apt.tvheadend.org/stable $(lsb_release -sc) main" | tee -a /etc/apt/sources.list.d/tvheadend.list'
#sudo sh -c 'echo "deb https://apt.tvheadend.org/unstable $(lsb_release -sc) main" | tee -a /etc/apt/sources.list.d/tvheadend.list'

sudo apt-get update
sudo apt-get install tvheadend #set admin username/password

#un:tvheadmin
#pw:tvhepassw

#notice the popup with tvheadend address/portnumber 9981

sudo systemctl start tvheadend.service

```

[i]
The use of a package manager in Ubuntu APT+deb helps us not only with installing Tvheadend but also with integrating it as a self starting service and configuring some settings like specific Linux user HTS which has its on /home/HTS folder containing the configuration files and recordings set by the Tvheadend webinterace! If you ever need to debug Tvheadend the hard way and understand whats happening after install and run it mannualy look here:

```

sudo systemctl stop tvheadend.service
sudo mkdir /home/$testuser/tvheadendtest
sudo /usr/bin/tvheadend -C -c /home/$testuser/tvheadendtest -u root -g root #the user that actually runs tvheadend also need access to /dev/dvb hardware!!!

```
[/i]

Setup DVB Tuner(s):
Except for the SAT>IP & HDHomeRun based tuners or ip streams, all other tuners will depend on drivers which are linux kernel version specific in some cases. 
 
We start with a Dutch DVB-C service provider "Ziggo" using the following USB Elgato EyeTV Hybrid tuner (other tuner types and service provider networks will follow).  This tuner works ootb with DVB-C but is missing firmware for some of it features (probably DVB-T(2)/analog tuning/CVBS/S-video). I advice to plugin/install the DVB tuner hardware only on request by this howto and after Tvheadend is installed to simplify debugging. So first open a terminal and type:

```

lsusb
#plugin you usb tuner

lsusb #see this device id?
## 0fd9:0018 Elgato Systems GmbH EyeTV Hybrid

dmesg# see missing firmware?
[uptime...] usb 2-3: Direct firmware load for dvb-usb-terratec-htc-stick-drxk.fw failed with error -2
[uptime...] drxk: Could not load firmware file dvb-usb-terratec-htc-stick-drxk.fw.

#direct download missing firmware
wget https://github.com/OpenELEC/dvb-firmware/raw/master/firmware/dvb-usb-terratec-htc-stick-drxk.fw
#wget https://github.com/mdamt/linux-firmware/blob/master/dvb-usb-terratec-h5-drxk.fw

#install missing firmware
sudo cp dvb-usb-terratec-htc-stick-drxk.fw /lib/firmware/
#sudo cp dvb-usb-terratec-h5-drxk.fw /lib/firmware/

#restart tvheadend to make firmware available
sudo systemctl restart tvheadend.service

```

Storage preparation:
If you want Tvheadend to record a single SD TV+RADIO channel continuously 24/7 for 2 weeks and rotate (delete everything older than 14 days), alot of storage is needed. A single 1TB disk is enough to hold the OS and Media storage. Depending on your disk usage/requirments the following examples will defer. 

```

#check which partition/disk has most storage space
df -h #this shows already available volumes to the system
sudo parted -l #this show raw volumes/partitions and sizes

#disk1 partition 4 is gonna be used for media storage in my example
sudo mkfs.ext4 /dev/sda4 -L mediastorage #this will format partition 4 on disk a and label it "mediastorage"

#mediastorage volume will be available in this location
sudo mkdir /mnt/mediastorage

#mount mediastorage at boot so Tvheadend can record to it
sudo nano /etc/fstab
### copy code below at end off file
LABEL=mediastorage 			/mnt/mediastorage ext4 defaults 0 0 
### press CTRL + X than Y than Enter will save changes 
sudo mount -a #will mount (make available) mediastorage to the system

#prepare Tvheadend default record folder
sudo mkdir /mnt/mediastorage/tvherecordings

#fix permisions so every can read/write including webservice
sudo chmod -R 777 /mnt/mediastorage

#make new mounted volume available for Tvheadend
sudo systemctl restart tvheadend.service

```

[s]Continuous/Rotate recording preparation:
Since Tvheadend <4.2 will not auto delete recordings (only its name listings log) we will have to use cron/find/rm for schedule/detecting/removing media files older than 14 days every hour:

```

sudo nano /etc/cron.hourly/cvdm-24x24-tvhe-remove 
### copy code below
#!/bin/bash
find /mnt/mediastorage/tvherecordings/24-14/* -type f -mtime +13 -delete
### press CTRL + X than Y than Enter will save changes 

sudo chmod +x /etc/cron.hourly/cvdm-24x24-tvhe-remove

```
[/s]

**Setup Tvheadend Webinterface:**
During the install of Tvheadend earlier you may noticed that the service is running on port 9981. Therefor you can access the webinterface on [127.0.0.1:9981](127.0.0.1:9981) (this link will only work if you are using a desktop session on the same machine Tvheadend server is running on). From a remote device on the network you should use the static IP ADDRESS you setup up earlier followed by :9981 port number. 
A small summary, first we will Cancel away the "Configuration Wizard" popup that comes with version 4.2 for Tvheadend, than we make you aware on the debug section of the Web-interface, than make you aware of view levels that affect the options available to you in webinterface.
Second we will add a Dutch DVB-C network service provider for Ziggo FreeToAir radio/television (SD channel order uses 4444 id).  
Third we will link available USB DVB-C tuner hardware to the service provider network we just made, and if all goes well, it will start discovering muxes and services/channels.
Fourth step will make the scanned/tuned services available as channels(mapping), doing this makes the channels available for recording/scheduling/third party PVR clients etc. 

Open a Web Browser and login to the Web-interface of Tvheadend using the "ipaddres:9981" following your username:tvheadmin and password:tvhepassw and Cancel the Popup Wizard!

Log for easy debug:
In the extreme lower right corner of the webinterface there is a icon of two upfacing angled brackets ^^ which opens up the log and is very usefull for debuging TVheadend its activity (or lack of). Since Tvheadend 4.2 annoying VIASAT EPG log messages are gone! [s]
The EPG grab of viasat baltic is hardcoded and spoils the log, disable 

```

Configuration > Channel/EPG > EPG Grabber
    VIASAT:Baltic uncheck #or any other non usable grabber
save

``` [/s]

Web-interface looks different:
A fresh install of Tvheadend most of the times give a webinterface with access to all the options discussed here, however sometimes different type of admin accounts for the webinterface got setup on different linux distributions. Meaning your view of the webinterface may look different or very limited (not even a Configuration Tab). If you look in the right corner or middle of each setup TAP there is a "Help" but also "View Level" button. This last button gives access to simple/advanced/expert levels of viewing/editing options.  In the Configuration > User > Access Entries "tab" you find options to make these view levels persistent to each type of user or admin account!

Setup Ziggo service provider network:

```

Configuration > DVB Inputs > Networks
                                                         Add Network: DVB-C
                                                         Network Name: ziggofta
                                                         Pre-defined muxes: Netherlands: nl-Ziggo
                                                         Network ID (limit scanning): 4444 #5555 for HD encrypted
                                                         Network discovery: New muxes + changed muxes
create


```

Setup Telfort (Fiber/KPN/XS4all) service provider network:
[https://www.telfort.nl/persoonlijk/service/dvbc-ontvanger-instellen.htm](https://www.telfort.nl/persoonlijk/service/dvbc-ontvanger-instellen.htm)

```

Configuration > DVB Inputs > Networks
                                                         Add Network: DVB-C
                                                         Network Name: telfortfta
                                                         Network ID (limit scanning): empty #or 1000 depending on City/Region
create

Configuration > DVB Inputs > Muxes
                                                         Add Mux
                                                         Network: telfortfta
                                                         Frequency: 304000000
                                                         Symbolrate: 6875000
                                                         Constellation:QAM/64
create


```

Tune/Scan services:
Before we can tune services on a network, we have to link the service provider network (made earlier) to a available DVB-C tuner.
```

Configuration > DVB Inputs > TV adapters
                                                         DRXK DVB-C DVB-T #0 : DVB-C #0
                                                         Enabled:* checkbox
                                                         Networks:ziggofta or telfortfta
save

Configuration > DVB Inputs > Networks
"select your linked network and force scan"

```

Test/View/Listen stream "Services" and "map" them as RADIO / TV "Channels":
As soon as pressing save in the last step, or a couple of minutes later (or Tvheadend service restarts on some systems) you'll see that in the tab "Configuration > DVB Inputs > Networks", the "ziggofta" network is discovering muxes and services(11th column), these numbers will increase until muxes left scanning will be zero 0 see "Scan Q length"(13th column). When "Network discovery: New muxes + changed muxes" has been checked, the number of muxes might increase during search which might increase the amount of valid services found.

The latter "services" will be the radio/tv channels which will need to be mapped to channels before they can be used by Tvheadend its (internal)recording or external streaming clients (XBMC/KODI/etc). This is the coolest (or most frustrating part in case of failure) where you actually see the capabilities and strength of Tvheadend come alive. First we will look for some familiar service names (channel names) and see if they will tune/play with a simple player like VLC.

```

Configuration > DVB Inputs > Services
#Use alphabetical ordering, service numbers or filters to find a serivce name for testing/viewing.
#On each service row there is a small URL (playback icon) on the veryleft of the screen.
This will download a single item play-list (with includes a hashed user credentials from the adminuser) which can be opened with Videolan/VLC so you can verify if the channel is working!

#find / select preferred channels (multiple rows use SHIFT or CTRL) press "Map Selected" than "Map Selected Services"
Besides creating common tags (SDTV/HDTV/RADIO) also create networkname tags which may ease linking specific users/usergroups to available DVB TV-adapters. 
Create network name tags:*Checkbox

*As you see Tvheadend is also able to probe services for audio/video content on a automated way by itself, this speeds up adding thousands of services from multiple satellites when using map all services. 

```

Prepare storage location:
```

Configuration > Recording > Digital Video Recorder Profiles
(Default Profile)
	DVR Log Retention Time (days):14
        Recording System Path: /mnt/mediastorage/tvherecordings
	File Permissions (octal, e.g. 0664): 0777
	Directory Permissions (octal, e.g. 0775):0777
        Skip Commercials: unCheck

        Make Subdirectories Per Channel:*Check

        Include Channel Name In Filename:*Check

        Remove All Unsafe Characters From Filename:*Check
        Replace Whitespace In Title with '-':*Check
        Use Windows-compatible filenames:*Check
save

```

Continuous/Rotate recording preparation:
Tvheadend 4.2 comes with built-in file retention/delete method, this replaces the cron scheduled older than 2 weeks remove "cvdm-24x24-tvhe-remove" script! However it is necessary  that during the setup of the autorec entries the correct DVR profile gets selected which has the "log/file removal" enabled!

```

Configuration > Recording > Digital Video Recorder Profiles
(Default Profile)
	DVR log retention period: "On file removal"
        DVR file retention period: "2 weeks"

```

Continous/Rotate recording entries:
You have to repeat the next code step 24* times to make a schedule for 24/7 days recording, just change the name and Start/Stop times accordingly, two examples will be given.

```

Digital Video Recorder > Timers
Add entry
   Enabled: *
   Name:tv-bbb-2300-2400
   Title:TV-%F_%R
   Directory:24-14
   Channel:bbb
   Start:23:00
   Stop:00:00
   Week Days:Mon,Tue,Wed,Thu,Fri,Sat,Sun
   Priority:Normal
   Retention:0
   DVR Configuration:(Default Profile)
   Comment:
create

```

```

Digital Video Recorder > Timers
add entry
Enabled: *
 
Name:tv-bbb-2400-0100
Title:TV-%F_%R
Directory:24-14
Channel:bbb
Start:00:00
Stop:01:00
eek Days:Mon,Tue,Wed,Thu,Fri,Sat,Sun
Priority:Normal
Retention:0
DVR Configuration:(Default Profile)
Comment:
save

```

At this point, you should have a working 2 week continuous/rotate recording schedule for a DVB-C based channel. If not, carefully (re)read again or ask a question in this topic?

**[size=+2]Setup more DVB tuners:[/size]**
Since the release of Ubuntu 16.04 a lot have happened on the "mediatree" driver side. This [mediatree]("https://git.linuxtv.org//media_tree.git") is part of the linux kernel which gives increasing compatibility for media related hardware like DVB tuners. However these mediatree improvements don't come automatically/easy available to our current/dated Ubuntu 16.04 with its 4.4 LTS linux kernel version which was the linux version I focus on for this tutorial. To get most new/exotic DVB tuners working there are multiple options to get newer kernel modules / mediatree build into your server, see below:

[list]
[*] Use a newer kernel supported by Ubuntu using its [HWE LTS]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") upgrade stack. This kernel version (4.15) might not be new enough to support the tuners described in this tutorial.

[*] Use a less supported but still Ubuntu build kernel with relatively easy and assistence of [ukuu]("https://launchpad.net/~teejee2008/+archive/ubuntu/ppa"). This ppa gives a CLI and GUI option to install and revert newer kernels!

[*] Hauppauge sponsored Ubuntu kernel builds with backported [mediatree]("https://launchpad.net/~b-rad/+archive/ubuntu/kernel+mediatree+hauppauge") supporting most of the LTS versions.

[*] Custom patch and compile linux kernel modules yourself, like I did in the past for this tutorial but will be [s]striked[/s] and not get improvements!
[/list]

The option that mostly matches my personal and Ubuntu its LTS character is the 3rd one by Hauppauge, although not updated that frequently it will keep your Ubuntu Kernel version the same as the one you started from in the beginning but with a updated/backported mediatree for improved tuner support! 

**DVB-C**

Only the minimal steps to get the tuner hardware functional are given, since a DVB-C service provider with channel support has been described earlier in this tutorial!

2040:1605 Hauppauge WinTV-HVR 930C-HD
This USB tuner is just missing firmware and works fine after making it available. Just open a terminal: 

```

lsusb
#plugin your usb tuner

lsusb #see this device id?
##2040:1605 Hauppauge

dmesg #see problems with drxk module about missing firmware?
##[ uptime...] usb 1-5: Direct firmware load for dvb-usb-hauppauge-hvr930c-drxk.fw failed with error -2
##[ uptime...] drxk: Could not load firmware file dvb-usb-hauppauge-hvr930c-drxk.fw.
##[ uptime...] drxk: Copy dvb-usb-hauppauge-hvr930c-drxk.fw to your hotplug directory!

#direct download missing firmware
wget https://raw.githubusercontent.com/OpenELEC/dvb-firmware/master/firmware/dvb-usb-hauppauge-hvr930c-drxk.fw

#install missing firmware
sudo cp dvb-usb-hauppauge-hvr930c-drxk.fw /lib/firmware/

#restart Tvheadend to reprobe
sudo systemctl restart tvheadend.service

#dmesg again to see that firmware gets loaded this time
dmesg

```

2040:0265 Hauppauge WinTV-DualHD 01590:
Since this tuner requires firmware and a recent linux 4.17.x kernel, I noticed that a [Hauppage sponsored project]("https://github.com/b-rad-NDi/Ubuntu-media-tree-kernel-builder") makes a [PPA]("https://launchpad.net/~b-rad/+archive/ubuntu/kernel+mediatree+hauppauge") available which not only includes (backported) Hauppauge drivers for current Ubuntu releases but also includes other recent linux mediatree drivers for non-Hauppauge hardware. This makes the extensive cumbersome custom kernel build options I described earlier in this tutorial absolete! Just a side note it still doens't include most of the required firmware for Hauppauge devices, but maybe that changes in future with "linux-firmware-hauppauge".

```

#adding a non default ubuntu kernel affects your ubuntu support status!
sudo apt-get -y install software-properties-common
sudo add-apt-repository ppa:b-rad/kernel+mediatree+hauppauge
sudo apt-get update

sudo apt-get -y install linux-image-mediatree
sudo apt-get -y install linux-headers-mediatree

#direct download missing firmware
wget https://github.com/OpenELEC/dvb-firmware/raw/master/firmware/dvb-demod-si2168-b40-01.fw

#install missing firmware
sudo cp dvb-demod-si2168-b40-01.fw /lib/firmware/

#reboot to make newer kernel active
sudo systemctl reboot;exit

#after reboot it shows up in Tvheadend Web-interface as multiple:
Silicon Labs Si2168 #1 : DVB-C #0
Silicon Labs Si2168 #2 : DVB-C #0

```
*You have to reboot your server to let it boot with the updated kernel, than your new tuner hardware should showup in Tvheadend.*

15f4:0131 HanfTek 2014 revision 
The following cheap (18 euro) and easy available USB 2.0 DVB-C tuner "Astrometa dvb-t2" has seen some improvement since linux kernel 4.4. There was a bug and a fix for not reading its firmware via i2c reliable, but there are still issues if you prefer higher frequencies to work reliable search striked part!

```

#don't plug/install your tuner hardware yet...
lsusb #this will show current USB devices
lspci #if using a pci device...
dmesg #this will show current kernel driver/debug messages 
#you want this to detect/see the change in devices/modules/drivers before/after you install a certain type of tuner

#plugin your usb tuner
lsusb #see this device id?
##15f4:0131 HanfTek
dmesg #see problems with mn88473 module about missing firmware?
##[ uptime...] mn88473 5-0018: Direct firmware load for dvb-demod-mn88473-01.fw failed with error -2
##[ uptime...] mn88473 5-0018: firmare file 'dvb-demod-mn88473-01.fw' not found

```

If you noticed "failed / not found" you are spot on in resolving the error by just submitting the correct firmware file. Although tuners might show up in Tvheadend webinterface if you we're looking already, they might not function fully. For instance DVB-T may be working on this USB tuner, but DVB-C is not until we download the firmware...

```

#download missing firmware
wget http://palosaari.fi/linux/v4l-dvb/firmware/MN88473/01/latest/dvb-demod-mn88473-01.fw

#install missing firmware
sudo cp dvb-demod-mn88473-01.fw /lib/firmware/

#restart Tvheadend to retry/probe hardware
sudo systemctl restart tvheadend.service

dmesg #see success/problems 
##[ uptime...] mn88473 5-0018: downloading firmware from file 'dvb-demod-mn88473-01.fw'
##[ uptime...] mn88473 5-0018: firmware parity check succeeded=0x20

#note some revisions come with a Panasonic mn88472 which requires dvb-demod-mn88472-02.fw
wget http://palosaari.fi/linux/v4l-dvb/firmware/MN88472/02/latest/dvb-demod-mn88472-02.fw
sudo cp dvb-demod-mn88472-02.fw /lib/firmware/

```

If you are lucky you will see "downloading.../succeeded" but it will not always be the case because there is a kernel bug in linux kernel 3.19<>4.7 related to the i2c speed which will affect firmware download into the usb tuner, therefor it will not always succesfully load firmware at 1st attempt. 
Skip the following striked block and upgrade to a newer kernel by following the instructions for the 2040:0265 Hauppauge!
[s]restart Tvheadend multiple times until firmware loads successfully with the following script.

```

sudo nano /home/hts/usb-checkfirmware.sh 
### copy following code ###
#!/bin/bash
Service=tvheadend.service
function diditsucceed {
if (dmesg | grep -v grep | grep "firmware already running")
#succeeded=0x20
#mn88473 9-0018: firmware already running
then
echo "mn88473 firmware loaded correctly, dvb-c available in tvheadend"
exit 0
else
echo "mn88473 firmware missing/broken, dvb-c unavailable in tvheadend"
sleep 2
#/etc/init.d/$service start
echo "mn88473 retrying firmware load... by (re)starting tvheadend "
sudo systemctl restart $Service
sleep 2
echo "mn88473 retrying firmware load... waiting 10 seconds "
sleep 10
echo "mn88473 retrying firmware load... "
diditsucceed
fi
}
diditsucceed

#while true; do
#	dmesg | grep -v grep | grep "succeeded=0x20"
#done

### press CTRL + X than Y than Enter will save changes 

sudo chmod +x /home/hts/usb-checkfirmware.sh

```

By adding the following script to '/etc/rc.local' it will (re)load Tvheadend at boot until it detects the firmware for the USB DVB-C tuner has loaded correctly!

```

sudo nano /etc/rc.local 
### copy following line ### above exit0 line
nohup /home/hts/usb-checkfirmware.sh >/dev/null &
### press CTRL + X than Y than Enter will save changes 

```[/s]

[s]
Option 4 Custom Kernel Module Patch (deprecated)
For fixing high frequency tuning and increasing reception errors on these higher frequencies it may be a good idea to patch this in the current kernel. Its still not perfect, commit 275350a [media] r820t: enable flt_ext_wide for SYS_DVBC_ANNEX_A standard is kinda strange since it actually patched the ISDB-T part instead of the DVB-C annex A vs C part which it title refers to, besides the other suggested good patch by &#1069;&#1076;&#1091;&#1072;&#1088;&#1076; &#1052;&#1103;&#1075;&#1080; addressed in the patchfile attachment. To re-compile/build the current kernel it takes around 20GB, alot of CPU compile time and you have to do it manually for every system upgrades which ships with a newer kernel. But its just a few steps to type in the terminal. First we add the ability to the system to download sources from Ubuntu "apt" this can be done via GUI "Software & Updates" by checking a checkbox or CLI. Second we will get the right building tools. Third get the Ubuntu kernel source for the current version, fourth prepare and five patch it and finally compile and install if successful.

[ATTACH]277249[/ATTACH]
```

#1st add sources to apt packaging system
sudo nano /etc/apt/sources.list
#uncomment and change the line with the first instance of '# deb-src' to 'deb-src' 
CTRL+X save and exit

#make package sources available to apt
sudo apt-get update

#2nd install building tools and components (make sure you are running the current kernel version you wish to alter)
sudo apt-get build-dep linux-image-$(uname -r)

#3rd get kernel sources around 20GB when building (without sudo!)
apt-get source linux-image-$(uname -r)
cd linux*
#4th prepare it (same kernel config as before, no need for new one), change name
chmod a+x debian/rules
chmod a+x debian/scripts/*
chmod a+x debian/scripts/misc/*
fakeroot debian/rules clean
#change / increase the version number so the custom kernel looks distinguishable by apt just add '+test01'
nano debian.master/changelog #example edit add '+test01'
--------------------------------------------------------------------------------------------
linux (4.4.0-97.120+test01) xenial; urgency=low

  * linux: 4.4.0-97.120+test01 -proposed tracker (LP: #1718149)
    -Write/Address the changes here you want to
--------------------------------------------------------------------------------------------
CTRL+X save y and exit

#5th download  and unzip patch from thread attachment[ATTACH]277249[/ATTACH] and put it in the current linux-* folder
patch -p0 < ruN-p0-multifix.patch

#build and wait for a small hour (old quadcore with SSD) 
fakeroot debian/rules binary-headers binary-generic binary-perarch &>> ../buildlog+test01.txt

#install/test the 4 deb files containing the words image&headers and reboot
cd ../
sudo dpkg -i linux-image*.deb linux-header*.deb

```
 
By upgrading the linux kernel version to 4.10.x the i2c firmware loading issue will be gone. Remember that upgrading the linux kernel and its modules will have a strong impact on all other functioning hardware in your server for instance network/wireless/sound/videocard/storage/usb/etc drivers. This means that a upgraded kernel may also break support of a previously working device because of a regression. If newer drivers/fixes are not backported to older kernel version you have to upgrade but it seems that although the firmware loading issue is gone, its performance seem more unstable than on 4.4.x even with high frequency fix!
```

uname -a #shows current linux kernel version
sudo apt-get install --install-recommends linux-generic-hwe-16.04 #if running a desktop on your tvheadend server also install "xserver-xorg-hwe-16.04"
sudo reboot

```

Still compared to the Microsoft Windows driver of the Astometa DVB T2, one issue remains with the current linux tuner driver which is an issue with tuning/scanning high frequencies/muxes leading to no channels or high error rates. This is however fixable by building you're own linux kernel module from the V4L2 media_build on linux kernel version 4.10.x and applying the r820t tuner patch suggested by &#1069;&#1076;&#1091;&#1072;&#1088;&#1076; &#1052;&#1103;&#1075;&#1080;. Remember that custom patched linux kernel modules will break on "apt" dist-upgrades, this means that you have to rebuild these driver modules again after each kernel upgrade(or create a DKMS script...)!
```

#check your kernel version and if upgrade if lower than 4.10 see previous block
uname -a

#install packages for building custom updated v4l media_build linux kernel modules!
sudo apt install make gcc git patch patchutils libproc-processtable-perl bc libncurses5-dev libdigest-sha-perl

#clone media_build and patched xbox sources
mkdir -p xboxtuner/attempt01
cd xboxtuner/attempt01
git clone git://linuxtv.org/media_build.git
git clone --depth=1 https://github.com/trsqr/media_tree.git -b xboxone ./media

#reset&build media_build
cd media_build
git reset --hard 258461908cbb83a4d2f869f0f70b6b511fce6baa #since 2017-08-08 commits break building V4L2/LINUX
#patch Astrometa DVB-T2 tuner for high frequency support which also affects DVB-C
sed -i '0,/air_cable1_in = 0x60;/s//air_cable1_in = 0x00;/' ../media/drivers/media/tuners/r820t.c

#be aware this will build modules for the kernel you are currently running NOW, so if you upgraded the kernel but not rebooted yet its time to reboot now otherwise it will build modules for the older kernel 
make dir DIR=../media
make distclean
cp ../media/mm/frame_vector.c v4l/ #otherwise building might hang on this!
make -j4 #adding -j4 will make use of the quadcore and decrease build time user higher number for more cpu cores! 

#force install build kernel modules
sudo make install

#download the needed firmware
cd /lib/firmware
#dvb-usb-dib0700-1.20.fw firmware is packaged in "linux-firmware" 
sudo wget http://palosaari.fi/linux/v4l-dvb/firmware/MN88472/02/latest/dvb-demod-mn88472-02.fw

#finally reboot and fixed astrometa dvb-t2 higher frequencies for DVB-C and XBOX USB tuner will be available in tvheadend!

``` 

[/s]

15f4:0135 HanfTek 2015 revision
It really requires a newer kernel (see 2040:0265 Hauppauge) besides the firmware(see 15f4:0131 HanfTek 2014 revision). After these requirments are met the adapter should show up in Tvheadend.

045e:02d5 Microsoft Corp. Xbox One Digital TV Tuner:
Thanks to the continuous effert of the following developers on the tvheadend forum  [thread]("https://tvheadend.org/boards/5/topics/13685?r=27555#message-27555") (Olli Salonen, Tux User, Gavin Ridgway, Sky Anakin, Andras Farago, and ...) there is a mainline linux kernel conform driver module (still testing/debugging). For now it seems that DVB-T(2) is working well even with HD but DVB-C has continuity/transport/data errors just like most other Panasonic mn88742/3 based devices. It is unknown yet if the problem is in the mn88472, tda18250 or dib module code.

To get this tuner working, follow the steps from the 2040:0265 Hauppauge adapter and install following firmware, after a restart it should show up in Tvheadend!
```

lsusb
#notice 
##045e:02d5 Microsoft Corp. Xbox One Digital TV Tuner:

#besides a recent 4.16x kernel the x-box tuner requires firmware
wget http://palosaari.fi/linux/v4l-dvb/firmware/MN88472/02/latest/dvb-demod-mn88472-02.fw
sudo cp dvb-demod-mn88472-02.fw /lib/firmware/

#dib0700-1.20.fw is shipped by default in Ubuntu but in debian requires package "linux-firmware"

#after reboot is shows up in Tvheadend Web-interface as:
Panasonic MN88472 #1 : DVB-C #0

```

HDHomeRun Expand/HDHR3-4DC:
To configure a HDHomeRun DVB-C tuner is very similar to upcoming networked "SAT>IP" tuner. It will need avahi/bonjour/zerconf support on the ubuntu Tvheadend server to get detected by Tvheadend and it requires Tvheadend to be compiled with "libhdhr" support. The good news is that most versions of Tvheadend available have this libhdhr support compiled in. Therefor your "HDHomeRun Expand/HDHR3-4DC" may show up as 4 tuners just after installing Tvheadend, without any linux kernel module fiddling. Like "SAT>IP" tuners keep in mind that other devices in your network besides Tvheadend server may block/prevent tuner usage, for instance a HDHomerun App on a Tablet/Smartphone/SetopBOX may use 1 out of 4 tuners without noticing it(EPG update/etc in background)!

**DVB-S2**
This time we will setup DVB-S(2) tuner in Tvheadend using SAT>IP protocol with a Telestar Digibit R1.
It is important to use a recent firmware for the SATIP device, Inverto currently has the latest version of 'idl4k' which is compatible with TeleStar Digibit R1, also use a recent Tvheadend version 4.2.x. Some might even need to use a alternative firmware like satip-axe from Perexg see (github link see table) for improved usage/stability. Without these optimized firmware versions, tuners will work inconsistent or have bad reception, less channel search or tuning results. Connect the Digibit R1 in the same LAN as the Tvheadend server and make sure no other SAT>IP clients in the network use this SAT>IP box directly!!! I'm gonna say it again make sure your Tablets/SmartPhones/SmartTV/mediaplayers don't use the tuners directly available on the Digibit R1, otherwise Tvheadend will perform inconsistent!!! 
Depending on the use case, this SAT>IP device can be used in 'Quatro/unicable' mode (1 satellite 4 transponders) or 'quad' mode which is useful for single or more transponders on multiple satellite of choice. Keep in mind that diseqc switches can be used but that may only be useful if you want view/record 'more' than 4 different satellites or record from 4 transponders at the same time on the same / multiple satellite(s). One nice thing about this SATIP-tuner is that it requires no drivers from the Tvheadend server side and that it shows workable diseqc 1.0  capabilities from the start.

```

Configuration > DVB Inputs > Networks
                                                         Add Network: DVB-S
                                                         Network Name: satiptuner1-AA-astra192
                                                         Pre-defined Muxes: > 19.2E:Astra
                                                         Orbital Position:19.2E : Astra 1KR/1L/1M/1N
create

repeat these steps for the other 2-4 SAT>IP tuners (when using diseqc AA-AB-BA-BB, also create seperate networks for each tuner its diseqc position)!


```

After adding a service provider network, we need to link it to its corresponding correct SAT>IP tuner and diseqc position (we use Technisat multitenne diseqc layout 19.2e 13e 23.5e 28.2e) and enable its tuner and position.

```

Configuration > DVB Inputs > TV adapters
DIGIBIT-MACADDRESS:SAT>IP - ipadress
                               SAT>IP DVB-S Tuner #1 (ipadress)
                                                          Select it and thick 'enable' checkbox
save

Configuration > DVB Inputs > TV adapters
DIGIBIT-MACADDRESS:SAT>IP - ipadress
                               SAT>IP DVB-S Tuner #1 (ipadress)
                                                          Position #1 (AA)
                                                                                          Enabled: * checkbox
                                                                                          Networks: satiptuner1-astra192
                                                                    
save

repeat these steps for Tuner #2-4 and its corresponding diseqc positions

```

Why create different Networks for each Tuner/Diseqc position? Well if you want Tvheadend to be a consistent streaming server for more users than you have physical tuners, like 100 clients you may find it useful to 'map' only channels from within a single transponder to a specific network linked to a specific tuner using multiple tuners(each tuner hosting a couple of channels). This will limit to total number of different channels for each user, but will maximize those channels available to all users at all time!

Setup DVB Tuner(s):
This time we will setup a dual DVB-S(2) pci-e tuner, a "TBS 6981 DVB-S2 Dual Tuner Card" for use with Tvheadend. First will determine which exact card is available in the server by opening a terminal and typing:

```

#lookup the device on the pcibus
lspci -v #shows pci devices

#lspci -v output
#02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)
#	Subsystem: Device 6981:8888
#	Flags: bus master, fast devsel, latency 0, IRQ 16
#	Memory at dfa00000 (64-bit, non-prefetchable) [size=2M]
#	Capabilities: <access denied>
#	Kernel driver in use: cx23885
#	Kernel modules: cx23885

lspci -vbn #shows specific device-id

#lspci -vbn output
#02:00.0 0400: 14f1:8852 (rev 04)
#	Subsystem: 6981:8888
#	Flags: bus master, fast devsel, latency 0, IRQ 11
#	Memory at dfa00000 (64-bit, non-prefetchable)
#	Capabilities: <access denied>
#	Kernel driver in use: cx23885
#	Kernel modules: cx23885

dmesg #will show which driver module got loaded and which adapter & frontend number is used

#dmesg outp
[    6.181605] cx23885 driver version 0.0.4 loaded
[    6.181941] CORE cx23885[0]: subsystem: 6981:8888, board: TurboSight TBS 6981 [card=40,autodetected]
[    8.122353] cx25840 9-0044: cx23885 A/V decoder found @ 0x88 (cx23885[0])
[    8.789986] cx25840 9-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
[    8.805217] cx23885_dvb_register() allocating 1 frontend(s)
[    8.805222] cx23885[0]: cx23885 based dvb card
[    8.808577] cx24117 8-0055: creating new instance
[    8.808585] i2c i2c-8: cx24117: Attaching frontend 0
[    8.808589] DVB: registering new adapter (cx23885[0])
[    8.808594] cx23885 0000:02:00.0: DVB: registering adapter 3 frontend 0 (Conexant CX24117/CX24132)...
[    8.809065] cx23885_dvb_register() allocating 1 frontend(s)
[    8.809069] cx23885[0]: cx23885 based dvb card
[    8.809074] cx24117 8-0055: attaching existing instance
[    8.809077] i2c i2c-8: cx24117: Attaching frontend 1
[    8.809080] DVB: registering new adapter (cx23885[0]
[   26.670038] i2c i2c-8: cx24117_load_firmware: FW version 1.44.95.2
[   26.670053] i2c i2c-8: cx24117_firmware_ondemand: No firmware uploaded (timeout or file not found?)


```

As you may have noticed in the 'dmesg' output, the driver complains about missing firmware. To get this dual tuner working, you have two options use the opensource driver or the proprietary one. We choose the easiest option (opensource) although this driver lacks blindscan/spectrum analyzer support. We will just download the firmware and put it in the right location:

```

#download prestripped firmware from prorietary windows/linux driver
wget https://github.com/OpenELEC/dvb-firmware/raw/master/firmware/dvb-fe-cx24117.fw

#copy firmware to system lib firmware folder
sudo cp dvb-fe-cx24117.fw /lib/firmware/

#restart tvheadend
sudo systemctl restart tvheadend.service

#look at dmesg output for success loading firmware
dmesg

#dmesg output
#[   26.670038] i2c i2c-8: cx24117_load_firmware: FW version 1.44.95.2
#[   26.670053] i2c i2c-8: cx24117_firmware_ondemand: Firmware upload complete


```

This DVB-S(2) tuner did already show up 2 times in Tvheadend webinterface as "Conexant CX24117/CX24132 : DVB-S #0", but this time its actualy working. Add any service network provider diseqc switch combination as described before.

Setup DVB Tuner(s):
This time we will setup a DVB-S(2)ci pci tuner, a less ancient Technotrend s2-3200 (CI) for use with Tvheadend. First will determine which exact card is available in the server by opening a terminal and typing:

```

#lookup the device on the pcibus
lspci -v #shows pci devices

#lspci -v output
#04:03.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
#	Subsystem: Technotrend Systemtechnik GmbH S2-3200
#	Flags: bus master, medium devsel, latency 64, IRQ 19
#	Memory at df9ff400 (32-bit, non-prefetchable) [size=512]
#	Kernel driver in use: budget_ci dvb
#	Kernel modules: budget_ci

lspci -vbn #shows specific device-id

#lspci -vbn output
#04:03.0 0480: 1131:7146 (rev 01)
#	Subsystem: 13c2:1019
#	Flags: bus master, medium devsel, latency 64, IRQ 5
#	Memory at df9ff400 (32-bit, non-prefetchable)
#	Kernel driver in use: budget_ci dvb
#	Kernel modules: budget_ci

dmesg #will show which driver module got loaded and which adapter & frontend number is used

#dmesg output
#[    6.070322] DVB: registering new adapter (TT-Budget S2-3200 PCI)
#[    6.529783] budget_ci dvb 0000:04:03.0: DVB: registering adapter 0 frontend 0 (STB0899 Multistandard)...


```

This DVB-S tuner will show up in Tvheadend webinterface as "STB0899 Multistandard", to use it we first add a service provider network and than link it to the appropriate Tuner.  We now use hotbird13e as a e

```

Configuration > DVB Inputs > Networks
                                                         Add Network: DVB-S
                                                         Network Name: pcituner2-1-hotbird13
                                                         Pre-defined Muxes: > 13.0E:Hotbird
                                                         Orbital Position:13E : Eutelsat Hot Bird 13B/13C/13D
create

Configuration > DVB Inputs > TV adapters
                      STB0899 Multistandard : DVB-S : DVB-S #0
                                                     Enabled: * checkbox
                                                     Universal LNB only

save

Configuration > DVB Inputs > TV adapters
                      STB0899 Multistandard : DVB-S : DVB-S #0
                                                     Universal LNB only
                                                                              Networks:pcituner2-1-hotbird13
save


```

Setup DVB Tuner(s):
This time we will setup a DVB-S pci tuner, an ancient Hauppauge WinTV-NOVA-S DVB card (Technotrend Budget) for use with Tvheadend. First will determine which exact card is available in the server by opening a terminal and typing:

```

#lookup the device on the pcibus
lspci -v #shows pci devices

#lspci -v output
#04:04.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
#	Subsystem: Technotrend Systemtechnik GmbH Technotrend-Budget/Hauppauge WinTV-NOVA-S DVB card
#	Flags: bus master, medium devsel, latency 64, IRQ 16
#	Memory at df9ff600 (32-bit, non-prefetchable) [size=512]
#	Kernel driver in use: budget dvb
#	Kernel modules: budget

lspci -n #shows specific device-id

#lspci -n output
#04:04.0 0480: 1131:7146 (rev 01)

dmesg #will show which driver module got loaded and which adapter & frontend number is used

#dmesg output
[    6.083649] saa7146: register extension 'budget dvb'
[    6.848203] budget dvb 0000:04:04.0: DVB: registering adapter 1 frontend 0 (ST STV0299 DVB-S)...


```

This DVB-S tuner will show up in Tvheadend webinterface as "ST STV0299 DVB-S", to use it we first add a service provider network and than link it to the appropriate Tuner and or diseqc 1.1 position. We choose a diseqc 1.1 config which can handle +4-64 satellites, the Turksat is located on the 5th position, we address this by using the second uncommited switch=1 postion 1=AA, astra1 for example resided on the first uncommited swith=0 position 1=AA and astra2 on switch=0 position4=BB! When combining the multiple of 0-16 (un)commited switches with each 4 positions (AA-AB-BA-BB) you can get a total of 64 satellites (your neighbors will be very pleased by the look ;-) ) .

```

Configuration > DVB Inputs > Networks
                                                         Add Network: DVB-S
                                                         Network Name: pcituner1-5AA-turksat42
                                                         Pre-defined Muxes: > 42.0E:Turksat
                                                         Orbital Position:42E : Türksat 2A/3A/4A
create

Configuration > DVB Inputs > TV adapters
                      ST STV0299 DVB-S : DVB-S #0
                                         Select it and thick 'enable' checkbox
                                         Satellite config: 'Advanced (non-universal LNBs, rotors, etc.)'
save

Configuration > DVB Inputs > TV adapters
                      ST STV0299 DVB-S : DVB-S #0
                                                               Advanced (non-universal LNBs, rotors, etc.)
                                                                                   Orbital positions:'5' #depending how many LNB/satellites switches you have!
save


Configuration > DVB Inputs > TV adapters
                      ST STV0299 DVB-S : DVB-S #0
                                         Select it and thick 'enable' checkbox
                                                               Advanced (non-universal LNBs, rotors, etc.)
                                                                                   Position #5
                                                                                   Enabled: * checkbox
                                                                                   Networks: 'pcituner1-5AA-turksat42'
                                                                                   LNB type: Universal
                                                                                   Switch type: Generic

save

Configuration > DVB Inputs > TV adapters
                      ST STV0299 DVB-S : DVB-S #0
                                         Select it and thick 'enable' checkbox
                                                               Advanced (non-universal LNBs, rotors, etc.)
                                                                                     Position #5
                                                                                     Switch:Generic
                                                                                     Committed:AA
                                                                                     UnCommitted:1


save


```

If everything was configured when, the Turksat 42e on uncommited switch level 1 position 1=AA will be scanned for services!

**DVB-T**
The broadcasting of DVB-T has ceased in the Netherlands and replaced by DVB-T, therefor this part of the howto cannot be verified anymore. This time we will setup a DVB-T pci tuner from  Medion/Creatix CTX953 Hybrid for use with Tvheadend. First will determine which exact card is available in the server by opening a terminal and typing:

```

#lookup the device on the pcibus
lspci -v #shows pci devices

#lspci -v output
#04:05.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
#	Subsystem: Creatix Polymedia GmbH SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
#	Flags: bus master, medium devsel, latency 64, IRQ 17
#	Memory at df9ff800 (32-bit, non-prefetchable) [size=2K]
#	Capabilities: <access denied>
#	Kernel driver in use: saa7134
#	Kernel modules: saa7134

lspci -vbn #shows specific device-id

#lspci -vbn output
#4:05.0 0480: 1131:7133 (rev d1)
#	Subsystem: 16be:0010
#	Flags: bus master, medium devsel, latency 64, IRQ 9
#	Memory at df9ff800 (32-bit, non-prefetchable)
#	Capabilities: <access denied>
#	Kernel driver in use: saa7134
#	Kernel modules: saa7134

dmesg #will show which driver module got loaded and which adapter & frontend number is used

#dmesg output
[    6.850855] saa7134: saa7133[0]: found at 0000:04:05.0, rev: 209, irq: 17, latency: 64, mmio: 0xdf9ff800
[    6.850862] saa7134: saa7133[0]: subsystem: 16be:0010, board: Medion/Creatix CTX953 Hybrid [card=134,autodetected]
[    6.850881] saa7134: saa7133[0]: board init: gpio is 0
[    7.000779] saa7134: i2c eeprom 00: be 16 10 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    7.000783] saa7134: i2c eeprom 10: 00 ff 86 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[    7.000785] saa7134: i2c eeprom 20: 01 40 01 02 02 03 01 00 06 ff 00 2c 02 51 96 2b
[    7.000786] saa7134: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[    7.000788] saa7134: i2c eeprom 40: ff 21 00 c0 96 10 03 22 15 00 fd 79 44 9f c2 8f
[    7.000789] saa7134: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.000791] saa7134: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.000792] saa7134: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.000793] saa7134: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.000795] saa7134: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.000796] saa7134: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.000797] saa7134: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.000799] saa7134: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.000800] saa7134: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.000802] saa7134: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    7.000803] saa7134: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.928125] saa7134: saa7133[0]: registered device video1 [v4l2]
[   10.928242] saa7134: saa7133[0]: registered device vbi0
[   10.932399] saa7134_alsa: saa7134 ALSA driver for DMA sound loaded
[   10.932435] saa7134_alsa: saa7133[0]/alsa: saa7133[0] at 0xdf9ff800 irq 17 registered as card -2
[   10.932952] saa7134_dvb: dvb_init() allocating 1 frontend
[   10.952066] DVB: registering new adapter (saa7133[0])
[   10.952077] saa7134 0000:04:05.0: DVB: registering adapter 5 frontend 0 (Philips TDA10046H DVB-T)...
[   11.072030] tda1004x: setting up plls for 48MHz sampling clock
[   13.072030] tda1004x: found firmware revision 26 -- ok


```

This DVB-T tuner will show up in Tvheadend webinterface as "Philips TDA10046H DVB-T : DVB-T #0", to use it we first add a service provider network and than link it to the appropriate Tuner.  We now use Dutch DVB-T provider Digitenne which is by default available in Tvheadend and has 4 FTA channels in my region.

```

Configuration > DVB Inputs > Networks
                                                         Add Network: DVB-T
                                                         Network Name: 'pcituner3-digitenne'
                                                         Pre-defined Muxes: 'Netherlands: nl-All'

create

Configuration > DVB Inputs > TV adapters
                      Philips TDA10046H DVB-T : DVB-T #0
                                                     Enabled: * checkbox
                                                      Networks: 'pcituner3-digitenne'
save


```

By now you should have a DVB-T working, except that from 2019-07-09 there is only DVB-T2.

**DVB-T2**
You must use one of the supported USB DVB-T2 tuners: Microsoft XBOX, Hauppauge WinTV-DualHD or Astrometa DVB-T2 and just use the same config as previous DVB-T except the following changes.

```

Configuration > DVB Inputs > Networks
                                                         Add Network: DVB-T
                                                         Network Name: 'usb-digitenne2'
                                                         Pre-defined Muxes: 'Netherlands: nl-All'

create

```

After adding the "network", goto the Muxes TAB in the tvheadend webinterface and "edit" the 618MHz MUX(Zuid-Holland example, to be safe choose all DVB-T muxes) the "Delivery system" from "DVB-T" to "DVB-T2" and press apply. Than link this to a supported adapter, for Astrometa (which has 3 modulation) you must use the Panasonic DVB-T not the RealtekSDR one. 

```

Configuration > DVB Inputs > TV adapters
                      Panasonic MN88473 DVB-T : DVB-T #0
                                                     Enabled: * checkbox
                                                      Networks: 'usb-digitenne2'
save


```

Than force the network scan back at the "Networks" TAB and by now you probably have DVB-T2 working.


**[size=+2]Setup non-DVB sources:[/size]**

**IPCAM**
A Ubiquity Aircam ip-camera will be added as a live feed to tvheadend, just like the firewire/DV source this needs a helper/wrapper script to make a DVB compatible MPEGTS feed. On the contrary its video feed with native mpeg4 h264 content needs only to be rewrapped into a valid container instead of re-encoded.
```

#install remux/rewrap capable tool
sudo apt-get install ffmpeg

#create wrapper script
sudo nano /home/hts/aircam.sh
### copy code below
#!/bin/bash
#maybe ffmpeg doesn't need 2 instances compared to avconv to get the job done... test
/usr/bin/ffmpeg -loglevel quiet -rtsp_transport tcp -i rtsp://IPADDRESS/live/ch00_0 -vcodec copy -acodec copy -f flv - | /usr/bin/ffmpeg -loglevel quiet -i - -vcodec copy -acodec copy -bsf h264_mp4toannexb -f mpegts pipe:1
### CTRL +X save
sudo chmod +x /home/hts/aircam.sh

```

You might try to pipe the output of the former script to ffplay or vlc if is succesfull we can now add the fake DVB stream to Tvheadend.
```

Configuration > DVB Inputs > Networks
                                                Add IPTV-network
						Network name:securitycam2
create

Configuration > DVB Inputs > Muxes
					        Add Mux:securitycam2
                                                EPG disableinfo	
                                                URL:pipe:///home/hts/aircam.sh
                                                Interface: enp0s10
                                                Mux name:seccam2mux
                                                Service name:seccam2service #will be listed as channel name after mapping!
create

Configuration > DVB Inputs > Services
#check this "ipcam" service with VLC
#map this channel

```

**DV**
We will use a FireWire DV camcorder as a source for a Tvheadend SDTV channel, therefor we will install the following tools which will simplify testing and grabbing dv/hdv video and encoding and mulitplexing it to a fake DVB compatible stream which can be used in Tvheadend.
```

sudo apt-get install dvgrab ffmpeg

#test dv video capture
dvgrab -noavc testvideo.dv #press CTRL + C top stop capture

#playback of captured dv file
vlc testvideo.dv

sudo nano /home/hts/dvcam.sh
### copy code below
#!/bin/bash
#/usr/bin/dvgrab -f raw -noavc - | /usr/bin/ffmpeg -i - 
/usr/bin/ffmpeg -f iec61883 -i auto -vcodec mpeg2video -s 720x576 -r 25 -flags cgop -sc_threshold 1000000000 -b:v 5M -minrate:v 5M -maxrate:v 5M -bufsize:v 1.4M -acodec mp2 -ac 2 -b:a 128k -f mpegts pipe:1
### CTRL +X save
sudo chmod +x /home/hts/dvcam.sh

```

If previous attemps were succesful, we can now add the fake DVB stream to Tvheadend.
```

Configuration > DVB Inputs > Networks
                                                Add IPTV-network
						Network name:securitycams
create

Configuration > DVB Inputs > Muxes
					        Add Mux:securitycams
                                                EPG disableinfo	
                                                URL:pipe:///home/hts/dvcam.sh
                                                Interface: enp0s10
                                                Mux name:seccammux
                                                Service name:seccamservice #will be listed as channel name after mapping!
create

Configuration > DVB Inputs > Services
#check this "ipcam" service with VLC
#map this channel

```

**HDV**
We will use a FireWire HDV camcorder as a source for a Tvheadend HDTV channel, therefor we will install the following tools which will simplify testing and grabbing dv/hdv video and remux it to a fake DVB compatible stream which can be used in Tvheadend.
```

sudo apt-get install dvgrab ffmpeg

#test hdv video capture, you will need the captured file!
cd /home/hts
sudo dvgrab -noavc -f hdv testhdvideo -F 750 #press CTRL + C to stop capture after the first split ~30seconds
sudo chown hts:hts testhdvideo001.m2t #fix file permissions so the hts user from tvheadend can read the movie file

#playback of captured dv file
vlc testhdvideo001.m2t

sudo nano /home/hts/hdvcam.sh
### copy code below
#!/bin/bash
/usr/bin/ffmpeg -re -i /home/hts/testhdvideo001.m2t -vcodec copy -acodec copy -f mpegts pipe:1 #this is only temporary until tvheadend has detected a single valid service from the mux

### CTRL +X save
sudo chmod +x /home/hts/hdvcam.sh

```

First we need to make Tvheadend detect the recorded m2t file as a valid DVB MPEG2HD stream because detecting the FireWire directly will fail! If Tvheadend found a service in the corresponding network>mux than we can add the real FireWire HDV stream! 
```

Configuration > DVB Inputs > Networks
                                                Add IPTV-network
						Network name:hdvcam
create

Configuration > DVB Inputs > Muxes
					        Add Mux:hdvcam
                                                EPG disableinfo	
                                                URL:pipe:///home/hts/hdvcam.sh
                                                Interface: enp0s10
                                                Mux name:hdvcammux
                                                Service name:hdvcamservice #will be listed as channel name after mapping!
create

Configuration > DVB Inputs > Networks
"force scan"

Configuration > DVB Inputs > Services
#check this "Service01" m2t file with VLC
#map this service to channel

```

If a valid service (which is actually a movie file) was detected we need to re-edit the "hdvcam.sh" script to swap the m2t recorded file with the Firewire HDV device.
```

sudo nano /home/hts/hdvcam.sh
### edit code below
#!/bin/bash
#/usr/bin/ffmpeg -re -i /home/hts/testhdvideo001.m2t -vcodec copy -acodec copy -f mpegts pipe:1 #this is only temporary until tvheadend has detected a service from the mux
/usr/bin/ffmpeg -f iec61883 -i auto -vcodec copy -acodec copy -f mpegts -mpegts_service_type mpeg2_digital_hdtv pipe:1
### CTRL +X save

```

**ALSA**
This example will show you how to use a USB soundcard (Behringer UCA200) as a alsa source for a DVB radio webstream in uncommon mp3 format, using a special recording profile with audio only instead of pass it writes a mp3 container directly instead of mpegTS. Its not perfect, as in it starts around 15 seconds after several testing/bad state. Open a terminal:

```

#first check if the USB soundcard is listed
lsusb
#Bus 001 Device 005: ID 08bb:2902 Texas Instruments PCM2902 Audio Codec

#second check if alsa does list the device
arecord -l
#card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
#  Subdevices: 1/1
#  Subdevice #0: subdevice #0
#card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
#  Subdevices: 1/1
#  Subdevice #0: subdevice #0

#if not detected install alsa and or fix user permissions
sudo apt-get install alsa-base alsa-utils ffmpeg #alsa-oss pavucontrol
sudo adduser $USER audio
sudo adduser hts audio #plugdev?

#third do a 30s test recording on card1subdevice0 and playback the wav  
ffmpeg -f alsa -i hw:1,0 -t 30 adminrecord.wav

#login as tvheadend user named hts and test recording again!
sudo su -l hts
ffmpeg -f alsa -i hw:1,0 -t 30 htsrecord.wav

#four create a tvheadend capture script and alter RADIOPROVIDER / RADIONAME at will!
sudo nano /home/hts/usbaudio.sh
### copy code below
#!/bin/bash
/usr/bin/ffmpeg -loglevel quiet -f alsa -ac 2 -i hw:1,0 -vn -acodec libmp3lame -b:a 256k -metadata service_provider=RADIOPROVIDER -metadata service_name=RADIONAME -tune zerolatency -f mpegts -mpegts_service_type digital_radio pipe:1
### CTRL +X save
sudo chmod +x /home/hts/usbaudio.sh

```

Add the following the the Tvheadend Webinterface:
```

Configuration > DVB Inputs > Networks
                                                Add IPTV-network
						Network name:usbaudio
create

Configuration > DVB Inputs > Muxes
					        Add Mux:usbaudio
                                                EPG disableinfo	
                                                URL:pipe:///home/hts/usbaudio.sh
                                                Interface: enp0s10
                                                Mux name:usbaudiomux
                                                Service name:usbaudioservice #will be listed as channel name after mapping!
create

Configuration > DVB Inputs > Services
#check this "usbaudio" service with VLC
#map this channel

```

**DECKLINK**
It is possible to stream from uncompressed digital video sources like SDI/HDMI or even analogue Component/Composite/S-video provided by Blackmagicdesign decklink/intensity IO-cards. Besides the Proprietary Desktop Video Driver this will also require the SDK in case of a custom ffmpeg build(to much work) or bmdtools(see below) maybe melt works without SDK?

```

#install Decklink Desktop video driver debs

#check hardware
lspci

#checke mediaexpress gui

#install capture tools
sudo apt-get install build-essential pkgconf pkg-config libavcodec-dev libavdevice-dev libavformat-dev libavutil-dev melt ffmpeg
git clone https://github.com/lu-zero/bmdtools.git
cd bmdtools
git reset --hard 88c5204
make SDK_PATH=/path/to/the/bmd/sdk/linux/include

#look at syntax
./bmdcapture -h #look at -m -A -V -f nut

#test capture and playback
./bmdcapture -m 1 -F nut -f pipe:1 | ffplay -

```

If test capture/viewing works continue with adding it to Tvheadend.

```

sudo nano /home/hts/decklink.sh
### copy code below
#!/bin/bash
/home/admin/mygits/bmdtools/bmdcapture -m 1 -F nut -f pipe:1 | /usr/bin/ffmpeg -loglevel quiet -i --vcodec mpeg2video -s 720x576 -r 25 -flags cgop -sc_threshold 1000000000 -b:v 5M -minrate:v 5M -maxrate:v 5M -bufsize:v 1.4M -acodec mp2 -ac 2 -b:a 128k -f mpegts pipe:1
### CTRL +X save
sudo chmod +x /home/hts/decklink.sh

```

If previous attempts were successful, we can now add the fake DVB stream to Tvheadend.
```

Configuration > DVB Inputs > Networks
                                                Add IPTV-network
						Network name:decklinknetwork
create

Configuration > DVB Inputs > Muxes
					        Add Mux:decklinknetwork
                                                EPG disableinfo	
                                                URL:pipe:///home/hts/decklink.sh
                                                Interface: enp0s10
                                                Mux name:decklinkmux
                                                Service name:decklinkservice #will be listed as channel name after mapping!
create

Configuration > DVB Inputs > Services
#check this "ipcam" service with VLC
#map this channel

```

**V4L2**
The Hauppauge WinTV PVR-150 has been used successfully for Composite Video (CVBS) streaming with Tvheadend(Analogue Tuning and S-video not tested). This device requires firmware and a additional setup util "ivtv-utls", the card has a hardware mpeg encoder therefor ffmpeg only needs to rewrap to a mpegts stream:

```

sudo apt-get install ivtv-utils

cat << EOF | sudo tee /home/hts/pvr150comp.sh 
#!/bin/bash
v4l2-ctl -d /dev/video0 -i 2 #2=composite 1=svideo 0=analogue television
#v4l2-ctl -d /dev/video0 --list-formats
#v4l2-ctl -d /dev/video0 --list-formats-ext
/usr/bin/ffmpeg -loglevel quiet -re -y -f mpeg -i /dev/video0 -c copy -f mpegts pipe:1
EOF

chmod +x /home/hts/pvr150comp.sh

```

Select video source and test simple capture:
```

v4l2-ctl -d /dev/video0 -i 2 #2=composite 1=svideo
cat /dev/video0 > ~/Desktop/catcomp.mpg

```

If previous attempts were successful, we can now add the fake DVB stream to Tvheadend.
```

Configuration > DVB Inputs > Networks
                                                Add IPTV-network
						Network name:pvr150network
create

Configuration > DVB Inputs > Muxes
					        Add Mux:pvr150network
                                                EPG disableinfo	
                                                URL:pipe:///home/hts/pvr150comp.sh
                                                Interface: enp0s10
                                                Mux name:dpvr150mux
                                                Service name:pvr150service #will be listed as channel name after mapping!
create

Configuration > DVB Inputs > Services
#check this "pvr150" service with VLC
#map this channel

```

**[size=+2]DVB-api woes[/size]**
DVB_MAX_ADAPTERS
There is indeed a limit for the number of physical DVB adapters connected to the same system running at the same time, the total amount is 8. This can be fixed by altering kernel module 'dvb-core' its source code and recompile a new module. Although its not hard to accomplish, just comment a few lines and address a new limit, it takes around 20GB, alot of CPU compile time and you have to do it manually for every system upgrades which ships with a newer kernel. First we add the ability to download sources from Ubuntu "apt" this can be done via GUI "Software & Updates" by checking a checkbox or CLI. Second we will get the right building tools. Third get the Ubuntu kernel source, fourth prepare and five patch it and finally compile and install if successful.

```

#1st add sources to apt packaging system
sudo nano /etc/apt/sources.list
#uncomment and change the line with the first instance of '# deb-src' to 'deb-src' 
CTRL+X save and exit

#make package sources available to apt
sudo apt-get update

#2nd install building tools and components (make sure you are running the current kernel version you wish to alter)
sudo apt-get build-dep linux-image-$(uname -r)

#3rd get kernel sources around 20GB when building (without sudo!)
apt-get source linux-image-$(uname -r)
cd linux*
#4th prepare it (same kernel config as before, no need for new one), change name
chmod a+x debian/rules
chmod a+x debian/scripts/*
chmod a+x debian/scripts/misc/*
fakeroot debian/rules clean
#change / increase the version number so the custom kernel looks distinguishable by apt just add '+test01'
nano debian.master/changelog #example edit add '+test01'
--------------------------------------------------------------------------------------------
linux (4.4.0-97.120+test01) xenial; urgency=low

  * linux: 4.4.0-97.120+test01 -proposed tracker (LP: #1718149)
--------------------------------------------------------------------------------------------
CTRL+X save y and exit

#5th 
nano drivers/media/dvb-core/dvbdev.h
#comment the following block around line 35 just like below and add the line #define....max limit including the hashtag!

/*
#if defined(CONFIG_DVB_MAX_ADAPTERS) && CONFIG_DVB_MAX_ADAPTERS > 0
  #define DVB_MAX_ADAPTERS CONFIG_DVB_MAX_ADAPTERS
#else
  #define DVB_MAX_ADAPTERS 8
#endif
*/

#define DVB_MAX_ADAPTERS 16
CTRL+X save and exit

#final build and install the 4 deb files containing the words image&headers and reboot
fakeroot debian/rules binary-headers binary-generic binary-perarch &>> ../buildlog+test01.txt
sudo dpkg -i linux-image*.deb linux-header*.deb

``` 

indistinguihable...
Having multiple DVB-tuners of the same kind brand/type might be indistinguishable therefor /dev/dvb/frontend number are changed after reboot or when adding extra adapters. Some drivers can cope with MAC address identification which can assist in identification but the opensource drivers for the TBS dual tuner does not [yet]("https://github.com/ljalves/linux_media/pull/140"). As a workaround you should only connect both tuners to the same satellite, so in case of accidentally swapping frontend numbers you end up having the same tuner configuration. For the budget cards which come with a opensource driver supporting unique mac address identification it should be possible to make a script that creates a symlink to a specific frontend number based on MAC Address. It has caught attention to linux kernel [developers]("https://patchwork.kernel.org/patch/10612153/") that it may be a good idea to let dvb adapter number set by udev be influenced by its mac address.

legacy apps...
Some older dvb apps cannot or partly work if a specific tuner frontend is located not on the preferred first number like /dev/dvb/frontend0 or its following 4-8 positions. To comply with these needs it is possible to specify a frontend number to a certain tuner frontend by adding them to its driver kernel modules.

```

#create tuner specific kernel module options for selecting frontend adapter number
sudo nano /etc/modprobe.d/budget_ci.conf
### change/ add code 
options budget_ci adapter_nr=3,4
### CTRL +X save

```

**[size=+2]Playlist.m3u[/size]**
Services that are mapped to channels are possible to be exported as a m3u playlist, this will ease testing and compatibility with software mediaplayers and lowers requirements for specific mediaplayer addons&credentials. This is a user unique feature that needs some checkboxes to be enabled for its user account, after that a playlist will be generated and patched with these user credentials.

```

Configuration > Users > Access Entries
   Add
        Enabled:*Check
        Username:m3uviewers
        Change parameters:*Rights
        Streaming:*Basic,Advanced
        Streaming profiles:*pass
        Connection limit type:*Streaming
create

Configuration > Users > Passwords
   Add
        username:m3uviewers
        password:simple
create

```

```

#generate a playlist from the terminal, and offcourse change un/pw/ipaddress to your situation!
wget http://username:password@ipadresstvheadendserver:9981/playlist

#add credentials to playlist using sed find&replace
sed -i 's/ipaddress/username:password@ipaddress/g' playlist

#rename playlist
mv playlist playlist.m3u


```

**[size=+2]Recordings share[/size]**

HTTP access
To have easy remote access to the recordings made by Tvheadend without the use of logins/etc, we will install a simple HTTP webserver which will be available from the webbrowser on all the LAN clients:
```

sudo apt-get install lighttpd
sudo nano /etc/lighttpd/lighttpd.conf
### change/ add code 
server.document-root        = "/mnt/mediastorage/tvherecordings/"
dir-listing.activate = "enable"
dir-listing.set-footer = "This can be used as a identifier like hostname or description of the server"
### CTRL +X save
sudo systemctl restart lighttpd.service

```

NFS access
Besides HTTP access to recordings, the KODI Tvheadend HTSP integration gives the client easy access to recordings on the server. However on some networks live streaming of DVB sources works perfect(including HD channels) while watching back recordings via the PVR system is erratic! As a workaround NFS needs to be used. This also requires changes on the KODI client side, since you need to mount the NFS share on the client and than bookmark that folder in the KODI environment(see part2).

```

#nfs example
sudo apt-get install nfs-kernel-server

#adjust /mnt path and ip subnet range 192.168.x.x/x to your situation
echo "/mnt/mediastorage/tvherecordings 192.168.1.0/24(ro,sync,all_squash,insecure)" | sudo tee -a /etc/exports

#make edited /etc/exports folders available by nfs
sudo exportfs -rav

#restart nfs if necessary?
sudo systemctl restart nfs-server.service

```

---

### Post by walterav on 2016-09-09
**[size=+2]part2: Tvheadend further client integration[/size]**

**VLC**
The client we used earlier in this howto for Tvheadend was "VideoLAN (vlc)", this was good enough for testing/debugging server tuner functions and maybe simple playlist or adhoc based streaming use cases. However more clients exist which give way more features than plain channel zapping, for instance watch back recordings, schedule recordings or even timeshift (not addressed)! On the Tvheadend server side, a "user account" accompanied with a "password" and some mapped "channels" is necessary before a Tvheadend client setup will succeed. Use the Tvheadend server post above and use section "Channels/playlists" as a template for a new user account, but this time you can keep the default checkboxes/settings for this user just make sure HTSP is enabled for streaming.
 
**KODI**
We will address the software client KODI with is PVR addon "Tvheadend HTSP client" (don't mix up with the KODI Tvheadend Backend available in Libreelec/Openelec). This software client with this addon like its name reveals can use the HTSP streaming protocol that improves stable streaming on less than perfect networks. KODI itself is a program that must be run on a certain OS and hardware combination, due to the extreme variety here in hardware/software setups we will limit or examples to the following:

hardware:
PC/LAPTOP/DESKTOP #x86/amd64 with descent intel/amd/nvidia based GPU
Raspberry Pi #including MPEG2 license

operating-systems:
Ubuntu 16.04 #x86/amd64 versions with descent kernel/graphics stack to assist playback
Libreelec #Raspberry pi
Windows/Mac OS #very descent hardware only!

setup: KODI (app on a existing Desktop environment #x86/amd64)

On Ubuntu 16.04 we will add a KODI [ppa]("https://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux") since the KODI client is very dated and its GUI differs to much from current 17.6/18.x releases. If you use Ubuntu 18.04 you may skip this ppa part "except the last line" if you're fine with using KODI 17.6.

```

#cleanup older kodi & pvr form ubuntu's own repo if installed!
sudo apt-get -y remove kodi kodi-pvr-hts

#add up2date official kodi ppa which probably ships kodi 18 when released
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
#ubuntu 18.04 users may only need the following line if kodi 17.6 is good enough
sudo apt-get install kodi kodi-pvr-hts #mind the pvr-hts!!!

``` 

After KODI has been installed run it from a desktop menu category (Sound & Video) or from a terminal run 'kodi', and navigate (arrow keys+enter) to Add-ons > My add-ons > PVR clients > "Tvheadend HTSP Client".

From there you will see a config screen with 6 column blocks (Run/Configure/Update/Auto-update/Enable/Uninstall), first hit Configure. Fill in the Tvheadend IP-address of the Server followed by Username&Password and confirm with "OK". Back in the 6 column screen, go to "Enable" and press enter to enable the pvr-hts addon. If everything went well you will see in the top right corner some notifications popup about, receiving TV/Radio channel list and EPG guide data.

On Windows and Mac steps are very similar, except getting the KODI App which can be done via the Windows App store, or get the KODI app on the official KODI website both [Windows]("https://kodi.tv/download/849") and [Mac]("https://kodi.tv/download/851"). Running the KODI app on Windows requires it to allow firewall access to local networks, first popup when opening the App. Don't have access to MacOS so cannot say yet... 

setup: KODI (as a single environment #Raspberry Pi)
Actually multiple options are available these day's for the Raspberry Pi, if you would like to run default Raspbian Stretch be it a Desktop(slow) or raspbian-lite you can just follow the previous instructions and just install KODI with the following terminal command:

```

sudo apt-get install kodi kodi-pvr-hts

```

Before Raspbian 9 Stretch the only simple solution was a complete DISTRO with just the KODI app called OpenElec but personally I prefer [libreelec](https://libreelec.tv) or my own spin [roraspbiankodi](https://github.com/walterav1984/roraspbiankodi) project. Follow their respective install instructions followed by the Tvheadend HTSP client setup in this post and your done.

**[size=+2]Advanced PVR Integration:[/size]**
**Sleep/Wake/Suspend/Shutdown**
Before the following nice suspend script may work for you, its important to know if your Debian/Ubuntu TvHeadend server suspends/wakes without issues in the first place! A good start is a minimal Debian/Ubuntu CLI install (without GUI/desktop) and without internal/external connected PCI(e)/USB DVB-tuner hardware, even without TvHeadend package! First try to bring the system asleep:

```

sudo systemctl suspend;exit

```

If it sleeps for a couple of minutes (check if all fans are silent?), than wake it up with power button (keyboard / mouse may work). When its awake again check kernel driver diagnosticmessage "dmesg" to see if any errors popup after sleep. If the system won't sleep or wake, check BIOS/UEFI settings and make sure SLEEP/SUSPEND related settings are set to anything with S3/STR(suspend to ram) instead of S1 or other. 

```

sudo dmesg

```

Add DVB-tuner(s) one at the time (don't install TvHeadend yet) check with "lsmod" to see what modules they load and install Tvheadend and notice that some tuners load even more kernel modules. Sleep the system again if there are some devices that may not wakeup correctly unload their kernel modules before sleep with the following script in "/lib/systemd/system-sleep/examplescript". For example I need to unload the modules for a elgato DVB-C USB Tuner and a Technotrend DVB-S2/CAM PCI Tuner and notice that I also stop tvheadend service!

```

sudo nano /lib/systemd/system-sleep/examplescript #copy past script below

```

```

#!/bin/sh
#https://askubuntu.com/questions/226278/run-script-on-wakeup #SpmP

case $1/$2 in
  pre/*)
    echo "Going to $2..."
    # Place your pre suspend commands here, or `exit 0` if no pre suspend action required
systemctl stop tvheadend
    sleep 3
modprobe -r em28xx_alsa
modprobe -r em28xx_dvb
modprobe -r em28xx_rc
modprobe -r em28xx
modprobe -r drxk

modprobe -r budget_ci
modprobe -r budget_core
modprobe -r tda18271
modprobe -r stb0899
modprobe -r stb6100
modprobe -r lnbp21
modprobe -r rc_tt_1500
modprobe -r rc_nec_terratec_cinergy_xs
    ;;
  post/*)
    echo "Waking up from $2..."
    # Place your post suspend (resume) commands here, or `exit 0` if no post suspend action required
modprobe budget_ci
modprobe em28xx_dvb
sleep 5
systemctl restart tvheadend
    ;;
esac

```

```

sudo chmod a+x /lib/systemd/system-sleep/examplescript

```

If system sleeps and wakes correctly its time to check if RTC(RealtimeClock) is affective on letting the system poweron/wake from off/suspend on a specific alarm time. On Debian/Ubuntu "rtcwake" must be installed by the package "util-linux".

```

sudo apt-get install util-linux

```

To test if the system wakes 10 minutes from now (after suspending it again ;-) do:

```

sudo rtcwake -s 600 -m no #will set a wakeup event 600 seconds from now
sudo rtcwake -m show #shows wake time in UTC don't worry if its not local time!
timedatectl #shows your current local time and BIOS UTC time
sudo systemctl suspend;exit #sleeps system now wait for ~10 minutes and see if it powers up

```

If the system won't powerup after 10 minutes, check if your local system time( = +- ~x hours from UTC) / BIOS=UTC time are correctly matching. Also check BIOS that its using UTC time instead of local and that some power related settings in BIOS allow poweron by rtc/clock event/alarm PCI(e) device etc.

If these conditions are met its time to install "Mr Rooster" modified TvHeadend Auto shutdown/suspend and wakeup [script]("https://tvheadend.org/boards/4/topics/27066"). Notice that it need to setup with correct permissions for correct user and a corresponding cronjob for that user! First install "curl" than create script, fix ownership/execution and than give tvheadend user sudo permissions to allow suspending and at a cronjob timer.

```

sudo apt-get -y install curl
sudo nano /home/hts/sleep_after_rec.sh #copy code below inside this script

```

```

#!/bin/bash
# https://tvheadend.org/boards/4/topics/27066 #Mr Rooster modfied by me
# shutdown vs suspend doesn't create wakeup data for correct re-sleep check

TVHINSTU=hts
TVHWUSER=sleepuser
TVHWPASS=sleeppass
TVHIPADD=127.0.0.1
TVHHPORT=9981

#sudo apt-get install curl

#/etc/sudoers.d/hts
# hts user can shutdown with sudo permission
#hts  ALL= NOPASSWD: /bin/systemctl poweroff,/bin/systemctl halt,/bin/systemctl reboot,/bin/systemctl suspend,/usr/sbin/rtcwake,/bin/journalctl

#sudo crontab -u hts -e 
#*/10 * * * * /home/hts/shutdown_after_rec.sh

#verify suspend compatibility and adjust remove/reload some kernel modules before after suspend
#https://askubuntu.com/questions/226278/run-script-on-wakeup
#/lib/systemd/system-sleep/yoursleepscript

#test system rtcwake abilities
#sudo apt-get install utils-linux
#sudo rtcwake -s 240 -m no #will set a wakeup time 4 minutes from now
#timedatectl #shows local/rtc time
#sudo rtcwake -m show #shows the bios time for waking up -u -l utc local -a auto=default
#sudo systemctl suspend;exit #test and see if the system wakes in 4 minutes
#sudo rtcwake -m no -t $(date +%s -d 'today 19:45')
#sudo rtcwake -m show #check time what has been set if it correlates rtc to utc

#test system wakeonlan abilities
#cat /proc/acpi/wakeup
#sudo ethtool eth0 #pumb if the 'g' is missing it won't wake on magic packet!!! 
#sudo ethtool -set eth0 wol g #sets the 'g' as a condition to wake from lan

#tvheadend sleep user allow / set checkboxes video recording "manage all" to detect recordings
#ok recording realtime takes intro/ending padding in account
#ok rtcwake event takes padding&warmup in account

export PATH=/home/$TVHINSTU:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games

WAKEDATE=$(sudo journalctl -b 0 -o short-iso MESSAGE="PM: Finishing wakeup." | tail -1 | cut -d" " -f1 | sed -e 's/+.*//')
DATEWAKE=$(date -d"$WAKEDATE" +%s )
DATENOW=$(date +%s)

A=$(($DATENOW-$DATEWAKE))
B=540 #seconds 9 minutes
if (( A < B));
    then
        echo "$TVHINSTU user last suspend request was $A < 540 seconds ago skip suspend" | logger
        exit 0
    else
        echo "$TVHINSTU user last suspend request was $A > 540 seconds ago continue suspend" | logger
##
## Check for active connections, except those from the local machine.
##
if [ "`curl -s http://$TVHWUSER:$TVHWPASS@$TVHIPADD:$TVHHPORT/api/status/connections | tr } '\n' | grep peer | grep -v 127.0.0.1`" != "" ]; then
        echo "$TVHINSTU user detects active TvHeadend connections skip suspend" | logger
        exit 0
fi

##
## Check for active recordings
##
curl -s "http://$TVHWUSER:$TVHWPASS@$TVHIPADD:$TVHHPORT/api/dvr/entry/grid_upcoming?limit=99999" | grep -q '"sched_status":"recording",'
match=$?
if [ "$match" != "0" ]; then
        ##
        ## Not recording, can we shutdown?
        ##
        next_recording=`curl -s "http://$TVHWUSER:$TVHWPASS@$TVHIPADD:$TVHHPORT/api/dvr/entry/grid_upcoming?limit=99999" | tr , '\n' | grep start_real | sed "s/.*start_real.:\([0-9]*\).*/\1/" | sort -n | head -1`

        ## 
        ## If there are no recordings we should wake up tomorrow 
        ## everyday wakeup for epg index?
        if [ "$next_recording" = "" ]; then
          echo "$TVHINSTU user detects no TvHeadend scheduled recordings, set EPG update wake" | logger
          next_recording=`date --date "tomorrow" +%s`
        fi

        gap=$(($next_recording-`date +%s`))

        echo Next recording: `date -d "1970-01-01 $next_recording sec" "+%F %H:%M:%S" -u` | logger

        if [ $gap -gt 2400 ]; then
                ##
                ## The gap to the next recording is more than 40 minutes, so lets shutdown
                ##

                ##
                ## Set the wakeup for 2 minutes before the next recording
                ##
                wakeup=$((next_recording-120))
                wakeup_date=`date -d "1970-01-01 $wakeup sec" "+%F %H:%M:%S"`
                echo "$TVHINSTU user sets wake up for next TvHeadend event at: $wakeup_date" | logger
                /usr/bin/sudo /usr/sbin/rtcwake -m no -t $wakeup
                ##
                ## Now shutdown
                ##
                /usr/bin/sudo /bin/systemctl suspend #poweroff
        fi
else
        ##
        ## Still recording, log the attempt and do nothing.
        ##
        echo "$TVHINSTU user detects active TvHeadend recording(s) skip suspend" | logger
fi
        #exit 0
fi

```

```

sudo chmod +x /home/hts/sleep_after_rec.sh #makes it executable
sudo chown hts:hts /home/hts/sleep_after_rec.sh #makes hts user own it

sudo nano /etc/sudoers.d/hts #add following lines without comments!
hts  ALL= NOPASSWD: /bin/systemctl poweroff,/bin/systemctl halt,/bin/systemctl reboot,/bin/systemctl suspend,/usr/sbin/rtcwake,/bin/journalctl

sudo crontab -u hts -e #add a cronjob timer every 10 minutes
#*/10 * * * * /home/hts/sleep_after_rec.sh

```

Almost every thing is ready, but you'll notice the #comment before the cronjob timer, if it was not there your system automatically fall asleep every 10 minutes! Just need to create a TvHeadend user from the webinterface which is capable of listing connection and user status, create a admin username/password "sleepuser"/"sleeppass" with all defaults but also checkbox all checkboxes in the video recording section "view all/manage all/failed/etc" to detect recordings.

To test the interaction of the sleep script, we'll manually PREVENT triggering it with active Tvheadend sessions (nearby-upcoming)recording and or kodi htsp users active viewing connections (also VLC from tvheadend webinterface is OK). So first start watching a TV-channel from the server (web interface of kodi) which triggers activity and hopefully won't trigger the sleep script. Than check manually if the "curl" part of the sleep script will login to Tvheadend to detect active sessions/recording. If "curl" will load a webpage with a 404 error check if the Tvheadend webinterface sleepuser/password/rights are correct, if it cannot detect if Tvheadend is active and therefor the sleep script will behave irratic (it will sleep, although users are watching/recording or it will not wake on timer).

```

#adjust the following variables with your own settings!
#$TVHWUSER
#$TVHWPASS
#$TVHIPADD
#$TVHHPORT
curl -s http://$TVHWUSER:$TVHWPASS@$TVHIPADD:$TVHHPORT/api/status/connections

```

If this "curl" part of the script did indeed login into the webinterface of Tvheadend listing its current activity or lack of you may test the following complete script.

```

sudo -u hts /home/hts/sleep_after_rec.sh #will test sleep as user hts

``` 

If everything works correct the system won't sleep since it detects a active viewing connection, see the log files to see that the sleep script did run but did not finish.

```

sudo cat /var/log/syslog | grep hts
#... hts: hts user last suspend request was 4202 > 540 seconds ago continue suspend...
#... hts: hts user detects active TvHeadend recording(s) skip suspend...


```

Stop active viewing/recording sessions schedule a recording an hour from here and force sleep again:

```

sudo -u hts /home/hts/sleep_after_rec.sh

```

If the system sleeps and wakes for recording and sleeps again you may activate the cronjob(remove #comment) and your done.

```

sudo crontab -u hts -e #add a cronjob timer every 10 minutes
*/10 * * * * /home/hts/sleep_after_rec.sh

```

**WAKE ON LAN "WOL"**
This can be used to let a kodi client trigger a event to remotely wake the tvheadend server for watching. The enable wakeonlan on TvHeadend server, check BIOS setting for waking on LAN/Ethernet PCI/PCI(e) activity and check in Debian/Ubuntu following settings:

```

sudo apt-get install ethtool
sudo ethtool eth0 #check current WOL settings
#       ....
#	Supports Wake-on: pg
#	Wake-on: pbum
#	Current message level: 0x0000003f (63)
#       ...

sudo ethtool -set eth0 wol g #set WOL magic packet
#       ....
#	Supports Wake-on: pg
#	Wake-on: g
#	Current message level: 0x0000003f (63)
#       .

#Some systems need acpi trigger for specific pci slot/device in my example LAN0 device says "disabled"
cat /proc/acpi/wakeup #look for something that looks like LAN/Ethernet/SLOT lspci -tn

#after following command /proc/acpi/wakeup shows "enabled"
echo "LAN0" | sudo tee /proc/acpi/wakeup

#if necessary add ethtool/ echo proc/acpi/wake to /etc/rc.local if wakeonlan settings are not saved!

sudo ifconfig #lookup macaddress of eth0

sudo systemctl suspend#or wait for script to suspend it

```

On the Client side install and do the following the wake the remote TvHeadend server. Or use my roraspbiankodi cient image.

```

sudo apt-get install wakeonlan
wakeonlan macaddress #wakes the tvheadend server

```

This raspbian based [kodi]("https://github.com/walterav1984/roraspbiankodi") image is readonly/power outage/cut proof and triggers wakeonlan as soon as television goes on with raspberry pi.

---

### Post by acoloss on 2016-12-02
Hi and thanks for this.

I've got the same tuner as in your example.

[COLOR=#000000]Astrometa dvb-t2 with the [/COLOR][COLOR=#000000]updated mn88473 I believe.

I got it to work with openelec/libreelec - it sees all the tuners (including dvb-c), but the quality is too bad to watch, and sometimes doesn't work at all..

so i tested on windows with progdvb and it works flawless.

-

I then decided to try it on my ubuntu server  which i'm using with tvheadend at the moment ([/COLOR][COLOR=#000000]to see if it was related to openelec/libreelec)[/COLOR][COLOR=#000000]. I currently have a TBS6909 (octo tuner) connected to 3 satellites by diseqc. all works flawless.

I put in the USB device and tvheadend showed only the dvb-T device (along with my tbs card).

i checked dsmeg and i didn't see any error with it not finding the firmware.

I rebooted and now tvheadend won't start at all.. if i restart tvheadend i can see this in dsmeg - basically tvheadend won't start with it plugged in.
i tried adding the firmware anyway, same problem

[/COLOR]```
[    3.571168] TBSECP3 driver 0000:04:00.0: TurboSight TBS 6909 DVB-S/S2[    3.571524] DVB: registering new adapter (TBSECP3 DVB Adapter)
[    3.573188] WARNING: You are using an experimental version of the media stack.
                As the driver is backported to an older kernel, it doesn't offer
                enough quality for its usage in production.
                Use it with care.
               Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
                91374e5f36b0f912136b9f46c6b9e34b909fe21c si2157: ISDB-T support.
[    3.598138] usb 2-1.6: dvb_usb_v2: found a 'Astrometa DVB-T2' in warm state
[    3.625757] Adding 25069564k swap on /dev/sda5.  Priority:-1 extents:1 across:25069564k SSFS
[    3.671711] usb 2-1.6: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[    3.671717] DVB: registering new adapter (Astrometa DVB-T2)
[    3.671719] usb 2-1.6: media controller created
[    3.671864] dvb_create_media_entity: media entity 'dvb-demux' registered.
[    3.675869] i2c i2c-12: Added multiplexed i2c bus 13
[    3.675870] rtl2832 12-0010: Realtek RTL2832 successfully attached
[    3.685701] mn88473: module is from the staging directory, the quality is unknown, you have been warned.
[    3.688188] mn88473 12-0018: Panasonic MN88473 successfully attached
[    3.688192] usb 2-1.6: DVB: registering adapter 1 frontend 0 (Realtek RTL2832 (DVB-T))...
[    3.688195] dvb_create_media_entity: media entity 'Realtek RTL2832 (DVB-T)' registered.
[    3.688228] usb 2-1.6: DVB: registering adapter 1 frontend 1 (Panasonic MN88473)...
[    3.688230] dvb_create_media_entity: media entity 'Panasonic MN88473' registered.
[    3.691088] TBSECP3 driver 0000:04:00.0: MAC address 00:22:ab:91:3a:58
[    3.703353] r820t 13-003a: creating new instance
[    3.710134] r820t 13-003a: Rafael Micro r820t successfully identified
[    3.710137] r820t 13-003a: attaching existing instance
[    3.715017] r820t 13-003a: Rafael Micro r820t successfully identified
[    3.722972] Hydra chip version 2
[    3.728759] loading firmware, please wait...
[    3.734514] Linux video capture interface: v2.00
[    3.734515] WARNING: You are using an experimental version of the media stack.
                As the driver is backported to an older kernel, it doesn't offer
                enough quality for its usage in production.
                Use it with care.
               Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
                91374e5f36b0f912136b9f46c6b9e34b909fe21c si2157: ISDB-T support.
[    3.762307] frame_vector: module license 'unspecified' taints kernel.
[    3.762309] Disabling lock debugging due to kernel taint
[    3.762342] frame_vector: exports duplicate symbol frame_vector_create (owned by kernel)
[    3.816635] Registered IR keymap rc-empty
[    3.816681] input: Astrometa DVB-T2 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/rc/rc0/input6
[    3.817037] rc rc0: Astrometa DVB-T2 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/rc/rc0
[    3.817176] usb 2-1.6: dvb_usb_v2: schedule remote query interval to 200 msecs
[    3.819416] lirc_dev: IR Remote Control driver registered, major 244
[    3.820656] rc rc0: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
[    3.820657] IR LIRC bridge handler initialized
[    3.825383] usb 2-1.6: dvb_usb_v2: 'Astrometa DVB-T2' successfully initialized and connected
[    3.825406] usbcore: registered new interface driver dvb_usb_rtl28xxu
[    3.839923] EXT4-fs (sdb1): mounting ext3 file system using the ext4 subsystem
[    3.901375] EXT4-fs (sdb1): recovery complete
[    3.901377] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    4.385679] EXT4-fs (md0p1): recovery complete
[    4.417569] EXT4-fs (md0p1): mounted filesystem with ordered data mode. Opts: (null)
[    4.697741] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    4.905914] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[    8.423644] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[    8.423676] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[   29.595490] Hydra FW alive
[   29.653077] chipID=00000001
[   29.654854] chipVer=00000002
[   29.656584] FWVer=0202010a
[   29.688168] TBSECP3 driver 0000:04:00.0: DVB: registering adapter 0 frontend 0 (TurboSight TBS 6909 DVB-S/S2 )...
[   29.688312] DVB: registering new adapter (TBSECP3 DVB Adapter)
[   29.799666] TBSECP3 driver 0000:04:00.0: MAC address 00:22:ab:91:3a:59
[   29.799679] TBSECP3 driver 0000:04:00.0: DVB: registering adapter 2 frontend 0 (TurboSight TBS 6909 DVB-S/S2 )...
[   29.799812] DVB: registering new adapter (TBSECP3 DVB Adapter)
[   29.907077] TBSECP3 driver 0000:04:00.0: MAC address 00:22:ab:91:3a:5a
[   29.907089] TBSECP3 driver 0000:04:00.0: DVB: registering adapter 3 frontend 0 (TurboSight TBS 6909 DVB-S/S2 )...
[   29.907261] DVB: registering new adapter (TBSECP3 DVB Adapter)
[   30.027260] TBSECP3 driver 0000:04:00.0: MAC address 00:22:ab:91:3a:5b
[   30.027272] TBSECP3 driver 0000:04:00.0: DVB: registering adapter 4 frontend 0 (TurboSight TBS 6909 DVB-S/S2 )...
[   30.027410] DVB: registering new adapter (TBSECP3 DVB Adapter)
[   30.147194] TBSECP3 driver 0000:04:00.0: MAC address 00:22:ab:91:3a:5c
[   30.147207] TBSECP3 driver 0000:04:00.0: DVB: registering adapter 5 frontend 0 (TurboSight TBS 6909 DVB-S/S2 )...
[   30.147341] DVB: registering new adapter (TBSECP3 DVB Adapter)
[   30.259220] TBSECP3 driver 0000:04:00.0: MAC address 00:22:ab:91:3a:5d
[   30.259233] TBSECP3 driver 0000:04:00.0: DVB: registering adapter 6 frontend 0 (TurboSight TBS 6909 DVB-S/S2 )...
[   30.259367] DVB: registering new adapter (TBSECP3 DVB Adapter)
[   30.342344] TBSECP3 driver 0000:04:00.0: MAC address 00:22:ab:91:3a:5e
[   30.342356] TBSECP3 driver 0000:04:00.0: DVB: registering adapter 7 frontend 0 (TurboSight TBS 6909 DVB-S/S2 )...
[   30.342493] DVB: registering new adapter (TBSECP3 DVB Adapter)
[   30.418323] TBSECP3 driver 0000:04:00.0: MAC address 00:22:ab:91:3a:5f
[   30.418336] TBSECP3 driver 0000:04:00.0: DVB: registering adapter 8 frontend 0 (TurboSight TBS 6909 DVB-S/S2 )...
[   30.418473] TBSECP3 driver 0000:04:00.0: TurboSight TBS 6909 DVB-S/S2 : PCI 0000:04:00.0, IRQ 34, MMIO 0xf7c00000
[   30.866580] TBSECP3 driver 0000:04:00.0: DVB: adapter 8 frontend 0 frequency 0 out of range (950000..2150000)
[   30.866865] TBSECP3 driver 0000:04:00.0: DVB: adapter 7 frontend 0 frequency 0 out of range (950000..2150000)
[   30.867309] TBSECP3 driver 0000:04:00.0: DVB: adapter 6 frontend 0 frequency 0 out of range (950000..2150000)
[   30.867558] TBSECP3 driver 0000:04:00.0: DVB: adapter 5 frontend 0 frequency 0 out of range (950000..2150000)
[   30.867703] TBSECP3 driver 0000:04:00.0: DVB: adapter 4 frontend 0 frequency 0 out of range (950000..2150000)
[   30.867887] TBSECP3 driver 0000:04:00.0: DVB: adapter 3 frontend 0 frequency 0 out of range (950000..2150000)
[   30.868093] TBSECP3 driver 0000:04:00.0: DVB: adapter 2 frontend 0 frequency 0 out of range (950000..2150000)
[   35.107866] usb 2-1.6: DVB: adapter 1 frontend 0 frequency 0 out of range (174000000..862000000)
[   35.643583] BUG: unable to handle kernel NULL pointer dereference at 0000000000000018
[   35.643611] IP: [<ffffffffc0362966>] mn88473_init+0x46/0x290 [mn88473]
[   35.643631] PGD 0
[   35.643638] Oops: 0000 [#1] SMP
[   35.643648] Modules linked in: ir_lirc_codec(OE) lirc_dev(OE) videobuf2_v4l2(OE) videobuf2_core(OE) videodev(OE) r820t(OE) mxl5xx(OE) mn88473(C) rtl2832(OE) dvb_usb_rtl28xxu(OE) dvb_usb_v2(OE) rc_core(OE) tbsecp3(OE) intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm dcdbas irqbypass crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd serio_raw tas2101(OE) dvb_core(OE) i2c_mux media(OE) mei_me mei shpchp ie31200_edac edac_core 8250_fintek lpc_ich mac_hid autofs4 raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid0 multipath linear raid1 i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect psmouse sysimgblt fb_sys_fops e1000e ahci drm libahci ptp pps_core fjes video
[   35.643880] CPU: 3 PID: 1782 Comm: kdvb-ad-1-fe-1 Tainted: P         C OE   4.4.0-31-generic #50-Ubuntu
[   35.643902] Hardware name: Dell Inc. PowerEdge T20/0VD5HY, BIOS A06 01/27/2015
[   35.643920] task: ffff8805fc000000 ti: ffff88060187c000 task.ti: ffff88060187c000
[   35.643937] RIP: 0010:[<ffffffffc0362966>]  [<ffffffffc0362966>] mn88473_init+0x46/0x290 [mn88473]
[   35.643960] RSP: 0018:ffff88060187fd98  EFLAGS: 00010246
[   35.643973] RAX: 0000000000000000 RBX: ffff880600c6e000 RCX: 0000000000001772
[   35.643990] RDX: ffffffffc0362920 RSI: ffff88061eb99f20 RDI: ffff880602be0030
[   35.644006] RBP: ffff88060187fdd8 R08: 0000000000019f20 R09: ffffffff8156ed9b
[   35.644023] R10: ffffea00180af7c0 R11: 0000000000000000 R12: ffff880602be0030
[   35.644039] R13: ffff8800356fa000 R14: 0000000000000000 R15: 0000000000000000
[   35.644056] FS:  0000000000000000(0000) GS:ffff88061eb80000(0000) knlGS:0000000000000000
[   35.644074] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   35.644088] CR2: 0000000000000018 CR3: 0000000001e0a000 CR4: 00000000001406e0
[   35.644104] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   35.644120] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
[   35.644136] Stack:
[   35.644142]  0000000000000001 ffff88060187fdd8 0000000000000000 00000000b03c95ec
[   35.644162]  ffff8800356fa478 ffff880602be0030 ffff8800356fa000 ffff880600c6e000
[   35.644183]  ffff88060187fe08 ffffffffc03ef6b8 ffff88060187fe58 ffff880602be0030
[   35.644203] Call Trace:
[   35.644213]  [<ffffffffc03ef6b8>] dvb_usb_fe_init+0xb8/0x180 [dvb_usb_v2]
[   35.644233]  [<ffffffffc037f72b>] dvb_frontend_init+0x2b/0xb0 [dvb_core]
[   35.644251]  [<ffffffffc0381314>] dvb_frontend_thread+0x94/0x720 [dvb_core]
[   35.644269]  [<ffffffff81829376>] ? __schedule+0x3b6/0xa30
[   35.644284]  [<ffffffffc0381280>] ? dtv_set_frontend+0x410/0x410 [dvb_core]
[   35.644302]  [<ffffffff810a0808>] kthread+0xd8/0xf0
[   35.644314]  [<ffffffff810a0730>] ? kthread_create_on_node+0x1e0/0x1e0
[   35.644330]  [<ffffffff8182decf>] ret_from_fork+0x3f/0x70
[   35.644343]  [<ffffffff810a0730>] ? kthread_create_on_node+0x1e0/0x1e0
[   35.644358] Code: 48 c7 45 d0 00 00 00 00 65 48 8b 04 25 28 00 00 00 48 89 45 d8 31 c0 f6 05 a9 1b 00 00 04 4c 8b b3 c0 00 00 00 0f 85 a1 01 00 00 <49> 8b 7e 18 48 8d 55 cc 41 c6 86 50 05 00 00 00 be f5 00 00 00
[   35.644455] RIP  [<ffffffffc0362966>] mn88473_init+0x46/0x290 [mn88473]
[   35.644472]  RSP <ffff88060187fd98>
[   35.645102] CR2: 0000000000000018
[   35.647682] ---[ end trace cfa95937fae40857 ]---
[   37.604403] TCP: request_sock_TCP: Possible SYN flooding on port 9982. Sending cookies.  Check SNMP counters.
[   93.377513] TBSECP3 driver 0000:04:00.0: DVB: adapter 8 frontend 0 frequency 0 out of range (950000..2150000)
[   93.377868] TBSECP3 driver 0000:04:00.0: DVB: adapter 7 frontend 0 frequency 0 out of range (950000..2150000)
[   93.378189] TBSECP3 driver 0000:04:00.0: DVB: adapter 6 frontend 0 frequency 0 out of range (950000..2150000)
[   93.378467] TBSECP3 driver 0000:04:00.0: DVB: adapter 5 frontend 0 frequency 0 out of range (950000..2150000)
[   93.378668] TBSECP3 driver 0000:04:00.0: DVB: adapter 4 frontend 0 frequency 0 out of range (950000..2150000)
[   93.378837] TBSECP3 driver 0000:04:00.0: DVB: adapter 3 frontend 0 frequency 0 out of range (950000..2150000)
[   93.379038] TBSECP3 driver 0000:04:00.0: DVB: adapter 2 frontend 0 frequency 0 out of range (950000..2150000)



```

[COLOR=#000000]any help would be greatly appreciated. sorry for bumping the old thread.
I came across this on my google rampage search

If i can get this to work on ubuntu i can see if the problem with the choppy video with dvb-c is related to linux in general or openelec/libreelec.

-

I built the v4l drivers and installed them - but it seems it's recognised as dvb-s, so i can't select dvb-c network

[/COLOR][IMG]http://i64.tinypic.com/ok1oiv.png[/IMG]

---

### Post by walterav on 2017-02-14
Hi there,

You are showing incomplete/inconsistent info I believe, so to start my blind guess work of what might be good/wrong:

>  I've got the same tuner as in your example.
Please add the terminal output of 'lsusb', because there are alot of cheap USB DVB adapters which share same chipset but also other components (demodulaters/tuners/filters) and therefor have different tuners working dvb-t(2) dvb-c /v4l2/SDR/etc. Some cheap/exotic usb-dvb-x adapters will work, some will eventually (newer kernel/hacking attempts) and some will probably never work.

> I got it to work with openelec/libreelec - it sees all the tuners (including dvb-c), but the quality is too bad to watch, and sometimes doesn't work at all..
The bad quality thing, although it was working a little bit is related to bad signal tuning reception on higher Mhz transponders with the linux driver(Microsoft Windows driver not affected). You probably did nothing wrong here and did a correct observation.
> so i tested on windows with progdvb and it works flawless.
Correct, this is a known bug and [s]as far as I know a still un[/s]solved bug related to tuner component r820t. The tvheadend forum user &#1069;&#1076;&#1091;&#1072;&#1088;&#1076; &#1052;&#1103;&#1075;&#1080; addresses a patch that worked for me:
[https://tvheadend.org/boards/5/topics/22310?r=25348#message-25348]("https://tvheadend.org/boards/5/topics/22310?r=25348#message-25348")
Although using high quality shielded cable's and connectors also does improve a lot[s], however some transponders still won't tune in Linux compared to Windows[/s]. Its also a good idea to show which kernel version OpenElec was using by typing in the terminal 'uname -a'.

>  I currently have a TBS6909 (octo tuner) connected to 3 satellites by diseqc. all works flawless.
Good its working, its also a good idea to mention if you are running opensource or proprietary drivers for this TBS octo tuner? Also post terminal output of 'lspci'. Are you aware Linux DVB has some strange numbering limitations to be compatible with older DVB api's?  For instance /dev/dvb/adapter0-x, if your TBS octo claims all these early numbers /dev/dvb/fronted numbers, that might be a cause for the USB DVB-C tuner not working (just guessing)?

>  I put in the USB device and tvheadend showed only the dvb-T device (along with my tbs card).
This is correct and normal behaviour(missing firmware) that it will only show DVB-T tuner.

>  i checked 'dmesg' and i didn't see any error with it not finding the firmware.
Very good you checked 'dmesg', it shows valuable info look at 35 seconds uptime... there is a little kernel oops/panic happening relating to your USB-DVB tuner.

```
[   35.643583] BUG: unable to handle kernel NULL pointer dereference at 0000000000000018
[   35.643611] IP: [<ffffffffc0362966>] mn88473_init+0x46/0x290 [mn88473]
[   35.643631] PGD 0
[   35.643638] Oops: 0000 [#1] SMP
[   35.643648] Modules linked in: ir_lirc_codec(OE) lirc_dev(OE) videobuf2_v4l2(OE) videobuf2_core(OE) videodev(OE) r820t(OE) mxl5xx(OE) mn88473(C) rtl2832(OE) dvb_usb_rtl28xxu(OE) dvb_usb_v2(OE) rc_core(OE) tbsecp3(OE) intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm dcdbas irqbypass crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd serio_raw tas2101(OE) dvb_core(OE) i2c_mux media(OE) mei_me mei shpchp ie31200_edac edac_core 8250_fintek lpc_ich mac_hid autofs4 raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid0 multipath linear raid1 i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect psmouse sysimgblt fb_sys_fops e1000e ahci drm libahci ptp pps_core fjes video
[   35.643880] CPU: 3 PID: 1782 Comm: kdvb-ad-1-fe-1 Tainted: P         C OE   4.4.0-31-generic #50-Ubuntu
[   35.643902] Hardware name: Dell Inc. PowerEdge T20/0VD5HY, BIOS A06 01/27/2015
[   35.643920] task: ffff8805fc000000 ti: ffff88060187c000 task.ti: ffff88060187c000
[   35.643937] RIP: 0010:[<ffffffffc0362966>]  [<ffffffffc0362966>] mn88473_init+0x46/0x290 [mn88473]
[   35.643960] RSP: 0018:ffff88060187fd98  EFLAGS: 00010246
[   35.643973] RAX: 0000000000000000 RBX: ffff880600c6e000 RCX: 0000000000001772
[   35.643990] RDX: ffffffffc0362920 RSI: ffff88061eb99f20 RDI: ffff880602be0030
[   35.644006] RBP: ffff88060187fdd8 R08: 0000000000019f20 R09: ffffffff8156ed9b
[   35.644023] R10: ffffea00180af7c0 R11: 0000000000000000 R12: ffff880602be0030
[   35.644039] R13: ffff8800356fa000 R14: 0000000000000000 R15: 0000000000000000
[   35.644056] FS:  0000000000000000(0000) GS:ffff88061eb80000(0000) knlGS:0000000000000000
[   35.644074] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   35.644088] CR2: 0000000000000018 CR3: 0000000001e0a000 CR4: 00000000001406e0
[   35.644104] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   35.644120] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
[   35.644136] Stack:
[   35.644142]  0000000000000001 ffff88060187fdd8 0000000000000000 00000000b03c95ec
[   35.644162]  ffff8800356fa478 ffff880602be0030 ffff8800356fa000 ffff880600c6e000
[   35.644183]  ffff88060187fe08 ffffffffc03ef6b8 ffff88060187fe58 ffff880602be0030
[   35.644203] Call Trace:
[   35.644213]  [<ffffffffc03ef6b8>] dvb_usb_fe_init+0xb8/0x180 [dvb_usb_v2]
[   35.644233]  [<ffffffffc037f72b>] dvb_frontend_init+0x2b/0xb0 [dvb_core]
[   35.644251]  [<ffffffffc0381314>] dvb_frontend_thread+0x94/0x720 [dvb_core]
[   35.644269]  [<ffffffff81829376>] ? __schedule+0x3b6/0xa30
[   35.644284]  [<ffffffffc0381280>] ? dtv_set_frontend+0x410/0x410 [dvb_core]
[   35.644302]  [<ffffffff810a0808>] kthread+0xd8/0xf0
[   35.644314]  [<ffffffff810a0730>] ? kthread_create_on_node+0x1e0/0x1e0
[   35.644330]  [<ffffffff8182decf>] ret_from_fork+0x3f/0x70
[   35.644343]  [<ffffffff810a0730>] ? kthread_create_on_node+0x1e0/0x1e0
[   35.644358] Code: 48 c7 45 d0 00 00 00 00 65 48 8b 04 25 28 00 00 00 48 89 45 d8 31 c0 f6 05 a9 1b 00 00 04 4c 8b b3 c0 00 00 00 0f 85 a1 01 00 00 <49> 8b 7e 18 48 8d 55 cc 41 c6 86 50 05 00 00 00 be f5 00 00 00
[   35.644455] RIP  [<ffffffffc0362966>] mn88473_init+0x46/0x290 [mn88473]
[   35.644472]  RSP <ffff88060187fd98>
[   35.645102] CR2: 0000000000000018
[   35.647682] ---[ end trace cfa95937fae40857 ]---
[   37.604403] TCP: request_sock_TCP: Possible SYN flooding on port 9982. Sending cookies.  Check SNMP counters.
```

It also shows you are using the TBS octo tuner.

Did you try a clean ubuntu server install with only the USB-DVB connected, without the TBS octo dvb-s?

>  I built the v4l drivers and installed them - but it seems it's recognised as dvb-s, so i can't select dvb-c network
Its not necessary to build v4l2, that is mostly related to analoge tuning devices.

About the screenshot (I also need to do this in my tutorial ;-)), why doesn't it show the TBS octo DVB-s hardware?

---

### Post by bitaljus on 2017-06-02
Hello @walterav,
Thanks for the great tutorial :)

I saw that you are using custom pipes to add IP cams and other video streams, but can this approach be used for live tv directly from the tuner? I want to implement some kind of HW accelerated transcoding but only information is about Intel cards and I have ATI..
Can you give me some information is it even possible or I need to forget about it?

---

### Post by walterav on 2017-06-03
> **bitaljus said:**
> Hello @walterav,
Thanks for the great tutorial :)

I saw that you are using custom pipes to add IP cams and other video streams, but can this approach be used for live tv directly from the tuner? I want to implement some kind of HW accelerated transcoding but only information is about Intel cards and I have ATI..
Can you give me some information is it even possible or I need to forget about it?

I have no idea what you are trying to accomplish, maybe add some info about the hardware/software your are intending to use or  what the actual source of your video is and what the actual destination / end goal is?

---

### Post by djflix on 2017-06-11
> **walterav said:**
> 
[COLOR=#000000]Setup DVB Tuner(s):[/COLOR]
[COLOR=#000000]This time we will setup a DVB-C usb tuner from Microsoft, the XBOX ONE Digital TV TUNER for use with Tvheadend. TODO[/COLOR]


What is the current status on this? Is there still work to be done on getting this combo working or is the only issue that the steps haven't been documented yet? I can't seem to find anything documented about this specific tuner that implies that it's working at all on Ubuntu 16.04... (specifically using VID [COLOR=#000000]045e and PID 02d5). I'd like to contribute but I'm not sure where to begin.[/COLOR]

---

### Post by walterav on 2017-06-13
@djflix

Its working in ubuntu 16.04 HWE kernel 4.10 amd64 (both dvb-c and dvb-t tested) with a 1.3GB big media_tree/build tar file I was able to obtain from one of the users from the tvheadend thread. My goal is to complete the github version with the changes found in the 1.3GB tar since they differ and make that github version work with the general walkthrough for linux.org V4L-DVB and than update this howto. But I'm not able to get any repetitive results. Can we keep in contact via PM and keep this thread clean until some things are sorted out?

---

### Post by ajgreeny on 2018-12-09
Thread reopened for editing.

---

### Post by walterav on 2018-12-24
**[size=+2]part3:Tvheadend mpegts recordings lossless cut, split, trim and remuxing using ffmpeg[/size]**

Recordings made by Tvheadend using the pass profile keep the original DVB mpegts stream intact, these bigger files gives the possibility of remuxing specific/extra audio/subtitle steams into other video container like mp4/mkv without quality loss nor the need to re-encode audio video data. For DVB streams containing mpeg2/h264/ac3/mp2/teletext-subtitles, the following ffmpeg command creates a mp4 file which plays natively on Windows 10 "Movies TV App" and Mac OS "Quicktime" and can even be imported/edited in Premiere Pro CC without audio sync issues. However these files won't play a/v sync on a standalone philips bluray player, so more investigations is needed...! This works well for SD&HD streams from DVB-C provider Ziggo and some DVB-S/S2 satellite providers (except the subtitles). However the new DVB-T2 Digitenne streams come with "h265" video and "aac latm" with the first requiring a hevc specific ffmpeg flag " -tag:v hvc1" to create a Apple Quicktime compatible mp4, however the audio part refuses to be remuxed success into a mp4 by ffmpeg since it requires aac to be in adts for mp4. As a workaround MKV container might be an option but will not be compatible with default Apple apps.   

```

#install ffmpeg
sudo apt-get -y install ffmpeg

#investigate videorecording.ts
ffprobe videorecording.ts

#search which stream numbers are video/audio/subtitle content 

#DVB-C HD trim & remux command notice input/output filenames /stream numbers / and timecode 9 minute 12 to 59 minute 12
ffmpeg -fix_sub_duration -txt_format text -txt_page 888 -i videorecording.ts -ss 00:09:12 -to 00:59:12 -map 0:0 -map 0:2 -c copy -map 0:4 -scodec mov_text outputvideo.mp4

#DVB-T2 HD h265&aac_latm 
ffmpeg -fix_sub_duration -txt_format text -txt_page 888 -i videorecordingDVBT2.ts -map 0:0 -c copy -map 0:1 -tag:v hvc1 -map 0:2 -scodec mov_text outputvideo.mkv


```

Research:
* metadata chapter support in mp4?
* mpegts streams containing mpeg2 video and or audio codecs container compatibility av sync?
* av sync issues on standalone bluray players/smartv/setopbox?

---

### Post by walterav on 2019-08-16
DVB-T2 
Since the 9th of July DVB-T2 replaced DVB-T in our area (Zuid-Holland) and has been tested successful with FTA channels (1080p50 h265 8bit/yuv420 + aac + teletext) at 722mHz using different USB tuners.

---

### Post by helicase on 2019-08-31
When I tried to set this up the channel scan failed at first. Turns out the Ziggo presets do not cover all of the Netherlands (perhaps because some areas had UPC before?). Anyway, changing the frequencies manually did the trick. The correct frequencies for each area can be found on the ZIggo website.

---

### Post by walterav on 2019-09-02
> **helicase said:**
> When I tried to set this up the channel scan failed at first. Turns out the Ziggo presets do not cover all of the Netherlands (perhaps because some areas had UPC before?). 

Which version of Tvheadend are you running, since only pre 4.2 needed manual mux frequency editing. Most scans can be done at 474MHz with different network id's to filter region or subscriptions for region Noord Holland en Zuid Holland.

> Anyway, changing the frequencies manually did the trick. The correct frequencies for each area can be found on the ZIggo website.

Good to hear you got it working, maybe you could post the mux/transponder frequency you needed to change for your region?

BTW: Also the "network discovery" setting can affect channel search, set it to "new + changed muxes" than it will find/add more muxes and channels than the default from tvheadend itself. I edited the first topic with this usefull option.

---

