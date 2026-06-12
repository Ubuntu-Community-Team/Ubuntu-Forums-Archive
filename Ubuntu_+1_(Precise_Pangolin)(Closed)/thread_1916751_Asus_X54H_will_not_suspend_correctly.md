---
title: "Asus X54H will not suspend correctly"
date: 2012-01-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cryptotheslow on 2012-01-28
Hi,

I'm having problems getting this laptop to suspend properly with 12.04.

It seems to go through the motions but ends up unresponsive, with the screen still on showing whatever was there last, the HDD light permanently lit (although the drive ~seems~ to be spun down) and over the next 20 seconds or so the fan accelerates up to full speed from near idle where it usually is. Only recourse is a hard power down.

Asus X54H
M/Board vers: K54L
Intel i3 2310(M)
750GB SATA HDD
4GB DDR3 1333 RAM
Wireless: Atheros AR9285
LAN: AR8151 v2.0 Gigabit Ethernet (rev c0)

Ubuntu is clean installed into its own partitions (logical sda5 & 6).

When suspending:
Nothing is logged to /var/log/kern.log

/var/log/syslog
```
Jan 28 22:19:54 ubulaptop1204 anacron[2542]: Anacron 2.3 started on 2012-01-28
Jan 28 22:19:54 ubulaptop1204 anacron[2542]: Normal exit (0 jobs run)
```/var/log/pm-suspend.log
```
Sat Jan 28 22:19:53 GMT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux ubulaptop1204 3.2.0-11-generic #19-Ubuntu SMP Thu Jan 26 02:22:34 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  1 
rfcomm                 47604  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223755  1 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
joydev                 17693  0 
asus_nb_wmi            12667  0 
asus_wmi               24411  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
arc4                   12529  2 
psmouse                87603  0 
serio_raw              13211  0 
snd_hda_intel          33773  3 
snd_hda_codec         127723  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
ath9k                 132390  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              506931  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              410965  2 ath9k,ath9k_common
mac_hid                13253  0 
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              205544  3 ath9k,mac80211,ath
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
mei                    41616  0 
parport                46562  3 parport_pc,ppdev,lp
i915                  468516  1 
drm_kms_helper         42489  1 i915
wmi                    19256  1 asus_wmi
drm                   241834  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19411  1 i915
atl1c                  41679  0 
             total       used       free     shared    buffers     cached
Mem:       3950616     484580    3466036          0      52700     284172
-/+ buffers/cache:     147708    3802908
Swap:      2580476          0    2580476

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Jan 28 22:19:55 GMT 2012: performing suspend
```
All I see suspicious there is PulseAudio and Network Manager not being happy - although PulseAudio appears to resolve itself.

My fairly poor Launchpad search skills haven't turned up any bugs the same (but that could just be me :) )

Any thoughts on where else to look to see what is going on? 

Thanks
crypto

---

### Post by effenberg0x0 on 2012-01-28
My Asus K43E won't sleep without the following:
```

sudo -H gedit /etc/pm/sleep.d/20_custom-ehci-hcd

``````
#!/bin/sh
VERSION=1.1
DEV_LIST=/tmp/usb-dev-list
DRIVERS_DIR=/sys/bus/pci/drivers
DRIVERS="ehci xhci" # ehci_hcd, xhci_hcd
HEX="[[:xdigit:]]"
MAX_BIND_ATTEMPTS=2
BIND_WAIT=0.1

unbindDev() {
  echo -n > $DEV_LIST 2>/dev/null
  for driver in $DRIVERS; do
    DDIR=$DRIVERS_DIR/${driver}_hcd
    for dev in `ls $DDIR 2>/dev/null | egrep "^$HEX+:$HEX+:$HEX"`; do
      echo -n "$dev" > $DDIR/unbind
      echo "$driver $dev" >> $DEV_LIST
    done
  done
}

bindDev() {
  if [ -s $DEV_LIST ]; then
    while read driver dev; do
      DDIR=$DRIVERS_DIR/${driver}_hcd
      while [ $((MAX_BIND_ATTEMPTS)) -gt 0 ]; do
          echo -n "$dev" > $DDIR/bind
          if [ ! -L "$DDIR/$dev" ]; then
            sleep $BIND_WAIT
          else
            break
          fi
          MAX_BIND_ATTEMPTS=$((MAX_BIND_ATTEMPTS-1))
      done  
    done < $DEV_LIST
  fi
  rm $DEV_LIST 2>/dev/null
}

case "$1" in
  hibernate|suspend) unbindDev;;
  resume|thaw)       bindDev;;
esac

``````

sudo chmod +x /etc/pm/sleep.d/20_custom-ehci-hcd

```

---

### Post by cryptotheslow on 2012-01-28
Thanks - I'll give a go.

Have you flagged this up on launchpad?

---

### Post by effenberg0x0 on 2012-01-28
> **cryptotheslow said:**
> Thanks - I'll give a go.

Have you flagged this up on launchpad?
No, I just got this laptop a week ago or so, used it 3 or 4 times, haven't even managed to scratch it yet lol. This fix allowed it to suspend/wake correctly, but I'm aware there's a couple BIOS updates in ASUS website, other acpi fixes, etc. I was hoping to find the time to study it a little, update the BIOS, etc in order to be able to create a more complete report. 

Example: There's something wrong with the battery too. Even when plugged to AC for hours, precise shows it with 80% charge. W7 correctly displays the battery status / remaining time. Powertop/jupiter, etc didn't fix it.

---

### Post by cryptotheslow on 2012-01-28
Likewise - only had this one 3 weeks and it is just my couch-arm residing browse / message thing - hence I can afford to fool around with alphas on it - it's expendable.

That workaround worked perfectly here too - thanks :D

No problem here with the battery indicator. However, battery life is markedly down as opposed to W7 (1.5hrs Ubuntu / ~3hrs W7 from full charge) - but the indicator seems to work fine. But I've not optimised anything for power so no surprise really.

If it's OK with you - I'll leave the bug report to you - I expect the level of information I'd be able to provide would annoy rather than help the devs. I'm really still a dabbler.

If you have the time and want to explain how you worked out that workaround would work - I'd much appreciate learning - but I understand if you don't, I know how annoyingly time-consuming clueless faps (me) questions can be :D

Anyways - thanks again for your help.

---

### Post by ft_ on 2012-01-29
(Asus X43SA - K43SA with SSD Crucial M4)

The USB 3 suspend script is needed by my comp too (Oneiric or Precise).
Hibernation is full ok.

BUT : be aware that resume from sleep does shutdown instead of resume... This seems to be SSD-related. If you know a tweak, I'll send you 3MM$.

---

### Post by effenberg0x0 on 2012-01-29
> **ft_ said:**
> (Asus X43SA - K43SA with SSD Crucial M4)

The USB 3 suspend script is needed by my comp too (Oneiric or Precise).
Hibernation is full ok.

BUT : be aware that resume from sleep does shutdown instead of resume... This seems to be SSD-related. If you know a tweak, I'll send you 3MM$.

@ft_ I have replaced the default 7200PM HDD for a Corsair Force Sata3 120GB SSD. In this machine, the script works OK, there's no issue wth resume from sleep causing a shutdown.

@cryptotheslow Glad it worked for you. I guessed it would help in your case simply because I have read many reports of ASUS owners using this script as a way to fix suspend/resume. It was just a guess.

I am not the author of this script, it's widespread all over the net. As I said, I haven't really used this laptop yet and tested it thoroughly but, in a first glance, not only this script needs to be changed/improved but there are other fixes needed for compatibility. I am probably gonna update the BIOS, test EFI with it (never played with EFI, gotta learn it). I had plans to use it as a base for kexec tests too. I just have to find the time... I'm really overdue in mostly everything and will be working overnight for the next week or so before I can play again...

---

### Post by Helios747 on 2012-03-18
Well this is interesting!

This script has fixed shutdown on my ASUS K53E, but suspend still doesn't work. Odd.

Here's a copy of my suspend.log

```
Initial commandline parameters: 
Wed Mar 14 01:19:56 PDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux anthony-K53E 3.2.0-18-generic #29-Ubuntu SMP Fri Mar 9 21:36:08 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
dm_crypt               23125  1 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223860  1 
snd_hda_intel          33773  5 
snd_hda_codec         127669  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72627  0 
soundcore              15091  1 snd
videodev               98259  1 uvcvideo
cfg80211              205544  3 ath9k,mac80211,ath
joydev                 17693  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
asus_nb_wmi            12667  0 
asus_wmi               24411  1 asus_nb_wmi
v4l2_compat_ioctl32    17128  1 videodev
sparse_keymap          13890  1 asus_wmi
psmouse                87603  0 
serio_raw              13211  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
uas                    18027  0 
usb_storage            49198  0 
i915                  468529  3 
wmi                    19256  1 asus_wmi
drm_kms_helper         42489  1 i915
drm                   241873  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19411  1 i915
atl1c                  41679  0 
             total       used       free     shared    buffers     cached
Mem:       5888080    3924604    1963476          0     152328    2007212
-/+ buffers/cache:    1765064    4123016
Swap:       974844          0     974844

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Mar 14 01:19:57 PDT 2012: performing suspend
Initial commandline parameters: 
Wed Mar 14 13:47:59 PDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux anthony-K53E 3.2.0-18-generic #29-Ubuntu SMP Fri Mar 9 21:36:08 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
btrfs                 652957  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    75303  0 
qnx4                   17677  0 
hfsplus                84867  0 
hfs                    54782  0 
minix                  36288  0 
ntfs                  101885  0 
vfat                   17585  0 
msdos                  17332  0 
fat                    61512  2 vfat,msdos
jfs                   186647  0 
xfs                   836544  0 
reiserfs              244805  0 
ext2                   73795  0 
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223860  1 
joydev                 17693  0 
asus_nb_wmi            12667  0 
asus_wmi               24411  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
mei                    41616  0 
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127669  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 132390  0 
mac_hid                13253  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              506816  1 ath9k
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                87603  0 
uvcvideo               72627  0 
serio_raw              13211  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
wmi                    19256  1 asus_wmi
i915                  468529  3 
atl1c                  41679  0 
drm_kms_helper         42489  1 i915
drm                   241873  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19411  1 i915
             total       used       free     shared    buffers     cached
Mem:       5888072    2698884    3189188          0      90644    1479744
-/+ buffers/cache:    1128496    4759576
Swap:       974844          0     974844

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Mar 14 13:48:00 PDT 2012: performing suspend
Initial commandline parameters: 
Thu Mar 15 13:49:20 PDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux anthony-K53E 3.2.0-18-generic #29-Ubuntu SMP Fri Mar 9 21:36:08 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223860  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_hda_intel          33773  3 
snd_hda_codec         127669  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
cfg80211              205544  3 ath9k,mac80211,ath
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
joydev                 17693  0 
asus_nb_wmi            12667  0 
mac_hid                13253  0 
asus_wmi               24411  1 asus_nb_wmi
psmouse                87603  0 
sparse_keymap          13890  1 asus_wmi
serio_raw              13211  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
wmi                    19256  1 asus_wmi
i915                  468529  3 
drm_kms_helper         42489  1 i915
drm                   241873  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19411  1 i915
atl1c                  41679  0 
             total       used       free     shared    buffers     cached
Mem:       5888072    1360812    4527260          0      36388     725692
-/+ buffers/cache:     598732    5289340
Swap:       974844          0     974844

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Mar 15 13:49:22 PDT 2012: performing suspend
Initial commandline parameters: 
Sun Mar 18 12:30:18 PDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux anthony-K53E 3.2.0-19-generic #30-Ubuntu SMP Fri Mar 16 16:27:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
dm_crypt               23125  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223860  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
joydev                 17693  0 
asus_nb_wmi            12667  0 
asus_wmi               24411  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
arc4                   12529  2 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87603  0 
serio_raw              13211  0 
mac_hid                13253  0 
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205544  3 ath9k,mac80211,ath
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
i915                  468529  3 
drm_kms_helper         42489  1 i915
drm                   241873  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
wmi                    19256  1 asus_wmi
video                  19411  1 i915
atl1c                  41679  0 
             total       used       free     shared    buffers     cached
Mem:       5888072    1520644    4367428          0      55888     848508
-/+ buffers/cache:     616248    5271824
Swap:       974844          0     974844

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci-hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci-hcd suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Mar 18 12:30:20 PDT 2012: performing suspend
```

What happens visually is that suspend blanks the screen, but the LCD doesn't shutoff and neither does the CPU or fan. It just sits there.

Specs of laptop if needed:

Intel Core i5-2410M
6GB DDR3 RAM
500 GB HDD
Atheros wireless
Atheros ethernet

---

### Post by cryptotheslow on 2012-03-18
You might want to consider starting a new thread (with ref to this one) as a lot of people won't bother looking in here as it is marked as solved.

No idea on your problem unfortunately - thankfully the answer to mine was spoon-fed to me above :D

---

