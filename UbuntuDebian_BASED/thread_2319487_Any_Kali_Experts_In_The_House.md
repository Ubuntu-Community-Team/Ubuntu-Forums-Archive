---
title: "Any Kali Experts In The House?"
date: 2016-04-04
forum: Ubuntu/Debian BASED
---

### Post by utnubu4 on 2016-04-04
Hey guys,

I have an issue with Kali and can not get any decent information from the Kali forum... there is a great lack of help over at that place. When i have posted in this forum people have been very keen to help and solve any issue!

The past few days i have been attempting to get my WIFI to work on Kali, I have tried everything that i can find on the Internet with no luck! I feel that there may be some expert knowledge lurking about here at the ubuntu forum.

My network card is BCM43142. I have added the correct repositories to my sources.list and even changed the websites to mirror sites as i read this solves the issue. Here is what my repositories in the sources.list look like at the moment.

```
deb cdrom:[Debian GNU/Linux 2016.1 _Kali-rolling_ - Official Snapshot amd64 LIVE/INSTALL Binary 20160120-18:14]/ kali-rolling contrib main non-free
deb cdrom:[Debian GNU/Linux 2016.1 _Kali-rolling_ - Official Snapshot amd64 LIVE/INSTALL Binary 20160120-18:14]/ kali-rolling contrib main non-free
deb [http://de-rien.fr/kali/](http://de-rien.fr/kali/) kali main contrib non-free
deb [http://de-rien.fr/kali/](http://de-rien.fr/kali/) kali/updates main contrib non-free
deb [http://de-rien.fr/kali/](http://de-rien.fr/kali/) kali-rolling main non-free contrib
```

When i run "apt-get install -y linux-headers-$ 4.3.0-kali1-amd64" in the terminal this is the message i receive.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-latest-modules-4.3.0-kali1-amd64' for regex '4.3.0-kali1-amd64'
Note, selecting 'linux-image-4.3.0-kali1-amd64' for regex '4.3.0-kali1-amd64'
Note, selecting 'linux-modules-4.3.0-kali1-amd64' for regex '4.3.0-kali1-amd64'
Note, selecting 'linux-image-amd64' instead of 'linux-latest-modules-4.3.0-kali1-amd64'
Note, selecting 'linux-image-4.3.0-kali1-amd64' instead of 'linux-modules-4.3.0-kali1-amd64'
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (contrib/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (main/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (non-free/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Packages (non-free/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (non-free/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
W: Target Translations (non-free/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:3 and /etc/apt/sources.list:5
E: Unable to locate package linux-headers-$
E: Couldn't find any package by regex 'linux-headers-$'
```

I have tried everything to resolve this issue with zero luck, if anyone can provide me with any advice or guidance it would be greatly appreciated!

---

### Post by coffeecat on 2016-04-04
Support, not Cafe.

*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by QDR06VV9 on 2016-04-04
I have a couple of friends that use Kali... here is the suggested method for that card.
Installing the drivers
```
$ wget https://gist.githubusercontent.com/chokepoint/11305606/raw/52109f648c2ad5ec6a65bf8eee78fbda15fa1cfb/bcm43142_drivers.sh
$ chmod +x bcm43142_drivers.sh
$ sudo ./bcm43142_drivers.sh
```
The Script content is below
```
#!/bin/bash
# chmod +x broadcom_drivers.sh
# ./broadcom_drivers.sh

mkdir broadcom 
cd broadcom
apt-get install linux-headers-`uname -r` build-essential -y

if [ `uname -m` == "i686" ] ; then
 wget http://www.broadcom.com/docs/linux_sta/hybrid-v35-nodebug-pcoem-6_30_223_141.tar.gz
else
 wget http://www.broadcom.com/docs/linux_sta/hybrid-v35_64-nodebug-pcoem-6_30_223_141.tar.gz
fi
tar -xvf hybrid-v35*
wget http://www.mindwerks.net/wp-content/uploads/2013/10/wl_3.10.patch
patch -p2 < wl_3.10.patch
make
cp wl.ko /lib/modules/`uname -r`/kernel/net/wireless/
depmod
rmmod bcma
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
modprobe wl

```
Hope this is helpful for you..

---

### Post by utnubu4 on 2016-04-04
Thank you for the reply runrickus :)

This is what i get when i run the first few commands.


```
root@cryptic:~# wget https://gist.githubusercontent.com/chokepoint/11305606/raw/52109f648c2ad5ec6a65bf8eee78fbda15fa1cfb/bcm43142_drivers.sh
--2016-04-04 23:44:47--  https://gist.githubusercontent.com/chokepoint/11305606/raw/52109f648c2ad5ec6a65bf8eee78fbda15fa1cfb/bcm43142_drivers.sh
Resolving gist.githubusercontent.com (gist.githubusercontent.com)... 185.31.19.133, 64:ff9b::b91f:1385
Connecting to gist.githubusercontent.com (gist.githubusercontent.com)|185.31.19.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646 [text/plain]
Saving to: ‘bcm43142_drivers.sh’

bcm43142_drivers.sh 100%[===================>]     646  --.-KB/s    in 0s      

2016-04-04 23:44:50 (2.41 MB/s) - ‘bcm43142_drivers.sh’ saved [646/646]

root@cryptic:~# chmod +x bcm43142_drivers.sh
root@cryptic:~# sudo ./bcm43142_drivers.sh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-4.3.0-kali1-amd64
E: Couldn't find any package by glob 'linux-headers-4.3.0-kali1-amd64'
E: Couldn't find any package by regex 'linux-headers-4.3.0-kali1-amd64'
--2016-04-04 23:46:25--  http://www.broadcom.com/docs/linux_sta/hybrid-v35_64-nodebug-pcoem-6_30_223_141.tar.gz
Resolving www.broadcom.com (www.broadcom.com)... 209.132.249.240, 64:ff9b::d184:f9f0
Connecting to www.broadcom.com (www.broadcom.com)|209.132.249.240|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1786627 (1.7M) [application/octet-stream]
Saving to: ‘hybrid-v35_64-nodebug-pcoem-6_30_223_141.tar.gz’

hybrid-v35_64-nodeb 100%[===================>]   1.70M  19.7KB/s    in 28s     

2016-04-04 23:46:56 (62.1 KB/s) - ‘hybrid-v35_64-nodebug-pcoem-6_30_223_141.tar.gz’ saved [1786627/1786627]

Makefile
lib/
lib/wlc_hybrid.o_shipped
lib/LICENSE.txt
src/
src/shared/
src/shared/linux_osl.c
src/shared/bcmwifi/
src/shared/bcmwifi/include/
src/shared/bcmwifi/include/bcmwifi_channels.h
src/shared/bcmwifi/include/bcmwifi_rates.h
src/include/
src/include/typedefs.h
src/include/bcmdefs.h
src/include/bcmendian.h
src/include/linuxver.h
src/include/wlioctl.h
src/include/bcmutils.h
src/include/osl.h
src/include/linux_osl.h
src/include/packed_section_end.h
src/include/packed_section_start.h
src/include/pcicfg.h
src/include/epivers.h
src/common/
src/common/include/
src/common/include/proto/
src/common/include/proto/ethernet.h
src/common/include/proto/bcmeth.h
src/common/include/proto/bcmip.h
src/common/include/proto/bcmevent.h
src/common/include/proto/ieee80211_radiotap.h
src/common/include/proto/802.11.h
src/common/include/proto/802.1d.h
src/common/include/proto/wpa.h
src/wl/
src/wl/sys/
src/wl/sys/wl_cfg80211_hybrid.c
src/wl/sys/wl_export.h
src/wl/sys/wl_dbg.h
src/wl/sys/wlc_key.h
src/wl/sys/wlc_ethereal.h
src/wl/sys/wl_linux.c
src/wl/sys/wl_linux.h
src/wl/sys/wl_cfg80211_hybrid.h
src/wl/sys/wl_iw.c
src/wl/sys/wl_iw.h
src/wl/sys/wlc_types.h
src/wl/sys/wlc_pub.h
src/wl/sys/wlc_utils.h
--2016-04-04 23:46:56--  http://www.mindwerks.net/wp-content/uploads/2013/10/wl_3.10.patch
Resolving www.mindwerks.net (www.mindwerks.net)... failed: Name or service not known.
wget: unable to resolve host address ‘www.mindwerks.net’
./bcm43142_drivers.sh: line 16: wl_3.10.patch: No such file or directory
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: *** /lib/modules/4.3.0-kali1-amd64/build: No such file or directory.  Stop.
Makefile:136: recipe for target 'all' failed
make: *** [all] Error 2
cp: cannot stat ‘wl.ko’: No such file or directory
modprobe: FATAL: Module wl not found.
root@cryptic:~# 

```

This is what i got when i ran the apt-get install linux-headers- 4.3.0-kali1-amd64 build-essential -y

```
root@cryptic:~# uname -r
4.3.0-kali1-amd64
root@cryptic:~# apt-get install linux-headers- 4.3.0-kali1-amd64 build-essential -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-headers' is not installed, so not removed
Note, selecting 'linux-latest-modules-4.3.0-kali1-amd64' for regex '4.3.0-kali1-amd64'
Note, selecting 'linux-image-4.3.0-kali1-amd64' for regex '4.3.0-kali1-amd64'
Note, selecting 'linux-modules-4.3.0-kali1-amd64' for regex '4.3.0-kali1-amd64'
Note, selecting 'linux-image-amd64' instead of 'linux-latest-modules-4.3.0-kali1-amd64'
Note, selecting 'linux-image-4.3.0-kali1-amd64' instead of 'linux-modules-4.3.0-kali1-amd64'
build-essential is already the newest version (11.7).
build-essential set to manually installed.
linux-image-amd64 is already the newest version (4.3+70+kali1).
linux-image-4.3.0-kali1-amd64 is already the newest version (4.3.3-5kali4).
linux-image-4.3.0-kali1-amd64 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


This is what i get when i run chmod +x broadcom_drivers.sh

```
root@cryptic:~# chmod +x broadcom_drivers.sh
chmod: cannot access ‘broadcom_drivers.sh’: No such file or directory
```

To be completely honest with you i am not quite sure what i am supposed to be doing with the script provided? is it a list of commands to run?

Thank you very much for this help :)

---

### Post by QDR06VV9 on 2016-04-05
The script was provided as a courtesy to show the code only.
the command "$ wget https://gist.githubusercontent.com/chokepoint/11305606/raw/52109f648c2ad5ec6a65bf8eee78fbda15fa1cfb/bcm43142_drivers.sh"
should have executed the script I showed.
I myself don't run Kali but it looks to me that you don't have a necessary repo enabled.
> The Kali Rolling Repository

kali-rolling is our current active repository since the release of Kali 2016.1. Kali Rolling users are expected to have the following entries in their sources.list:
deb [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free
# _**For source package access, uncomment the following line**_
# deb-src [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free

So this from their forum
> For all of you who did not succede with this driver.
1. Make sure that file: /etc/apt/sources.list contains following 4 lines:

deb-src [http://http.kali.org/kali](http://http.kali.org/kali) sana main non-free contrib
deb-src [http://security.kali.org/kali-security](http://security.kali.org/kali-security) sana/updates main contrib non-free
deb [http://http.kali.org/kali](http://http.kali.org/kali) sana main non-free contrib
deb [http://security.kali.org/kali-security](http://security.kali.org/kali-security) sana/updates main contrib non-free

2. After that normaly:,

apt-get update
apt-get dist-upgrade
apt-get install-y linux-headers-$(uname -r)

3.Then the big surprise (full graphical install):-) Install synaptic.

apt-get install synaptic -y

-Then just open synaptic (the new-installed program under Kali-linux) and type "bcm43142" and search.

-U'll see 3 different drivers.
broadcom-sta-common
broadcom-sta-dkms
broadcom-sta-source

-Mark for installation to broadcom-sta-dkms and install it.

-Reboot.


Source:[URL="http://docs.kali.org/general-use/kali-linux-sources-list-repositories"] [http://www.chokepoint.net/2014/04/installing-broadcom-bcm43142-drivers-on.html](http://www.chokepoint.net/2014/04/installing-broadcom-bcm43142-drivers-on.html)








[/URL]

---

### Post by utnubu4 on 2016-04-09
Thank you for the reply and help :)

I have solved the WIFI issue on kali a few days ago now. I referred to the broadcom website and solved the issue!

Thanks for the help anyway!

---

