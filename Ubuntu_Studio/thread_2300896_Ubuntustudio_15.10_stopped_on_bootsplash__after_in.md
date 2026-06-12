---
title: "Ubuntustudio 15.10 stopped on bootsplash  after instalation FGLRX driver ."
date: 2015-10-29
forum: Ubuntu Studio
---

### Post by wlodarek1 on 2015-10-29
I istalled newest ubuntustudio 15.10 on my laptop acer aspire 7540 G
This model have a ATI MOBILITY RADEON 4500 graphic card .
System property started in default graphic driver - RADEON 
When I using "additional drivers" and installed FGRX driver  , and add command "aticonfig --initial -f  - 
system not started . Start freezing when bootspash display ;

[Zdj&#281;cia](http://pokazywarka.pl/qwdmze/)
Keyboard shortcuts type CTRL+ALT+F1 or F2 or BACKSPACE or DELETE - not working .

This situation is emerging in the standard kernel and kernel "low latency"
Please urgent help .[ATTACH=CONFIG]265225[/ATTACH]

---

### Post by ajgreeny on 2015-10-29
The fglrx driver is probably the reason for this as support for fglrx disappeared from the 4xxx series of AMD/ATI cards a long time ago, and there is an even more recent problem of fglrx for all AMD/ATI cards in 15.10.

If you are unable to get to a command-line when you boot I am not sure how to tell you to proceed other than booting to recovery-mode from grub and running ```
mount -o rw,remount / && apt-get remove fglrx
```
If you do not normally see a grub menu because you have only Linux on the machine you will need to press shift at boot for legacy BIOS systems, or possibly repeat presses of Esc in UEFI system.

---

### Post by wlodarek1 on 2015-10-29
Thank you ajgreeny for replies ):P
I removed FGLRX package  and after reboot xfce desktop running .
But resolution is not property ; 1152x864 76Hz 
Property resolution should be 1600x900 60 Hz .
RADEON module not return 
```
LSMOD results ;
darek@darek-JV71TR:~$ lsmod
Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  3
ccm                    20480  3
arc4                   16384  2
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     49152  2
snd_hda_intel          36864  5
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
ath9k                 147456  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
ath9k_common           36864  1 ath9k
snd_rawmidi            32768  1 snd_seq_midi
kvm_amd                65536  0
ath9k_hw              471040  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
kvm                   512000  1 kvm_amd
fglrx               13447168  1
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               90112  0
mac80211              745472  1 ath9k
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_core         49152  1 uvcvideo
snd_timer              32768  2 snd_pcm,snd_seq
edac_core              53248  0
input_leds             16384  0
serio_raw              16384  0
v4l2_common            16384  1 videobuf2_core
edac_mce_amd           24576  0
k10temp                16384  0
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
joydev                 20480  0
i2c_piix4              24576  0
cfg80211              557056  4 ath,ath9k_common,ath9k,mac80211
amd_iommu_v2           20480  1 fglrx
soundcore              16384  1 snd
shpchp                 36864  0
mac_hid                16384  0
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
ums_realtek            20480  0
uas                    24576  0
usb_storage            69632  2 uas,ums_realtek
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_generic,usbhid
psmouse               126976  0
tg3                   163840  0
ptp                    20480  1 tg3
pps_core               20480  1 ptp
ahci                   36864  2
libahci                32768  1 ahci
wmi                    20480  1 acer_wmi
video                  36864  1 acer_wmi
darek@darek-JV71TR:~$ 

```
Please help .....

---

### Post by ajgreeny on 2015-10-29
Sorry, it is years since I had dealings with AMD cards and I am now too out of date to help with that question.

What does command **xrandr** show in terminal?

---

### Post by haraldthi on 2015-10-31
I probably had the same problem when upgrading from Ubuntu Studio 15.04 to 15.10. But luckily I had the old 3.19.0-31 kernel still available on the system and got it working from there. There may very well be a mismatch between the fglrx kernel driver and the new kernel. 
And I do a lot of video work, so the best graphics driver possible is more important to me than an updated kernel.

You can boot into advanced/rescue mode, start the network and log in as root. Then you need to use a non-graphical package manager to try to find an older kernel that works with fglrx until it's fixed.
I use aptitude, but I doubt it's installed by default.
So you can write:
apt-get install aptitude
and press enter to get that command executed. After aptitude is installed, you can write
aptitude
and press enter to get aptitude started.
You may have to press "u" (without quotes) to update the list of packages in the cache. There's a menu if you press "F10" and a help screen at "?". Pressing "q" makes you go back, and out, like an escape button.
Then you can press / to start a search and write "linux" (without quotes) to find a package that has linux in it's name. There are some, but not too many, and you can find the next one by pressing "n".
3.19-0-31 works fine for me, but I guess any 3.19 kernel works. You want at least the linux-image package of that name.
Press "+" to add the package to the list of packages to install. Press "g" to get the short list of packages to be changed, and "g" again to start the install.
Press q to go out and "y" to confirm. Write:
reboot
on the command line and press enter to run the command.
The computer will reboot. At the boot prompt, choose advanced and the slightly older kernel you just installed.
Hope it works for you! :-)

---

### Post by QIII on 2015-10-31
Again, in case it was missed:  that video adapter is no longer supported by AMD on Linux.  No amount of searching for other kernels will make it work.  The only option is to uninstall fglrx and us the default open source Radeon driver.

---

### Post by haraldthi on 2015-10-31
For the technically interested, I digged this out of my /var/log/syslog. It's from my first failed start after upgrading last night. It hung like the image on the original post, with a slightly different boot screen (the same as on 14.04). I had to use a short press on the power button to make it stop, as there was no reaction from keyboard or mouse.

Happy hunting! :-)

---

### Post by haraldthi on 2015-10-31
Aha. I didn't consider the old card. I have something more recent, an AMD APU. The graphics solution on it is actually pretty decent, and it was at least at the time good value for the money.
You can get these quite cheap now, if you have the motherboard for it...

---

