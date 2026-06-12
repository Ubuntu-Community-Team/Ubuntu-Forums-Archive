---
title: "Unable to activate wireless on ThinkPAD E570 with Loki 0.4.1"
date: 2017-09-11
forum: Ubuntu/Debian BASED
---

### Post by davemalone on 2017-09-11
[COLOR=#242729][FONT=Arial]Hello friends,

After installing Loki 0.4.1 with Kernel 4.10... the wireless material or driver can't found, I udpate to kernel 4.13.1-041301-generic, always wireless don't found. With some command this is result :

[/FONT][/COLOR]```
[COLOR=#242729][FONT=Consolas]~$ : lspci [/FONT][/COLOR]
 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10) 
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device c821
```[FONT=Arial]
And also :
[/FONT]```
~$ : lshw -C network *-network               
   description: Ethernet interface
   product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
   vendor: Realtek Semiconductor Co., Ltd.
   physical id: 0
   bus info: pci@0000:04:00.0
   logical name: enp4s0
   version: 10
   serial: 54:e1:ad:3f:f2:58
   size: 10Mbit/s
   capacity: 1Gbit/s
   width: 64 bits
   clock: 33MHz
   capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
   resources: irq:122 ioport:c000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff

  *-network UNCLAIMED
   description: Network controller
   product: Realtek Semiconductor Co., Ltd.
   vendor: Realtek Semiconductor Co., Ltd.
   physical id: 0
   bus info: pci@0000:05:00.0
   version: 00
   width: 64 bits
   clock: 33MHz
   capabilities: cap_list
   configuration: latency=0
resources: ioport:b000(size=256) memory:f2000000-f200ffff
```[FONT=Arial]
[/FONT][COLOR=#242729][FONT=Arial]As you can see there is a network "UNCLAIMED". According to Lenovo the Wireless is Intel Wireless 8265/8275.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So please help me to install and activate the wireless. thanks[/FONT][/COLOR]

---

### Post by praseodym on 2017-09-11
Maybe this device is not supported (yet)?! Please show
```

lspci -nnk
```

---

### Post by davemalone on 2017-09-12
Thanks. Below is what i get :

```
[COLOR=#242729][FONT=Consolas]~$ : lspci -nnk
[/FONT][/COLOR]04:00.0 Ethernet controller[0280]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)  
         Subsystem : Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:505b]
         Kernel driver in use: r8169
         Kernel modules : r8169

05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:c821]
[COLOR=#222222][FONT=Verdana]             Subsystem : Lenovo Device [17aa:c024][/FONT][/COLOR]
```

---

### Post by praseodym on 2017-09-13
It looks like the driver (probably rtl8821ce) is currently under development :(

---

### Post by davemalone on 2017-09-13
So for now I can not do nothing but wait. that's it i think. :cry::cry::cry:

---

### Post by praseodym on 2017-09-13
Maybe buying a 10 $ stick?!

---

### Post by davemalone on 2017-09-14
10$ to have the driver?:(:(

---

### Post by jeremy31 on 2017-09-14
*Thread moved to **Ubuntu/Debian BASED**.*
praseodym meant to buy a compatible USB wireless device

---

### Post by davemalone on 2017-09-14
[COLOR=#000000]USB wireless device !!! Ok thanks[/COLOR]

---

### Post by praseodym on 2017-09-18
In the German forum, flash63 works on a solution. Please stay tuned

---

### Post by davemalone on 2017-09-21
Ok i stay tuned. Thanks

---

### Post by praseodym on 2017-09-21
You can try it (without warranty!), it compiles here:
```

wget https://media-cdn.ubuntu-de.org/forum/attachments/09/38/8887285-rtl8821ce_Test_2b.tar.bz2
tar xvf 8887285-rtl8821ce_Test_2b.tar.bz2
cd rtl8821ce_Test_2b/
make
```
Compiled without error? Then
```

sudo make install
sudo modprobe -v rtl8821ae
dmesg | grep rtl
iwconfig
iwlist chan
sudo iwlist scan
```
From here:
[https://forum.ubuntuusers.de/topic/wlan-probleme-mit-lenovo-e570/#post-8887285](https://forum.ubuntuusers.de/topic/wlan-probleme-mit-lenovo-e570/#post-8887285)

---

### Post by davemalone on 2017-09-22
Ok I stay tuned. Thanks

---

### Post by praseodym on 2017-09-22
Did you try it?

---

### Post by davemalone on 2017-10-05
Hi
Please any update?? Thanks

---

### Post by praseodym on 2017-10-08
Did you try that driver?

---

### Post by earadriel on 2017-10-09
sudo modprobe -v rtl8821ae

```
insmod /lib/modules/4.13.0-12-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko 
modprobe: ERROR: could not insert 'rtl8821ae': Required key not available
```

---

### Post by praseodym on 2017-10-09
Deactivate Secure Boot. If the computer freezes, activate it again

---

### Post by davemalone on 2017-10-15
Hello team,
I download and execute some command tell by [COLOR=#000000]**praseodym **[/COLOR]and when execute this command :> [COLOR=#000000]sudo modprobe -v rtl8821ae[/COLOR]Computer crashed.
Even if desactivate or activate the Boot secure in BIOS the computer crashe at boot. 
The computer work only if i desactivate the wireless device in BIOS.

So please help

---

### Post by praseodym on 2017-10-15
Ok, so we need to wait until Realtek provides a driver for that device. Uninstall the driver via

```
cd rtl8821ce_Test_2b/
sudo make uninstall
```

---

### Post by kurt18947 on 2017-10-15
I'd check into well proven USB devices.  It's worth having one of those in your toolbox even if everything were working well. If a problem crops up and there's a question of hardware or software problem, having  known-good hardware can be useful.

---

### Post by davemalone on 2017-10-16
Hello team
After > [COLOR=#000000][FONT=&quot]cd rtl8821ce_Test_2b/
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]sudo make uninstall[/FONT][/COLOR]
And reboot => Activated wireless device in BIOS => Desactivate Secure Boot => Computer still crahed. 
I have to desactivate the wireless device to make computer work.
:confused::confused::confused:

---

### Post by evassilyev on 2017-10-24
[COLOR=#242729][FONT=Arial]Worked solution (Requirements: **kernel >=4.11**) :[/FONT][/COLOR]

[LIST=1]
[*]Download driver directory from this repo:[https://github.com/endlessm/linux/tree/master/drivers/net/wireless/rtl8821ce](https://github.com/endlessm/linux/tree/master/drivers/net/wireless/rtl8821ce). You can do it by this link: [https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/endlessm/linux/tree/master/drivers/net/wireless/rtl8821ce](https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/endlessm/linux/tree/master/drivers/net/wireless/rtl8821ce)
[*]Unpack zip archive.
[*]Change the **Makefile**. Line "export TopDIR ?= ..." to export "TopDIR ?= PATH TO EXTRACTED DIRECTORY".
[*]make
[*]sudo make install
[*]sudo modprobe -a 8821ce
[/LIST]

---

### Post by praseodym on 2017-11-20
Confirmed that it works with kernel >=4.13. Both 4.10 and 4.11 did not work. Don't forget those kernel headers ;)

---

### Post by Mike Silberg on 2017-11-21
Solution of installing driver **rtl8821ce** from Endlessm repo worked for me too on my Thinkpad E470 and now WiFi just works.

However  I'm still having problems with Bluetooth, it simply doesn't start so I  can't see other BT devices.

It seems to me that a new upstream driver still doesn't support it. Isn't it that, am I missing something?

---

### Post by jeremy31 on 2017-11-21
Mike Silberg
Bluetooth might not work due to a lack of firmware as I don't see any file specific to the rtl8821ce at [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/rtl_bt](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/rtl_bt)

---

### Post by Mike Silberg on 2017-11-21
I'm wondering how much time it will take to maintainers to add this firmware support to the kernel.

Is there any schedule with a new hardware to be added in the future?

---

### Post by vasa1 on 2017-11-21
> **Mike Silberg said:**
> I'm wondering how much time it will take to maintainers to add this firmware support to the kernel.

Is there any schedule with a new hardware to be added in the future?You'd have a better chance of being answered correctly in the forum for Loki: [https://elementaryforums.com/index.php](https://elementaryforums.com/index.php)

---

### Post by Mike Silberg on 2017-11-21
> You'd have a better chance of being answered correctly in the forum for Loki: [https://elementaryforums.com/index.php](https://elementaryforums.com/index.php)

:D I'm using Ubuntu 17.10. But my issue was the same as in this thread.

---

### Post by Mike Silberg on 2017-12-05
Here's an update plans of **rtl8821ce** driver support by upstream kernel [https://www.spinics.net/lists/linux-wireless/msg166957.html](https://www.spinics.net/lists/linux-wireless/msg166957.html)

---

### Post by gusmagna on 2017-12-25
Hi Evassilyev! I have the same problem. I bought a Lenovo Thinkpad E470 the other day and the wifi was not available. I have followed your guide above and downloaded the driver directory from [https://minhaskamal.github.io]("https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/endlessm/linux/tree/master/drivers/net/wireless/rtl8821ce") and unpacked the zip-file. However, I do not understand what you mean in 3) "Change the **Makefile**. Line "export TopDIR ?= ..." to export "TopDIR ?= PATH TO EXTRACTED DIRECTORY".". Can you please describe this in another way? I cannot find the words export TopDIR?= anywhere. Thanks!

---

### Post by chili555 on 2017-12-30
> **gusmagna said:**
> Hi Evassilyev! I have the same problem. I bought a Lenovo Thinkpad E470 the other day and the wifi was not available. I have followed your guide above and downloaded the driver directory from [https://minhaskamal.github.io]("https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/endlessm/linux/tree/master/drivers/net/wireless/rtl8821ce") and unpacked the zip-file. However, I do not understand what you mean in 3) "Change the **Makefile**. Line "export TopDIR ?= ..." to export "TopDIR ?= PATH TO EXTRACTED DIRECTORY".". Can you please describe this in another way? I cannot find the words export TopDIR?= anywhere. Thanks!Please see: [https://askubuntu.com/questions/990378/wifi-not-working-on-lenovo-thinkpad-e570](https://askubuntu.com/questions/990378/wifi-not-working-on-lenovo-thinkpad-e570)

---

### Post by gusmagna on 2018-01-24
> **Mike Silberg said:**
> Solution of installing driver **rtl8821ce** from Endlessm repo worked for me too on my Thinkpad E470 and now WiFi just works.

However  I'm still having problems with Bluetooth, it simply doesn't start so I  can't see other BT devices.

It seems to me that a new upstream driver still doesn't support it. Isn't it that, am I missing something?

Hi, 
I bought a Lenovo Thinkpad E470 for a couple of months and my wifi did not work either. I have followed the guide in the thread:

export TopDir ...
make
sudo make install

but when i type the command

modprobe -a 8821ce 

I get the following error message:

"modprobe: ERROR: could not insert '8821ce': Required key not available

did modprobe work for you or how did you solve this key-problem?

Thanks in advance!
Best,
Gustaf

---

### Post by jeremy31 on 2018-01-24
You need to go into BIOS/UEFI settings and disable Secure Boot for third party modules to load

---

### Post by erickem on 2018-02-06
Its work, thanks praseodym;)

____________

my website: [thêu chân mày Ng&#7885;c Dung]("https://ngocdung.net/phun-theu")

---

### Post by chris-dungeonmaster on 2018-02-21
Doesn't work, make says linux/sched/signa.h doesn't exist

---

### Post by ajesteves on 2018-04-17
This solution works with kernel 4.15!
I've tried with 4.13 and failed to compile, throwing time_setup error!
thanks,

---

### Post by praseodym on 2018-04-19
New github version available:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms git
git clone git://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh
```

---

