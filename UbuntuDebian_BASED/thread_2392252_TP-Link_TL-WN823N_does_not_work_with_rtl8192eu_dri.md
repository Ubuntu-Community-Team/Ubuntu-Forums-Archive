---
title: "TP-Link TL-WN823N does not work with rtl8192eu driver"
date: 2018-05-18
forum: Ubuntu/Debian BASED
---

### Post by piucco on 2018-05-18
[FONT=arial]I followed [these]("https://ubuntuforums.org/showthread.php?t=2351228&p=13601820#post13601820") steps to setup rtl192eu driver for my TP-Link TL-WN823N wifi device and dkms status showed me that it was installed, but it still does not work.

Device: [TP-Link ]("https://www.tp-link.com/en/download/TL-WN823N_V2.html#Driver")[/FONT][FONT=arial][TL-WN823N V2]("https://www.tp-link.com/en/download/TL-WN823N_V2.html#Driver")
Ubuntu 16.04

lsusb

[/FONT]```
[FONT=arial]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=arial]Bus 002 Device 007: ID 2357:0109  [/FONT]
[FONT=arial]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=arial]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=arial]Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver[/FONT]
[FONT=arial]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=arial]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=arial]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=arial]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]

```[FONT=arial]

uname -r

[/FONT]```
[FONT=arial]4.13.0-41-generic[/FONT]

```[FONT=arial]

[/FONT][FONT=arial]I am using the following git repository: [https://github.com/Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver)

I believe the problem is the kernel version. 

How do I solve this? Its very annoying to have to waste time trying to make a popular device work. Why does ubuntu do not support this device automatically? I cant undestand... 

If I solve the problem manually, I'll probably have to keep doing this with every kernel update, right? That is terrible.
[/FONT]

---

### Post by jeremy31 on 2018-05-18
Post results for ```
modprobe -c | grep 0109
```

---

### Post by piucco on 2018-05-18
```
piucco@piucco-pc:~$ modprobe -c | grep 0109
alias pci:v00001093d00000160sv*sd*bc*sc*i* 8255_pci
alias pci:v00001093d00000161sv*sd*bc*sc*i* ni_labpc_pci
alias pci:v00001093d00000162sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00000400sv*sd*bc*sc*i* 8255_pci
alias pci:v00001093d00001150sv*sd*bc*sc*i* ni_pcidio
alias pci:v00001093d00001170sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00001180sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00001190sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000011B0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000011C0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000011D0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00001250sv*sd*bc*sc*i* 8255_pci
alias pci:v00001093d00001270sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00001290sv*sd*bc*sc*i* ni_670x
alias pci:v00001093d000012B0sv*sd*bc*sc*i* ni_pcidio
alias pci:v00001093d00001310sv*sd*bc*sc*i* ni_660x
alias pci:v00001093d00001320sv*sd*bc*sc*i* ni_pcidio
alias pci:v00001093d00001330sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00001340sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00001350sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00001360sv*sd*bc*sc*i* ni_660x
alias pci:v00001093d000013C0sv*sd*bc*sc*i* 8255_pci
alias pci:v00001093d000014E0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000014F0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00001580sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000015B0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00001630sv*sd*bc*sc*i* 8255_pci
alias pci:v00001093d00001710sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000017D0sv*sd*bc*sc*i* 8255_pci
alias pci:v00001093d00001800sv*sd*bc*sc*i* 8255_pci
alias pci:v00001093d00001870sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00001880sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000018B0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000018C0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00001920sv*sd*bc*sc*i* ni_670x
alias pci:v00001093d00001E30sv*sd*bc*sc*i* ni_660x
alias pci:v00001093d00001E40sv*sd*bc*sc*i* ni_660x
alias pci:v00001093d00002410sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002420sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002430sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002890sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000028C0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002A60sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002A70sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002A80sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002AB0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002B10sv*sd*bc*sc*i* ni_6527
alias pci:v00001093d00002B20sv*sd*bc*sc*i* ni_6527
alias pci:v00001093d00002B80sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002B90sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002C60sv*sd*bc*sc*i* ni_660x
alias pci:v00001093d00002C80sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002C90sv*sd*bc*sc*i* ni_670x
alias pci:v00001093d00002CA0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00002CC0sv*sd*bc*sc*i* ni_660x
alias pci:v00001093d00007085sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d00007086sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d00007087sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d00007088sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000070A9sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000070AAsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070ABsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070ACsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070ADsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070AEsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070AFsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070B0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070B1sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070B2sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070B3sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070B4sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070B5sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070B6sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070B7sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070B8sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070B9sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070BAsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070BBsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070BCsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070BDsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070BEsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070BFsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070C0sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070C3sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000070C8sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000070C9sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000070CCsv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000070CDsv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000070D1sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000070D2sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000070D3sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000070F2sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000070F3sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d0000710Dsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d00007124sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d00007125sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d00007126sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d00007127sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d00007128sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d0000716Csv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d0000716Dsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d0000717Dsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d0000717Fsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d0000718Bsv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d0000718Csv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000071BCsv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000071C5sv*sd*bc*sc*i* ni_65xx
alias pci:v00001093d000072E8sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001093d000072E9sv*sd*bc*sc*i* ni_pcimio
alias pci:v00001095d00000240sv*sd*bc*sc*i* sata_sil
alias pci:v00001095d00000242sv*sd*bc*sc*i* sata_sil24
alias pci:v00001095d00000244sv*sd*bc*sc*i* sata_sil24
alias pci:v00001095d00000640sv*sd*bc*sc*i* pata_cmd640
alias pci:v00001095d00000643sv*sd*bc*sc*i* pata_cmd64x
alias pci:v00001095d00000646sv*sd*bc*sc*i* pata_cmd64x
alias pci:v00001095d00000648sv*sd*bc*sc*i* pata_cmd64x
alias pci:v00001095d00000649sv*sd*bc*sc*i* pata_cmd64x
alias pci:v00001095d00000680sv*sd*bc*sc*i* pata_sil680
alias pci:v00001095d00003112sv*sd*bc*sc*i* sata_sil
alias pci:v00001095d00003114sv*sd*bc*sc*i* sata_sil
alias pci:v00001095d00003124sv*sd*bc*sc*i* sata_sil24
alias pci:v00001095d00003131sv*sd*bc*sc*i* sata_sil24
alias pci:v00001095d00003132sv*sd*bc*sc*i* sata_sil24
alias pci:v00001095d00003512sv*sd*bc*sc*i* sata_sil
alias pci:v00001095d00003531sv*sd*bc*sc*i* sata_sil24
alias pci:v0000109Ed00000350sv*sd*bc*sc*i* bttv
alias pci:v0000109Ed00000351sv*sd*bc*sc*i* bttv
alias pci:v0000109Ed0000036Csv*sd*bc*sc*i* bttv
alias pci:v0000109Ed0000036Esv*sd*bc*sc*i* bttv
alias pci:v0000109Ed0000036Fsv*sd*bc*sc*i* bttv
alias pci:v0000109Ed00000878sv00000070sd000013EBbc*sc*i* snd_bt87x
alias pci:v0000109Ed00000878sv00000070sd0000FF01bc*sc*i* snd_bt87x
alias pci:v0000109Ed00000878sv00000070sd0000FF07bc*sc*i* snd_bt87x
alias pci:v0000109Ed00000878sv00000071sd00000101bc*sc*i* bt878
alias pci:v0000109Ed00000878sv00001002sd00000001bc*sc*i* snd_bt87x
alias pci:v0000109Ed00000878sv0000107Dsd00006606bc*sc*i* snd_bt87x
alias pci:v0000109Ed00000878sv000011BDsd00000012bc*sc*i* snd_bt87x
alias pci:v0000109Ed00000878sv000011BDsd0000001Cbc*sc*i* bt878
alias pci:v0000109Ed00000878sv000011BDsd00000026bc*sc*i* bt878
alias pci:v0000109Ed00000878sv0000121Asd00003000bc*sc*i* snd_bt87x
alias pci:v0000109Ed00000878sv0000144Fsd00003000bc*sc*i* snd_bt87x
alias pci:v0000109Ed00000878sv00001461sd00000003bc*sc*i* snd_bt87x
alias pci:v0000109Ed00000878sv00001461sd00000761bc*sc*i* bt878
alias pci:v0000109Ed00000878sv00001461sd00000771bc*sc*i* bt878
alias pci:v0000109Ed00000878sv00001554sd00004011bc*sc*i* snd_bt87x
alias pci:v0000109Ed00000878sv00001822sd00000001bc*sc*i* bt878
alias pci:v0000109Ed00000878sv00001822sd00000026bc*sc*i* bt878
alias pci:v0000109Ed00000878sv000018ACsd0000D500bc*sc*i* bt878
alias pci:v0000109Ed00000878sv000018ACsd0000DB10bc*sc*i* bt878
alias pci:v0000109Ed00000878sv000018ACsd0000DB11bc*sc*i* bt878
alias pci:v0000109Ed00000878sv0000270Fsd0000FC00bc*sc*i* bt878
alias pci:v0000109Ed00000878sv00007063sd00002000bc*sc*i* bt878
alias pci:v0000109Ed00000878sv0000BD11sd00001200bc*sc*i* snd_bt87x
alias pci:v0000109Ed00000879sv00000070sd000013EBbc*sc*i* snd_bt87x
alias pci:v0000109Fd0000036Fsv*sd*bc*sc*i* dm1105
alias pci:v000010B8d00000005sv00001092sd00000AB4bc*sc*i* epic100
alias pci:v00001969d00001090sv*sd*bc*sc*i* alx
alias pci:v00001969d00001091sv*sd*bc*sc*i* alx
alias pci:v00008086d00000F15sv00001093sd00007884bc*sc*i* sdhci_pci
alias pci:v00008086d00001091sv*sd*bc02sc00i* e100
alias pci:v00008086d00001092sv*sd*bc02sc00i* e100
alias pci:v00008086d00001093sv*sd*bc02sc00i* e100
alias pci:v00008086d00001094sv*sd*bc02sc00i* e100
alias pci:v00008086d00001095sv*sd*bc02sc00i* e100
alias pci:v00008086d00001096sv*sd*bc*sc*i* e1000e
alias pci:v00008086d00001098sv*sd*bc*sc*i* e1000e
alias pci:v00008086d00001099sv*sd*bc*sc*i* e1000
alias pci:v00008086d0000109Asv*sd*bc*sc*i* e1000e
alias pci:v00008086d0000109Esv*sd*bc*sc*i* ixgb
alias pcmcia:m0109c0501f*fn*pfn00pa*pb*pc*pd* smc91c92_cs
alias pcmcia:m0109c0501f*fn*pfn01pa*pb*pc*pd* serial_cs
alias usb:v04CBp0109d*dc*dsc*dp*ic*isc*ip*in* gspca_finepix
alias usb:v050Dp0109d*dc*dsc*dp*ic*isc*ip*in* mct_u232
alias usb:v06CDp0109d*dc*dsc*dp*ic*isc*ip*in* keyspan
alias usb:v08CAp0109d*dc*dsc*dp*ic*isc*ip*in* zr364xx
alias usb:v0B39p0109d*dc*dsc*dp*ic*isc*ip*in* pegasus
alias usb:v1B3Dp0109d*dc*dsc*dp*ic*isc*ip*in* ftdi_sio
alias usb:v2304p0109d*dc*dsc*dp*ic*isc*ip*in* usbvision
alias usb:v2357p0109d*dc*dsc*dp*icFFiscFFipFFin* rtl8xxxu

```

---

### Post by jeremy31 on 2018-05-18
That shows that card is supported by the rtl8xxxu module
See the wireless script link in my signature and post results

---

### Post by piucco on 2018-05-18
Follow the script result: [http://paste.ubuntu.com/p/mxmPxmsttn/](http://paste.ubuntu.com/p/mxmPxmsttn/)

-edit

Sorry, I put another wifi adapter to use the internet and forgot to change to TP-Link, give me a second

---

### Post by piucco on 2018-05-18
Follow the correct result: [http://paste.ubuntu.com/p/DdzB36y9QN/](http://paste.ubuntu.com/p/DdzB36y9QN/)

Note: Sometimes changing usb port solves the problem for a while, but after some time the connection becomes inactive or unstable

---

### Post by jeremy31 on 2018-05-18
Lets try ```
echo "options 8192eu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/8192eu.conf
```
```
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```
Reboot, if it doesn't work at all do ```
sudo modprobe rtl8xxxu
```

---

### Post by piucco on 2018-05-18
[COLOR=#212121][FONT=arial]The first 2 commands and reboot did not solve the problem[/FONT][/COLOR]
[COLOR=#212121][FONT=arial]
After reboot, I did "sudo modprobe rtl8xxxu" [/FONT][/COLOR][COLOR=#212121][FONT=arial]and the wifi started working and connected on the network, but with instability, from 10mb that I have, picked between 2 and 3mb only.
[/FONT][/COLOR][COLOR=#212121][FONT=arial]
After all this I rebooted again and stopped working again.

[/FONT][/COLOR][COLOR=#212121][FONT=arial]I noticed one more thing, when I plugged in the TP-link device, my wireless mouse gets unstable, with interference[/FONT][/COLOR][COLOR=#212121][FONT=arial]

[/FONT][/COLOR]

---

### Post by jeremy31 on 2018-05-18
Reboot and run ```
./wireless-info
```
Then do the ```
sudo modprobe rtl8xxxu
```
Then post the new wireless-info.**txt** file

---

### Post by piucco on 2018-05-18
I am using my notebook right now, the last wireless-info was from my desktop at work. The problem persists, so I believe I can continue testing. Same kernel and ubuntu 16.04

I rebooted and here is my wireless-info: [https://pastebin.com/rS8FSqmZ](https://pastebin.com/rS8FSqmZ) (tp-link device is not working)

After sudo modprobe rtl8xxxu: [https://pastebin.com/YuWNzkm6](https://pastebin.com/YuWNzkm6) (tp-link device is working, but unstable)

---

### Post by piucco on 2018-05-22
Ok, I reinstalled the driver again as following and everything is working perfectly, i dont know why it did not work before... 

> sudo apt-get install git linux-headers-generic build-essential dkms
git clone [https://github.com/Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver)
cd rtl8192eu-linux-driver
sudo dkms add .
sudo dkms install rtl8192eu/1.0

---

### Post by jeremy31 on 2018-05-22
Moved to Ubuntu/Debian based as it involves Elementary OS

I am not sure what happens in some of these kernels but I suspect the module is getting built against the wrong headers somehow

---

