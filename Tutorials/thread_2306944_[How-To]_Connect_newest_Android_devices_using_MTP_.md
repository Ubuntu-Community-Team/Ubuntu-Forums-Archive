---
title: "[How-To] Connect newest Android devices using MTP in KUbuntu 12.04 LTS"
date: 2015-12-20
forum: Tutorials
---

### Post by peter-ludwig on 2015-12-20
After struggeling quite a time to get my China mobile working I want to share my experiences. This is according to my 12.04 installation. I am not sure if you will need all or less files to get it done. I for one needed all these steps and took me days to find out.


1. The ***kio-mtp*** file was missing:

```
sudo apt-get install kio-mtp
```

2. Now we need some ***more essential files***:

```
sudo apt-get install libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9 mtpfs
```

3. ***Update of MTP Pakage*** (my device was not working with older ones)

[http://sourceforge.net/projects/libmtp/files/libmtp/1.1.9/](http://sourceforge.net/projects/libmtp/files/libmtp/1.1.9/)

Download this file, Extract, 

Change into this folder. Inside you need to run: 

```
./configure
```
then
```
make
```

```
sudo checkinstall
```

If you have not done already please install "checkinstall" -  so it is easier to remove these packages later on. 

You will get a ***libmtp_1.1.9-1_amd64.deb*** file which you should install by klicking on it. 


4. We have to ***add udev rules***:

Added rule for device in "*/lib/udev/rules.d/69-libmtp.rules*".:

```
# Xiaomi Redmi Note 2 (MTP)
#ATTR{idVendor}=="**2717**",  ATTR{idProduct}=="**ff18**", SYMLINK+="libmtp-%k", MODE="660",  GROUP="audio", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
```

```
# Xiaomi Redmi Note 2 (MTP+ADB)
ATTR{idVendor}=="**2717**",  ATTR{idProduct}=="**ff48**", SYMLINK+="libmtp-%k", MODE="660",  GROUP="audio", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
```



The numbers ***2717*** und ***ff48*** / ***ff18*** you will find out by using "lsusb" or from "sudo mtp-detect | grep idVendor" AND "mtp-detect | grep idProduct")

Fill these numbers in according to your mobile!!!


```
sudo service udev restart
```

No reboot needed.


_Some general things:_

a) take a good USB cable. Not the cheapest one
b) insert your mobile into a direct USB port - no hub in between. (Energy problem)
c) you have to switch your mobile into the "mtp" mode. (It might be in PTP mode!!) 


Good luck!

---

