---
title: "Unity leaves a shadow when hiding"
date: 2012-10-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Prowlcat on 2012-10-05
On Quantal amd64, I just installed a new Geforce GT 520 video card. When using nouveau, Unity leaves a shadow on the screen that affects all opened windows.
Using the latest nvidia-current fixes that but brings along another reported bug, Unity stays hidden all the time, and also nvidia-current offers me less 16-9 resolutions settings than nouveau does.

I booted my system with the latest USB live and have the same symptom. Does anyone kow what's happening, if it's a reported bug?

---

### Post by josephmills on 2012-10-05
Do you mean a shadow like this ? 
[http://www.youtube.com/watch?v=VlOacuIldM8&feature=g-upl](http://www.youtube.com/watch?v=VlOacuIldM8&feature=g-upl)

as far as filing a bug you can open your terminal and enter in 
```
ubuntu-bug <[COLOR="DarkRed"]name of package[/COLOR]>
```

make sure that name of package is the name of the package like 
```
ubuntu-bug unity 
```

would launch apport and gather all the info then send you to launchpad by opening a browser. Then Launchpad asks you to enter a small input about the bug then checks to see if any other bugs are there, that are the same. 

[http://www.youtube.com/watch?v=495V7FokwBU&list=UUzkAk08QdVFd1CmwWQBD3Sw&index=30&feature=plpp_video](http://www.youtube.com/watch?v=495V7FokwBU&list=UUzkAk08QdVFd1CmwWQBD3Sw&index=30&feature=plpp_video)


can you please open you terminal and enter in 
```
lspci -vnn | grep VGA
```
and 

```
lsmod
```

then paste here thanks

---

### Post by Prowlcat on 2012-10-05
I watched the video but can find the relationship?

lspci -vnn | grep VGA
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119 [GeForce GT 520] [10de:1040] (rev a1) (prog-if 00 [VGA controller])

```
lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39842  1 
nls_iso8859_1          12713  1 
pci_stub               12622  1 
vboxpci                23157  0 
vboxnetadp             25670  0 
vboxnetflt             23442  0 
vboxdrv               320371  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 46619  0 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
snd_hda_codec_hdmi     32007  2 
snd_hda_codec_realtek    77876  1 
ext2                   72880  1 
hid_logitech           26585  0 
ff_memless             13013  1 hid_logitech
joydev                 17457  0 
arc4                   12529  2 
xfs                   837979  2 
hid_generic            12493  0 
kvm_amd                55604  0 
kvm                   414070  1 kvm_amd
usbhid                 46947  1 hid_logitech
hid                   100366  3 hid_logitech,hid_generic,usbhid
psmouse                95552  0 
microcode              22803  0 
nouveau               895609  2 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
k10temp                13126  0 
serio_raw              13215  0 
ttm                    83595  1 nouveau
drm_kms_helper         46784  1 nouveau
edac_core              52451  0 
edac_mce_amd           23303  0 
drm                   275528  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13413  1 nouveau
mxm_wmi                12979  1 nouveau
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
ath9k                 131308  0 
mac80211              539908  1 ath9k
snd_rawmidi            30512  1 snd_seq_midi
ath9k_common           14055  1 ath9k
ath9k_hw              395218  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              206566  3 ath9k,mac80211,ath
video                  19335  1 nouveau
asus_atk0110           17646  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13205  0 
wmi                    19070  2 nouveau,mxm_wmi
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
i2c_nforce2            13013  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
uas                    17844  0 
usb_storage            48838  1 
forcedeth              67156  0 
pata_amd               14118  0
```
Thanks!

---

### Post by Prowlcat on 2012-10-08
Thanks, I just reported bug #1063748.

---

