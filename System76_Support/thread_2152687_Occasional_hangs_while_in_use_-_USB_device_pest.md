---
title: "Occasional hangs while in use - USB device pest??"
date: 2013-06-08
forum: System76 Support
---

### Post by jcllings on 2013-06-08
So I think this is a misbehaving USB driver / device.  How can I identify such a device so that I can replace the hardware with something that doesn't suck? 

System76 Model: panp9
OS Version: 12.04

###@#########:~/temp/tmp/system_logs_20130608_h11m19s57$ uname -a
Linux blacklightning 3.2.0-45-generic #70-Ubuntu SMP Wed May 29 20:12:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

logs.tar is attached.  Latest occurence sometime between 11:15 and 11:30 am, Saturday June 8th.  Since it was a system hang, there was a restart or two.  I re-installed the System76 drivers and that required a restart also. 
System state was that I had just woken it up and was making a G+ entry regarding the wonders of IntelliJ IDEA + JAD plugin. Was thinking perhaps USB driver failed to wake properly?

USB devices I am using:

Logitech G510 macro and media keyboard. It's not very well supported and I'm using it on a USB hub which it may not like. Doesn't seem to be a problem on 'doze.  I sometimes unplug the hub and plug it in to a Doze 7 laptop and use it over synergy. 
Bus 001 Device 004: ID 046d:c22d Logitech, Inc. G510 Gaming Keyboard
Bus 001 Device 005: ID 046d:c045 Logitech, Inc. Optical Mouse

###@#########:~/temp/tmp/system_logs_20130608_h11m19s57$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    |__ Port 2: Dev 6, If 0, Class=stor., Driver=usb-storage, 480M
    |__ Port 4: Dev 7, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
    |__ Port 4: Dev 7, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/6p, 480M
        |__ Port 2: Dev 7, If 0, Class=hub, Driver=hub/4p, 480M
            |__ Port 1: Dev 8, If 0, Class=HID, Driver=usbhid, 12M
            |__ Port 1: Dev 8, If 1, Class=HID, Driver=usbhid, 12M
            |__ Port 2: Dev 9, If 0, Class=HID, Driver=usbhid, 1.5M
            |__ Port 4: Dev 10, If 0, Class=hub, Driver=hub/4p, 480M

USB 3.0 External backup drive. lsusb says:  Bus 003 Device 006: ID 1058:0740 Western Digital Technologies, Inc. My Passport 1TB

Lastly, I have an external HDMI monitor, ACER model H233H.

Additional toy notes (Not in use at the time): Virtual Box + windows 7 vm and a Logitech orbital Video cam. 

###@#########:~/temp/tmp/system_logs_20130608_h11m19s57$ lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23237  0 
vboxnetadp             25670  0 
vboxnetflt             23478  0 
vboxdrv               320211  3 vboxpci,vboxnetadp,vboxnetflt
ses                    17417  0 
enclosure              15312  1 ses
usbhid                 47238  0 
hid                    99636  1 usbhid
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_via      51474  1 
usb_storage            49198  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
iwlwifi               401125  0 
r8169                  62154  0 
psmouse                97485  0 
serio_raw              13211  0 
mac80211              506862  1 iwlwifi
i915                  478189  3 
drm_kms_helper         46978  1 i915
rts_bpp               353210  0 
drm                   241971  4 i915,drm_kms_helper
cfg80211              205774  2 iwlwifi,mac80211
mei                    41616  0 
i2c_algo_bit           13423  1 i915
wmi                    19256  0 
video                  19651  1 i915
parport_pc             32866  0 
rfcomm                 47604  0 
bnep                   18281  2 
mac_hid                13253  0 
bluetooth             180153  10 rfcomm,bnep
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
ext2                   73795  1

---

### Post by isantop on 2013-06-10
There's currently a kerne issue that causes problems when USB 3 devices reach high I/O. Try plugging the External Drive into a  USB 2 port.

---

### Post by jcllings on 2013-06-10
> **isantop said:**
> There's currently a kerne issue that causes problems when USB 3 devices reach high I/O. Try plugging the External Drive into a  USB 2 port.

It's just my backup drive. It only gets used at 3am and was not in use when this happened.

---

### Post by isantop on 2013-06-11
I would still try moving the drive and seeing if it still happens. If possible, try it with nothing plugged into the 3.0 port.

---

### Post by jcllings on 2013-11-23
This behaviour has long since ceased.  Assume a solution came down in an update.

---

