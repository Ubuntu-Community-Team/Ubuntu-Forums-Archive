---
title: "WNA 1100 netgear wireless adapter monitor and injection mode"
date: 2011-03-02
forum: Security
---

### Post by d3nn on 2011-03-02
I want to do some pen-testing using aircrack-ng on my local network and currently the only wireless adapter I have is the WNA 1100 netgear adapter. I am using the ath9k_htc driver. Thanks ahead for any advice :)

---

### Post by cariboo on 2011-03-03
According to [this]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers"), your device should be supported.

---

### Post by vleonbonnet on 2011-03-08
I tried to test some aircrack with my WNA1100 (ath9k_htc driver) also.
* First I try a connection with a bad password on the AP to match the channel of my wifi card the one of the AP: channel 6 (couldn't change it using airmon-ng).
* to be sure that the system don't mess with my card:
```
service network-manager stop
killall dhclient
killall wpa_supplicant
```
* I check with iwconfig that my card is on Frequency 2.437Ghz (channel 6)
* I start my interface into monitor mode:
```
airmon-ng start wlan1 6
```
* I start monitoring with airodump:
```
airodump-ng -c 6 --bssid 42:42:42:42:42:42 -w output mon0
```

Airodump displays:
```
CH 6 ][ Elapsed 24 s ][ date ][ fixed channel mon0: -1
```
So apparently there is an issue with the channel here... :confused:

* I try injection test:
```
aireplay-ng -9 -e APname -a 42:42:42:42:42:42 mon0
```
It displays:
```
mon0 is on channel -1, but the PA uses channel 6
```
Again this issue with mon0 not on the good channel... :confused:

* I try the injection test with wlan1:

```
aireplay-ng -9 -e APname -a 42:42:42:42:42:42 wlan1
```
Airodump display a lot of stuff, and it's working:
```
Injection is working!
Found 1 AP
```

* I fake authentication:
```
aireplay-ng -1 0 -e local -a 42:42:42:42:42:42 -h 24:24:24:24:24:24 wlan1
```

Airodump freezes while aireplay fail:
```
Sending Authentication Request (Open System)
Attack was unsuccessful.
```

After that every root command or sudo attempts freeze.
I don't know what I'm doing wrong, but this is most probably an issue with the driver.
Please let me know if somebody already succeed using WNA 1100 with aircrack.

---

### Post by vleonbonnet on 2011-03-09
Finally got it working!


If somebody have the same issue as me (negative channel on ar9271 [http://www.wikidevi.com/wiki/Netgear_WNA1100](http://www.wikidevi.com/wiki/Netgear_WNA1100) )
follow this:
download daily build version of compat-wireless: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
download also those two patches:
[http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)
[http://patches.aircrack-ng.org/mac80211_2.6.32.2-wl_frag+ack_radiotap.patch](http://patches.aircrack-ng.org/mac80211_2.6.32.2-wl_frag+ack_radiotap.patch)

```

wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
wget http://patches.aircrack-ng.org/mac80211_2.6.32.2-wl_frag+ack_radiotap.patch
tar -xf compat-wireless-2.6.tar.bz2
cp channel-negative-one-maxim.patch compat-wireless-2011-03-08/
cp mac80211_2.6.32.2-wl_frag+ack_radiotap.patch compat-wireless-2011-03-08/
cd compat-wireless-2011-03-08
patch -p1 < channel-negative-one-maxim.patch
patch -p1 < mac80211_2.6.32.2-wl_frag+ack_radiotap.patch
make
make install
make unload
modprobe ath9k_htc

```

The second patch will fail, try to fix it by hand, it's not very hard (goto the line, add manually the line in the .c)

lots of thanks to this page:
[http://forum.aircrack-ng.org/index.php?action=printpage;topic=8321.0](http://forum.aircrack-ng.org/index.php?action=printpage;topic=8321.0)


follow this tutorial:
[http://www.aircrack-ng.org/doku.php?id=simple_wep_crack&DokuWiki=39a652c8ce393263122cd2f0040045da](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack&DokuWiki=39a652c8ce393263122cd2f0040045da)

:popcorn:

---

### Post by betanman on 2011-05-13
> **vleonbonnet said:**
> Finally got it working!


If somebody have the same issue as me (negative channel on ar9271 [http://www.wikidevi.com/wiki/Netgear_WNA1100](http://www.wikidevi.com/wiki/Netgear_WNA1100) )
follow this:
download daily build version of compat-wireless: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
download also those two patches:
[http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)
[http://patches.aircrack-ng.org/mac80211_2.6.32.2-wl_frag+ack_radiotap.patch](http://patches.aircrack-ng.org/mac80211_2.6.32.2-wl_frag+ack_radiotap.patch)

```

wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
wget http://patches.aircrack-ng.org/mac80211_2.6.32.2-wl_frag+ack_radiotap.patch
tar -xf compat-wireless-2.6.tar.bz2
cp channel-negative-one-maxim.patch compat-wireless-2011-03-08/
cp mac80211_2.6.32.2-wl_frag+ack_radiotap.patch compat-wireless-2011-03-08/
cd compat-wireless-2011-03-08
patch -p1 < channel-negative-one-maxim.patch
patch -p1 < mac80211_2.6.32.2-wl_frag+ack_radiotap.patch
make
make install
make unload
modprobe ath9k_htc

```

The second patch will fail, try to fix it by hand, it's not very hard (goto the line, add manually the line in the .c)

lots of thanks to this page:
[http://forum.aircrack-ng.org/index.php?action=printpage;topic=8321.0](http://forum.aircrack-ng.org/index.php?action=printpage;topic=8321.0)


follow this tutorial:
[http://www.aircrack-ng.org/doku.php?id=simple_wep_crack&DokuWiki=39a652c8ce393263122cd2f0040045da](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack&DokuWiki=39a652c8ce393263122cd2f0040045da)

:popcorn:

hi, in Brief I have an D-Link DWA 126 which I think has the same chipset (AR9271), and I'm under Backtrack 4 r2 and 5.
my problem is that I can't get operate the packet injection.
I saw in your post that you used the patch (mac80211_2.6.32.2-wl_frag ack_radiotap.patch)
I got an error during the patching as you said and I don't know what to modify in the patch to make it work, here is the log of what I did in Backtrack 4 r2 live dvd
> root@bt:~# tar -xjf compat-wireless-2.6.39-rc6-1-sp.tar.bz2
root@bt:~# cd compat-wireless*
root@bt:~/compat-wireless-2.6.39-rc6-1-sp# sudo patch -Np1 -i patches/channel-negative-one-maxim.patch
patching file net/wireless/chan.c
Hunk #1 succeeded at 82 (offset 33 lines).
Hunk #2 succeeded at 134 (offset 55 lines).
root@bt:~/compat-wireless-2.6.39-rc6-1-sp# sudo patch -Np1 -i patches/mac80211_2.6.32.2-wl_frag+ack_radiotap.patch
patching file include/net/ieee80211_radiotap.h
Hunk #1 succeeded at 251 with fuzz 2 (offset 11 lines).
patching file net/mac80211/tx.c
Hunk #1 succeeded at 779 (offset 101 lines).
Hunk #2 succeeded at 1094 with fuzz 1 (offset 116 lines).
Hunk #3 FAILED at 1151.
Hunk #4 succeeded at 1258 with fuzz 1 (offset 158 lines).
1 out of 4 hunks FAILED -- saving rejects to file net/mac80211/tx.c.rej
root@bt:~/compat-wireless-2.6.39-rc6-1-sp# ./scripts/driver-select ath9k_htc
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backing up makefile: drivers/net/wireless/ath/Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
Backing up makefile: drivers/net/Makefile.bk
Backing up makefile: drivers/ssb/Makefile.bk
Backing up makefile: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk
root@bt:~/compat-wireless-2.6.39-rc6-1-sp# sudo make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.35.8/build M=/root/compat-wireless-2.6.39-rc6-1-sp modules
make[1]: Entering directory `/usr/src/linux-source-2.6.35.8'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.35.8/Module.symvers
           is missing; modules will have no dependencies and modversions.
.........
.........
root@bt:~/compat-wireless-2.6.39-rc6-1-sp# sudo make unload
Stoping bluetooth service..
Stopping bluetooth: bluetoothd.
* bluetooth is not running.
Unloading ath9k...
Unloading ath9k_htc...
Unloading rfcomm...
root@bt:~/compat-wireless-2.6.39-rc6-1-sp# modprobe -v ath9k_htc
insmod /lib/modules/2.6.35.8/kernel/drivers/leds/led-class.ko
insmod /lib/modules/2.6.35.8/updates/compat/compat.ko
insmod /lib/modules/2.6.35.8/kernel/net/rfkill/rfkill.ko
insmod /lib/modules/2.6.35.8/updates/net/wireless/cfg80211.ko
insmod /lib/modules/2.6.35.8/updates/drivers/net/wireless/ath/ath.ko
insmod /lib/modules/2.6.35.8/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
insmod /lib/modules/2.6.35.8/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
insmod /lib/modules/2.6.35.8/updates/net/mac80211/mac80211.ko
insmod /lib/modules/2.6.35.8/updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko thanks in advance

---

### Post by Theisonews on 2011-08-23
i had my netgear wna1100 working with bt 5  but now i upgrade to bt5 r1 and now injection mode does not work.  so i try to run compizz again and when i type make  i get this

```
oot@bt:~/Desktop/net/compat-wireless-3.0-2# make
/root/Desktop/net/compat-wireless-3.0-2/config.mk:212: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
make -C /lib/modules/2.6.39.4/build M=/root/Desktop/net/compat-wireless-3.0-2 modules
make: *** /lib/modules/2.6.39.4/build: No such file or directory.  Stop.
make: *** [modules] Error 2


```

---

### Post by vleonbonnet on 2011-08-23
I'm not quite an expert, but maybe you didn't installed your kernel headers.

---

### Post by uRock on 2011-08-23
We do not offer support for using Aircrack.

---

