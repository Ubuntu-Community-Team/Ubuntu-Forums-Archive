---
title: "Wifi usb dongle connection"
date: 2012-08-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by GreatDanton on 2012-08-07
Hi, 
on my desktop computer I am using Wifi dongle, and now I noticed that after the computer boots I am not able to connect to Internet. If unplug my Wifi dongle and plug it again internet is working. Wifi dongle is fully compatible with Linux (Linksys WUSB54GC). Does anybody has the same problem?

I never had such issue in 12.04.

Regards.

---

### Post by wildmanne39 on 2012-08-14
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by GreatDanton on 2012-08-14
Here is the output:

Thanks.

---

### Post by GreatDanton on 2012-08-14
modinfo:
```
filename:       /lib/modules/3.5.0-9-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C12322429087802C0A4E76D
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.5.0-9-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```

Thanks.

---

### Post by GreatDanton on 2012-08-14
The latest netinfo

---

### Post by wildmanne39 on 2012-08-14
Hi, please do:
```
echo "options rt73usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt73usb.conf
sudo modprobe -rfv rt73usb
sudo modprobe -v rt73usb
```
Then do:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit, close and reboot.

Watch for errors on the first command and copy and paste for accuracy.
Thanks

---

### Post by GreatDanton on 2012-08-14
echo "options rt73usb nohwcrypt=1" | sudo tee /etc/modprobe.d/rt73usb.conf:

```
options rt73usb nohwcrypt=1
```

 sudo modprobe -rfv rt73usb:
```
rmmod /lib/modules/3.5.0-9-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
rmmod /lib/modules/3.5.0-9-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
rmmod /lib/modules/3.5.0-9-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
rmmod /lib/modules/3.5.0-9-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-9-generic/kernel/net/wireless/cfg80211.ko

```


 sudo modprobe -v rt73usb
```

insmod /lib/modules/3.5.0-9-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-9-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-9-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.5.0-9-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko 
insmod /lib/modules/3.5.0-9-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko nohwcrypt=1

```

 gksudo gedit /etc/pm/power.d/wireless

---

### Post by wildmanne39 on 2012-08-14
Please post the contents of:
```
 gksudo gedit /etc/pm/power.d/wireless
```
did it work?
Thanks

---

### Post by GreatDanton on 2012-08-14
Thank you. Yes it's working. No problems so far.

Regards.

---

### Post by wildmanne39 on 2012-08-14
Your welcome!
Enjoy

---

