---
title: "Prevent USB-N13 [Realtek RTL8192CU] From Going To Sleep"
date: 2016-12-11
forum: Ubuntu/Debian BASED
---

### Post by guimaster on 2016-12-11
Elementary OS 16.04

If when I boot my computer, I start and continually ping a website, such as Google.com, I will _never_ lose my connection. However, if I am not running a ping, and I stop my internet activity, I will often lose my connection. From there I need to disable and re-enable wireless networking, in order to get a connection again. It seems clear to me that the problem is a matter of Ubuntu putting the device to sleep when not in use, and not waking it up again when needed.

I found the following code on-line and I placed it in a file in /etc/modprobe.d:

```

# Disable power management in the 8192cu driver. This works around a bug in
# some hardware where the device never wakes back up.
# Credit goes to Saqib Razaq (https://github.com/s-razaq) for the fix.


# rtw_power_mgnt=0 disables power saving
# rtw_enusbss=0 disables USB autosuspend
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

```

The file name is: " 8192cu-disable-power-management.conf "

Unfortunately this has no effect, and it's probably because I don't really know what I'm doing, LoL.

Could anyone tell me what the file name should be, and what the proper code should be, in order to get this to work? From playing around I'm convinced that the file will be read automatically on boot. It seems just to be a matter of the code or filename being wrong (most likely the code.)

---

### Post by chili555 on 2016-12-11
Is your driver 8192cu or **rtl**8192cu??```
lsmod
```

---

### Post by guimaster on 2016-12-11
[FONT=arial]> **chili555 said:**
> Is your driver 8192cu or **rtl**8192cu??```
lsmod
```

rtl8192cu, probably. I tried renaming the file to " rtl[COLOR=#000000]8192cu-disable-power-management.conf ", previously, as well as editing " [/COLOR][COLOR=#000000]options 8192cu rtw_power_mgnt=0 rtw_enusbss=0 " to say the following: " [/COLOR][COLOR=#000000]options rtl8192cu rtw_power_mgnt=0 rtw_enusbss=0 ", but it did not help.
[/COLOR][COLOR=#000000]
I saw another thread that you had posted in previously. You had the user blacklist the " [/COLOR]rtl8xxxu " driver, I think. I tried that without any success; however, I've done a clean reinstall of Elementary OS Loki since then.[/FONT][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
```

Module                  Size  Used by
ctr                    16384  2
ccm                    20480  2
rtl8xxxu               73728  0
arc4                   16384  2
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              737280  4 rtl8xxxu,rtl_usb,rtlwifi,rtl8192cu
cfg80211              565248  2 mac80211,rtlwifi
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1
snd_hda_intel          40960  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
coretemp               16384  0
dcdbas                 16384  0
snd_hwdep              16384  1 snd_hda_codec
kvm_intel             172032  0
kvm                   540672  1 kvm_intel
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
input_leds             16384  0
joydev                 20480  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
irqbypass              16384  1 kvm
serio_raw              16384  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                24576  0
soundcore              16384  1 snd
shpchp                 36864  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
drbg                   32768  1
ansi_cprng             16384  0
xts                    16384  1
gf128mul               16384  1 xts
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               28672  1
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  3
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon
drm_kms_helper        155648  1 radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  2
drm                   364544  6 ttm,drm_kms_helper,radeon
psmouse               131072  0
libahci                32768  1 ahci
floppy                 73728  0
fjes                   28672  0
via_rhine              36864  0
mii                    16384  1 via_rhine

```

Edit: I believe that I typed this: " RTL8192cu " instead of " rtl8192cu " and that may have been an issue. I've changed the text and have rebooted. I also changed the name of the file in /etc/modprobe.d/ to "  rtl8192cu.conf ".

So currently, with the following file name:
 
```

" rtl8192cu.conf "

```

Placed in the following location:
 
```

/etc/modprobe.d/

```

Containing the following text:

```

"  options rtl8192cu rtw_power_mgnt=0 rtw_enusbss=0 " 

```

Is not helping. The device continues to go to sleep.

wlx5C889A6B4BD1 IEEE 802.11bgn  ESSID:"ISP0584" 
           Mode:Managed  Frequency:2.437 GHz  Access Point:  30:B5:85:2E:3C:80 
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:44   Missed beacon:0

 In the past the connection used to be named something like " WLAN0 ", but now it's " wlx " followed by my MAC Address.

Strangely, it says that "Power Management" is set to OFF.

---

### Post by chili555 on 2016-12-11
Let's disable power saving in Network Manager:```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```Restart NM:```
sudo service network-manager restart
```Any change?

It may take a reboot.

---

### Post by guimaster on 2016-12-11
```

default-wifi-powersave-on.conf

```

Has been changed to:

```

 [connection]
wifi.powersave = 2

```

Unfortunately, the device has gone to sleep again, and connection therefore has been lost. Yes, I did reboot after making the change, but the connection still has been lost.

I'm now testin[FONT=arial]g: [COLOR=#000000]wifi.powersave = 1[/COLOR][/FONT]

[COLOR=#000000][FONT=arial]I've tested this also, to no avail:

wifi.powersave = 0
[/FONT][/COLOR]

I just found this online, and it sounds like it's talking about this issue:

 [https://git.kernel.org/cgit/linux/kernel/git/jes/linux.git/commit/?h=rtl8xxxu-devel](https://git.kernel.org/cgit/linux/kernel/git/jes/linux.git/commit/?h=rtl8xxxu-devel)

 [COLOR=#333333][FONT=sans-serif]**rtl8xxxu: Work around issue with 8192eu and 8723bu devices not reconnecting**[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]**[rtl8xxxu-devel]("https://git.kernel.org/cgit/linux/kernel/git/jes/linux.git/log/?h=rtl8xxxu-devel")**[/FONT][/COLOR][COLOR=#333333][FONT=monospace]The H2C MEDIA_STATUS_RPT command for some reason causes 8192eu and8723bu devices not being able to reconnect.Reported-by: Barry Day <briselec@gmail.com>Signed-off-by: Jes Sorensen <Jes.Sorensen@redhat.com>

 [COLOR=green]+#ifdef RTL8XXXU_GEN2_REPORT_CONNECT[/COLOR][/FONT][/COLOR]
[COLOR=green][FONT=monospace]+    /*[/FONT][/COLOR]
[COLOR=green][FONT=monospace]+     * Barry Day reports this causes issues with 8192eu and 8723bu[/FONT][/COLOR]
[COLOR=green][FONT=monospace]+     * devices reconnecting. The reason for this is unclear, but[/FONT][/COLOR]
[COLOR=green][FONT=monospace]+     * until it is better understood, leave the code in place but[/FONT][/COLOR]
[COLOR=green][FONT=monospace]+     * disabled, so it is not lost.[/FONT][/COLOR]
[COLOR=green][FONT=monospace]+     */[/FONT][/COLOR]

```
 [B]lsmod | grep rtl
[/B][B]rtl8xxxu               73728  0
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              737280  4 rtl8xxxu,rtl_usb,rtlwifi,rtl8192cu
cfg80211              565248  2 mac80211,rtlwifi
[/B]
```[COLOR=#DD4814][/COLOR]I wonder what would happen if the rtl8192cu driver was blacklisted instead of the rtl8xxxu driver?

---

### Post by howefield on 2016-12-12
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by chili555 on 2016-12-12
> I wonder what would happen if the rtl8192cu driver was blacklisted instead of the rtl8xxxu driver?
I would do the opposite. Do you need explicit instructions?

---

### Post by guimaster on 2016-12-12
I mentioned previously that I already tried blacklisting the [COLOR=#000000]rtl8xxxu driver,[/COLOR] without success.

The [COLOR=#000000]rtl8xxxu is the newer driver. It should work better, no?[/COLOR]

---

### Post by chili555 on 2016-12-12
> The rtl8xxxu is the newer driver. It should work better, no?Possibly. There is always a bit of a gap between "should" and "does."

In the half-dozen or so similar cases I've worked on, blacklisting rtl8xxxu was the successful approach. In a very few cases, also updating to *rtlwifi_new* was helpful.

By all means, try both ways and let us know.

---

### Post by guimaster on 2016-12-15
> **chili555 said:**
> In the half-dozen or so similar cases I've worked on, blacklisting rtl8xxxu was the successful approach. In a very few cases, also updating to *rtlwifi_new* was helpful.

Just how similar were these cases to my problem? Could these users maintain their connection with a ping? Was the issue with their network adapters going to sleep, when not in use?

I haven't been trying to fix it the past few days as I've been busy, and a constant "ping -s 1" to my router keeps my connection alive.

 > **guimaster said:**
> Elementary OS 16.04

If when I boot my computer, I start and continually ping a website, such as Google.com, I will _never_ lose my connection (or if I ping my router continuously) However, if I am not running a ping, and I stop my internet activity, I will often lose my connection. From there I need to disable and re-enable wireless networking, in order to get a connection again. It seems clear to me that the problem is a matter of Ubuntu putting the device to sleep when not in use, and not waking it up again when needed.

---

### Post by chili555 on 2016-12-15
Wow. It takes less time to try it and confirm or deny it, than it does to write and post a push-back.

---

### Post by guimaster on 2017-03-14
Maybe it's too early to say so for sure, but I think I finally found a solution (4 months later!) I found this repository tonight: [https://github.com/lwfinger/rtl8192cu](https://github.com/lwfinger/rtl8192cu)

> [COLOR=#24292E][FONT=-apple-system]Repository for vendor driver for RTL8192CU[/FONT][/COLOR]

It's possible that I found this git repository before, but it may not have worked until now. The most recent 'commit' happened just 4 days ago.

Anyway, I downloaded the file and extracted it which created a folder called "rtl8192cu-master." I then opened a terminal window inside this folder and ran the following two commands:

```

[LIST]
[*]make prefix=/usr/local all
[*]sudo make prefix=/usr/local install
[/LIST]

```

 I did do some other things tonight as well, but I think this is the thing that fixed the problem. This was the last modification that I made tonight. I've been trying to lose my connection for the past hour, and I have been unable to do so.

 If my connection continues to work flawlessly, I'll do a fresh install and try just this solution to confirm that this alone was the problem solver. Then I will return here and mark the thread as solved.

---

