---
title: "D-link DWA-131 (rtl8192cu driver) wifi trouble on Beaglebone Black rev. C"
date: 2017-10-08
forum: Ubuntu/Debian BASED
---

### Post by h-soderholtz on 2017-10-08
Hi!

I followed the advice of praseodym (post #4) in [this thread]("https://ubuntuforums.org/showthread.php?t=2352681") in an attempt to solve pretty much the same symptoms  which have been put forward in this thread, however my setup is probably quite different. My system is a Beaglebone Black running a dist of Ubuntu called [Umikaze (2.1.1)]("http://wiki.thing-printer.com/index.php?title=Umikaze#Umikaze_2.1.1") by thing-printer. (The system is the brains of a 3D-printer).

So, following that thread I had some trouble with some of the initial commands to get my system up-to-date, so I skipped the linux headers and git, as they weren't downloading. (could this be my problem?)

DKMS was downloaded, built and installed without any hick-ups.

However things aren't looking quite as good for me as they did for that OP.

I get a good downlink with 2.5Mbps down, but pretty much no bandwidth at all (SSH session times out) on the uplink. The wifi dongle connected to my AP without any issues after installing the Umikaze Ubuntu dist.

I have also blacklisted the rtl8192cu driver.

Here is my pastebin from the wireless script BEFORE installing the 8192cu driver: [http://paste.ubuntu.com/25694442/](http://paste.ubuntu.com/25694442/)

Here is my pastebin from the wireless script AFTER installing the 8192cu driver: [http://paste.ubuntu.com/25694645/](http://paste.ubuntu.com/25694645/)

Any help on resolving this would be very much appreciated!

//h-soderholtz

---

### Post by jeremy31 on 2017-10-08
*Thread moved to **Ubuntu/Debian BASED**.*

Try ```
echo "options 8192cu rtw_power_mgnt=0" | sudo tee /etc/modprobe.d/8192cu.conf
```
```
sudo modprobe -r 8192cu
```
```
sudo modprobe 8192cu
```

---

### Post by h-soderholtz on 2017-10-08
That actually seems to have my connection running much MUCH better. Thank you!

One thing I noticed after following the instructions in the aforementioned thread and running the wireless script, is that my link speed is now at 16mbit/s for all available connections except one:

```


[COLOR=#000000]SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
[/COLOR]Airport Extreme      <MAC 'Airport Extreme' [AC1]>  Infra  1     2412 MHz  16 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 
Jonsson              <MAC 'Jonsson' [AC2]>  Infra  12    2467 MHz  16 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
NETGEAR08            <MAC 'NETGEAR08' [AC3]>  Infra  1     2412 MHz  16 Mbit/s  49      &#9602;&#9604;__  WPA2       no        
Moni                 <MAC 'Moni' [AC4]>  Infra  1     2412 MHz  44 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2  no        
4G-Mobile-WiFi-F943  <MAC '4G-Mobile-WiFi-F943' [AN5]>  Infra  1     2412 MHz  8 Mbit/s   30      &#9602;___  WPA1 WPA2  no        
ASUS_EL51            <MAC 'ASUS_EL51' [AC5]>  Infra  1     2412 MHz  44 Mbit/s  15      &#9602;___  WPA2       no         
deathstar            <MAC 'deathstar' [AN7]>  Infra  6     2437 MHz  16 Mbit/s  15      &#9602;___  WPA2       no 
```([Here's a paste ]("http://paste.ubuntu.com/25702170/")of my latest script run after disabling power management)


Since I only got around 2.5MB/s down, and now seems I could get about the same up with your tip, I'm guessing it's running in 802.11g mode?

Any tips to bump me back up to N-standard?



Thanks again!

---

### Post by jeremy31 on 2017-10-08
Right now according to the script results there are 4 AP's on channel 1,  I would move away from channel 1 and I think the AP "Moni" has TKIP encryption which can cause problems with transfer speed and connection issues.  See this post by chili555 with his tips [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
He does post this info a lot and it does make a difference

---

### Post by h-soderholtz on 2017-10-08
Switched over to channel 6, and gained some signal strength (maximum now), but I remain on 16Mbit/s according to the Network Manager info, while in the iwconfig it does actually state 144.4Mbit/s, a download test using [http://speedtest.tele2.net/](http://speedtest.tele2.net/) gives me 2-3MB/s, which indicates the lower. The windows laptop I'm posting from shows similar performance though. (My ISP cap is 100Mbps DL)

Here's another [paste]("http://paste.ubuntu.com/25702459/") of the script.

Oh, and setting the country "permanently" didn't persist after a reboot as per chili555's tips. The REGDOMAIN=SE is set in the file, but [COLOR=#000000][FONT=&amp]sudo iw reg get doesn't show a country code unless i issue the iw reg set command.

//Henrik[/FONT][/COLOR]

---

### Post by jeremy31 on 2017-10-08
I only have one more idea, and that involves changing the SSID of your AP to remove the space, I think it is Airport Extreme, try making it Airport-Extreme
I am not sure why Praseodym chose that github when I normally see [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes) being used

---

### Post by chili555 on 2017-10-08
I'd suggest trying blacklisting 8192cu and* remove* the blacklist for rtl8xxxu and see if connectivity improves at all.

---

### Post by h-soderholtz on 2017-10-10
I tried this, and also turned power management off for the rtl8xxxu driver. However this resulted in my wifi dongle not showing up at all, and nothing showing up in lsmod.

I probably did something wrong. Some commands to go along with your tip would be much appreciated!

---

### Post by praseodym on 2017-10-10
Ok, so revert the last changes again. Try deactivating IPv6 in your networkmanager settings ("Ignore").

Other hint: Revert the changes in the interfaces file:
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
and reboot

---

### Post by chili555 on 2017-10-10
> **h-soderholtz said:**
> I tried this, and also turned power management off for the rtl8xxxu driver. However this resulted in my wifi dongle not showing up at all, and nothing showing up in lsmod.

I probably did something wrong. Some commands to go along with your tip would be much appreciated!Here is your last reported blacklist file; of course, we don't know what has happened since:
```
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rtl8192cu
blacklist rtl8xxxu

```Edit the file thus:```
sudo nano /etc/modprobe.d/blacklist.conf
```Change the last lines to read:```
<don't change any of the preceding>
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rtl8192cu
[COLOR="#FF0000"]#[/COLOR]blacklist rtl8xxxu
[COLOR="#FF0000"]blacklist 8192cu[/COLOR]
```Proofread carefully, save and close the text editor.> also turned power management off for the rtl8xxxu driver. How, exactly? We may need to revert that.

Reboot.

Did the module load?```
lsmod | grep rtl
```Any improvement?

---

