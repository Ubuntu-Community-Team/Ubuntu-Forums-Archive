---
title: "Trusty Tahr image with Kernel 4.2."
date: 2015-11-03
forum: Ubuntu Development Version
---

### Post by kagashe on 2015-11-03
I downloaded trusty-desktop-amd64 from [Daily/live]("http://cdimage.ubuntu.com/trusty/daily-live/current/") and found that it has Kernel 3.19.

I want to test the trusty-desktop ISO when the Kernel gets updated to 4.2 particularly for Bluetooth and would like to know approx when this is going to happen.

Kamalakar

---

### Post by Bucky Ball on 2015-11-03
Unaware when or if Trusty is ever going to be upgraded to 4.2, but you can install that kernel in 14.04 now if you want. Starting from the third thread down [here]("https://duckduckgo.com/?q=install+4.2+kernel+14.04") you will see some guides on how to do that.

---

### Post by howefield on 2015-11-03
> **kagashe said:**
> I want to test the trusty-desktop ISO when the Kernel gets updated to 4.2 particularly for Bluetooth and would like to know approx when this is going to happen.

Kamalakar

[Feb 2016]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

---

### Post by Bucky Ball on 2015-11-03
> **howefield said:**
> [Feb 2016]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

Good to know. Tnx howefield. :)

---

### Post by kagashe on 2015-11-03
> **howefield said:**
> [Feb 2016]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")I think that is the month when Ubuntu 14.04.4 gets released but I am interested to download and test the Daily image ISO when it gets Kernel 4.2 anyway it may not happen before Jan 2016. Thank you.

Kamalakar

---

### Post by howefield on 2015-11-03
Guess you could keep an eye on the manifest file for the image you are interested in or possibly ask in #ubuntu-kernel.

---

### Post by kagashe on 2015-11-03
> **howefield said:**
> Guess you could keep an eye on the manifest file for the image you are interested in or possibly ask in #ubuntu-kernel.Thanks will keep an eye on [manifest]("http://cdimage.ubuntu.com/trusty/daily-live/current/trusty-desktop-amd64.manifest")

Kamalakar

---

### Post by grahammechanical on 2015-11-03
It is usually the pattern for the point release to get the hardware enablement stack of the Ubuntu release that preceded it. So, 14.04.4 will get the kernels that came with 15.10.

But although the point release brings in desktop upgrades it does not automatically bring in the hardware enablement stack

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards

---

### Post by mc4man on 2015-11-04
The 4.2 (lts-wily) packages will show up in trusty -proposed first before being in any image. Some early test packages are around but aren't really meant for users so no sense linking. (though you can easily goggle or whatever to see how progressed, ect..

---

### Post by fjgaude on 2015-11-04
I installed 4.2 in 14.04.3 without any apparent issues... I have many of my normal files loaded but haven't gotten to VirtualBox yet... will tomorrow... so much to do and so little time!

---

### Post by kagashe on 2016-01-31
Downloaded the Daily Live today and found Linux Kernel 4.2.0-27

My purpose is to test Bluettooth for my Lenovo Laptop for which Kernel 4.2 is required. At present Bluetooth is disabled when I boot with Current Live image.
```
$ dmesg | grep -i bluetooth
[   11.359168] usb 4-1.3: Product: Bluetooth Radio 
[   59.941556] Bluetooth: Core ver 2.20
[   59.941641] Bluetooth: HCI device and connection manager initialized
[   59.941653] Bluetooth: HCI socket layer initialized
[   59.941660] Bluetooth: L2CAP socket layer initialized
[   59.941674] Bluetooth: SCO socket layer initialized
[   59.994710] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   59.994719] Bluetooth: BNEP filters: protocol multicast
[   59.994732] Bluetooth: BNEP socket layer initialized
[   60.044432] Bluetooth: RFCOMM TTY layer initialized
[   60.044467] Bluetooth: RFCOMM socket layer initialized
[   60.044483] Bluetooth: RFCOMM ver 1.11
[   60.882083] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   60.882094] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   60.882986] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_fw.bin failed with error -2
[   60.882998] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_fw.bin
```

I checked /lib/firmware folder and could not find rtl_bt folder which is supposed to contain the required driver rtl8723b_fw.bin

Kamalakar

---

### Post by zika on 2016-01-31
```
:~$ locate rtl8723b
/lib/firmware/rtl_bt/rtl8723b_fw.bin
/lib/firmware/rtlwifi/rtl8723befw.bin
/lib/modules/4.4-0.dmz.4-liquorix-amd64/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4-0.dmz.4-liquorix-amd64/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-2-lowlatency/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-2-lowlatency/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.4.0-xanmod3/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.4.0-xanmod3/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/lib/modules/4.5.0-999-lowlatency/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/lib/modules/4.5.0-999-lowlatency/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
/usr/src/linux-headers-4.4-0.dmz.4-liquorix-amd64/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4-0.dmz.4-liquorix-amd64/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4-0.dmz.4-liquorix-amd64/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-2/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-2/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-2-lowlatency/include/config/rtl8723be.h
/usr/src/linux-headers-4.4.0-xanmod3/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.4.0-xanmod3/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.4.0-xanmod3/include/config/rtl8723be.h
/usr/src/linux-headers-4.5.0-999/drivers/net/wireless/realtek/rtlwifi/rtl8723be
/usr/src/linux-headers-4.5.0-999/drivers/net/wireless/realtek/rtlwifi/rtl8723be/Makefile
/usr/src/linux-headers-4.5.0-999-lowlatency/include/config/rtl8723be.h
``````
:~$ locate rtl_bt
/lib/firmware/rtl_bt
/lib/firmware/rtl_bt/rtl8192ee_fw.bin
/lib/firmware/rtl_bt/rtl8192eu_fw.bin
/lib/firmware/rtl_bt/rtl8723a_fw.bin
/lib/firmware/rtl_bt/rtl8723b_fw.bin
/lib/firmware/rtl_bt/rtl8761a_fw.bin
/lib/firmware/rtl_bt/rtl8812ae_fw.bin
/lib/firmware/rtl_bt/rtl8821a_fw.bin
``````
:~$ dpkg -l|grep firmware
ii  amd64-microcode                                       2.20141028.1                                              amd64        Processor microcode [COLOR=#CC0000]**firmware**[/COLOR] for AMD CPUs
ii  ipxe-qemu                                             1.0.0+git-20141004.86285d1-1ubuntu3                       all          PXE boot [COLOR=#CC0000]**firmware**[/COLOR] - ROM images for qemu
ii  linux-[COLOR=#CC0000]**firmware**[/COLOR]                                        1.155                                                     all          Firmware for Linux kernel drivers
ii  linux-[COLOR=#CC0000]**firmware**[/COLOR]-image-4.4.0-xanmod3                    1.160129                                                  amd64        Linux kernel [COLOR=#CC0000]**firmware**[/COLOR], version 4.4.0-xanmod3
```
And, finally:```
:~$ dpkg-deb  -c linux-firmware_1.155_all.deb |grep rtl
-rw-r--r-- root/root      2115 2016-01-06 17:25 ./usr/share/doc/linux-firmware/licenses/LICENCE.[COLOR=#CC0000]**rtl**[/COLOR]wifi_firmware.txt
drwxr-xr-x root/root         0 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_bt/
-rw-r--r-- root/root     45048 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_bt/[COLOR=#CC0000]**rtl**[/COLOR]8723b_fw.bin
-rw-r--r-- root/root     38764 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_bt/[COLOR=#CC0000]**rtl**[/COLOR]8192ee_fw.bin
-rw-r--r-- root/root     37904 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_bt/[COLOR=#CC0000]**rtl**[/COLOR]8192eu_fw.bin
-rw-r--r-- root/root     24548 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_bt/[COLOR=#CC0000]**rtl**[/COLOR]8723a_fw.bin
-rw-r--r-- root/root     37420 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_bt/[COLOR=#CC0000]**rtl**[/COLOR]8821a_fw.bin
-rw-r--r-- root/root     40520 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_bt/[COLOR=#CC0000]**rtl**[/COLOR]8812ae_fw.bin
-rw-r--r-- root/root     74488 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_bt/[COLOR=#CC0000]**rtl**[/COLOR]8761a_fw.bin
drwxr-xr-x root/root         0 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/
-rw-r--r-- root/root     22172 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8723aufw_A.bin
-rw-r--r-- root/root     16096 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8192cufw_B.bin
-rw-r--r-- root/root     19200 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8723aufw_B_NoBT.bin
-rw-r--r-- root/root     16332 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8192cfwU_B.bin
-rw-r--r-- root/root     16192 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8192cfw.bin
-rw-r--r-- root/root     28984 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8821aefw.bin
-rw-r--r-- root/root     19858 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8821aefw_wowlan.bin
-rw-r--r-- root/root     80208 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8192sefw.bin
-rw-r--r-- root/root     24118 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8723aufw_B.bin
-rw-r--r-- root/root     11216 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8188efw.bin
-rw-r--r-- root/root     13904 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8188eufw.bin
-rw-r--r-- root/root     22996 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8723fw_B.bin
-rw-r--r-- root/root     16116 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8192cufw_TMSC.bin
-rw-r--r-- root/root    122328 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8712u.bin
-rw-r--r-- root/root     30746 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8723befw.bin
-rw-r--r-- root/root     31376 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8192defw.bin
-rw-r--r-- root/root     16014 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8192cufw.bin
-rw-r--r-- root/root     16116 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8192cufw_A.bin
-rw-r--r-- root/root     11662 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8723fw.bin
-rw-r--r-- root/root     31818 2016-01-06 16:57 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8192eefw.bin
-rw-r--r-- root/root     14818 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]wifi/[COLOR=#CC0000]**rtl**[/COLOR]8192cfwU.bin
drwxr-xr-x root/root         0 2015-05-13 17:08 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/
-rw-r--r-- root/root       832 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168g-3.fw
-rw-r--r-- root/root      2076 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8105e-1.fw
-rw-r--r-- root/root       976 2015-05-13 17:08 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8107e-2.fw
-rw-r--r-- root/root      1856 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8106e-1.fw
-rw-r--r-- root/root      3920 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168e-2.fw
-rw-r--r-- root/root      3872 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168e-3.fw
-rw-r--r-- root/root       976 2015-05-13 17:08 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168h-2.fw
-rw-r--r-- root/root       832 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8106e-2.fw
-rw-r--r-- root/root      1824 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8402-1.fw
-rw-r--r-- root/root      4896 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168g-2.fw
-rw-r--r-- root/root      2112 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8411-1.fw
-rw-r--r-- root/root      5500 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168e-1.fw
-rw-r--r-- root/root       992 2015-05-13 17:08 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168h-1.fw
-rw-r--r-- root/root      1040 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8411-2.fw
-rw-r--r-- root/root      1232 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168f-2.fw
-rw-r--r-- root/root      1324 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168d-2.fw
-rw-r--r-- root/root      4304 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168g-1.fw
-rw-r--r-- root/root      1492 2014-11-24 16:42 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168d-1.fw
-rw-r--r-- root/root       992 2015-05-13 17:08 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8107e-1.fw
-rw-r--r-- root/root      3424 2014-12-01 16:16 ./lib/firmware/[COLOR=#CC0000]**rtl**[/COLOR]_nic/[COLOR=#CC0000]**rtl**[/COLOR]8168f-1.fw
```You do not even need to install any of these additional package(s)/kernel(s), simply steal appropriate files and put them in right places...
Disregard some additional hits in my searches on my machine since I did not want to obscure results by deleting some unncessary stuff. Conclusion of mine is that You're chassing wrong rabbit. It is not kernel that is to be blamed.. ;)

---

### Post by mc4man on 2016-01-31
> **kagashe said:**
> Downloaded the Daily Live today and found Linux Kernel 4.2.0-27

My purpose is to test Bluettooth for my Lenovo Laptop for which Kernel 4.2 is required. At present Bluetooth is disabled when I boot with Current Live image.
[
I checked /lib/firmware folder and could not find rtl_bt folder which is supposed to contain the required driver rtl8723b_fw.bin

Kamalakar

While 14.04.4 has wily kernel & mesa the linux-firmware package is what's currently in 14.04, here's the list - 
[http://packages.ubuntu.com/trusty-updates/linux-firmware/filelist](http://packages.ubuntu.com/trusty-updates/linux-firmware/filelist)

edit: if me i'd download & try installing this package, though only possibly useful for a 14.04.4 install - 
[http://packages.ubuntu.com/wily-updates/linux-firmware](http://packages.ubuntu.com/wily-updates/linux-firmware)

---

### Post by kagashe on 2016-02-03
> **mc4man said:**
> While 14.04.4 has wily kernel & mesa the linux-firmware package is what's currently in 14.04, here's the list - 
[http://packages.ubuntu.com/trusty-updates/linux-firmware/filelist](http://packages.ubuntu.com/trusty-updates/linux-firmware/filelist)

edit: if me i'd download & try installing this package, though only possibly useful for a 14.04.4 install - 
[http://packages.ubuntu.com/wily-updates/linux-firmware](http://packages.ubuntu.com/wily-updates/linux-firmware)I installed linux-firmware package from wily-updates but Bluetooth does not work.

```
$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out
```

```
$ dmesg | grep -i bluetooth
[   11.374801] usb 4-1.3: Product: Bluetooth Radio 
[   52.132104] Bluetooth: Core ver 2.20
[   52.132247] Bluetooth: HCI device and connection manager initialized
[   52.132258] Bluetooth: HCI socket layer initialized
[   52.132264] Bluetooth: L2CAP socket layer initialized
[   52.132279] Bluetooth: SCO socket layer initialized
[   52.189107] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   52.189115] Bluetooth: BNEP filters: protocol multicast
[   52.189126] Bluetooth: BNEP socket layer initialized
[   52.198515] Bluetooth: RFCOMM TTY layer initialized
[   52.198536] Bluetooth: RFCOMM socket layer initialized
[   52.198548] Bluetooth: RFCOMM ver 1.11
[   52.949377] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   52.949388] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   53.033361] Bluetooth: hci0: rom_version status=0 version=1
[  237.593564] Bluetooth: hci0 command 0x0c3a tx timeout
[  239.593739] Bluetooth: hci0 command 0x0c1a tx timeout
[  241.593835] Bluetooth: hci0 command 0x2008 tx timeout
[  283.533115] Bluetooth: hci0 command 0x0401 tx timeout
```

Kamalakar

---

### Post by VMC on 2016-02-03
I have in integrated "Nvidia GeForce 6150SE nForce 430" on my 2009 motherboard that has been fine up until Xenial. I suspected it was the newer kernel 4.2. Nvidia will not load on any Xenial iso's.

Thankfully, Trusty has loaded nvidia fine so far, but if my suspicion is correct, then the newer Trusty with kernel 4.2 will not work.

Thankfully for the first time, nouveau works perfectly on Xenial. Odd, but nouveau freezes every time on all ubuntu versions from 10.4 on, until Xenial.

I'm going to try the lasted Trusty 14.04.4 and see what happens.

---

