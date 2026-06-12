---
title: "Broadcom 14e4:4312 - Wifi WPA2: Bad password"
date: 2015-10-09
forum: Ubuntu/Debian BASED
---

### Post by laks2 on 2015-10-09
Hello!

I'm new to Linux, but have learned a lot by trying to fix this issue. I have been banging my head against the issue for several days, reading through every comprehensible guide and forum post on the topic. I will describe my problem below, but I am not at home at the moment so I can't run the wifi script from the sticky at this time; please bear with me.

I have a Lenovo S10e, running Elementary OS (I have also tried with Mint and vanilla Ubuntu) with the 4312 network card. Everything is updated, all the correct drivers have been installed and tested independently. Wicd tells me the problem is a bad password, the Broadcom STA driver (wl) has me constantly re-entering my wifi password without managing to connect (same result if I use the wrong password on purpose). I am able to get internett on the laptop by connecting an ethernet cable.

I read somewhere that the correct driver for my card is the b43-lpphy version, but I am unable to install this via terminal because the package is unavailable; it also says that the b43 package replaces it. Unfortunately, the b43 package does a worse job of connecting to the wifi than the STA driver does (I don't even get a password prompt, it just gives up on connecting after a while.)
-Question: Has the b43-lpphy version really been replaced? Is the b43 package supposed to do the trick, or can I fix my problem by getting a hold of the lpphy version somehow?
-Question: Does the different results between wl and b43 indicate that the latter is failing to connect to Wifi for a different reason than wl?

I have wpa_supplicant installed, but my attempts at configuring it have not borne fruits. I have tried filling in the psk output from wpa_passphrase "my-ssid" "my-password", nothing changed.
-Question: I have never found a version of wpa_supplicant.conf with any text in it. It's always blank, and I always end up filling it out with text found online. Is this a symptom of an underlying problem?
-Question: What should my /etc/network/interfaces file look like with respect to my laptop, wireless card, and problem?

I am at my wits end trying to resolve this problem. I don't need you guys to hold my hand, but I am in need of new theories and potential solutions to explore in order to get my wifi up and running. My router (ZyXEL P8702N) does not have any other options than WPA and WPA2, so if I want Wifi, I need to resolve the issue.

Thanks in advance :)

---

### Post by Ubunterrific on 2015-10-11
> **laks2 said:**
> Hello!

I'm new to Linux, but have learned a lot by trying to fix this issue. I have been banging my head against the issue for several days, reading through every comprehensible guide and forum post on the topic. I will describe my problem below, but I am not at home at the moment so I can't run the wifi script from the sticky at this time; please bear with me.

I have a Lenovo S10e, running Elementary OS (I have also tried with Mint and vanilla Ubuntu) with the 4312 network card. Everything is updated, all the correct drivers have been installed and tested independently. Wicd tells me the problem is a bad password, the Broadcom STA driver (wl) has me constantly re-entering my wifi password without managing to connect (same result if I use the wrong password on purpose). I am able to get internett on the laptop by connecting an ethernet cable.

I read somewhere that the correct driver for my card is the b43-lpphy version, but I am unable to install this via terminal because the package is unavailable; it also says that the b43 package replaces it. Unfortunately, the b43 package does a worse job of connecting to the wifi than the STA driver does (I don't even get a password prompt, it just gives up on connecting after a while.)
-Question: Has the b43-lpphy version really been replaced? Is the b43 package supposed to do the trick, or can I fix my problem by getting a hold of the lpphy version somehow?
-Question: Does the different results between wl and b43 indicate that the latter is failing to connect to Wifi for a different reason than wl?

I have wpa_supplicant installed, but my attempts at configuring it have not borne fruits. I have tried filling in the psk output from wpa_passphrase "my-ssid" "my-password", nothing changed.
-Question: I have never found a version of wpa_supplicant.conf with any text in it. It's always blank, and I always end up filling it out with text found online. Is this a symptom of an underlying problem?
-Question: What should my /etc/network/interfaces file look like with respect to my laptop, wireless card, and problem?

I am at my wits end trying to resolve this problem. I don't need you guys to hold my hand, but I am in need of new theories and potential solutions to explore in order to get my wifi up and running. My router (ZyXEL P8702N) does not have any other options than WPA and WPA2, so if I want Wifi, I need to resolve the issue.

Thanks in advance :)

Hello :KS  I'll try to answer as many Qs as i can.

[LIST=1]
[*]Check out this handy page: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=b43&searchon=names](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=b43&searchon=names) - it will tell you all the versions in each of the 'buntu' flavoured repos. If i'm reading it correctly, it seems b43-lpphy is a very old name and was superceded. Newer versions may more than likely have annoying bugs fixed in them, but there'll be a question of dependency-hell if you try pulling in versions from later versions (more grey hairs lol) 
[*]Just a thought but the first thing i would check if i was being told the password was 'bad', apart from obviously checking like 5 times i'd spelt it exactly correctly :p, would next be to check what encryption specifics are set on the router's SSID password settings - WPA2 **Personal** or **Enterprise**? **TKIP** or **AES**? (I think WPA2 Personal AES is probably most common for home networks nowadays.) If it's something like that, that's an easy, harmless thing to correct. 
[*]I don't really like manually editing wpa_supplicant config settings (incase i make a spelling mistake and end up in just such a situation!), but you're right, many config files have survived over the ages and now exist but don't necessarily have anything in them - the Xorg.conf springs to mind. For example, mine resides at /etc/dbus-1/system.d/wpa_supplicant.conf and only contains: 
[/LIST]

```
<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
        <policy user="root">
                <allow own="fi.epitest.hostap.WPASupplicant"/>

                <allow send_destination="fi.epitest.hostap.WPASupplicant"/>
                <allow send_interface="fi.epitest.hostap.WPASupplicant"/>

                <allow own="fi.w1.wpa_supplicant1"/>

                <allow send_destination="fi.w1.wpa_supplicant1"/>
                <allow send_interface="fi.w1.wpa_supplicant1"/>
                <allow receive_sender="fi.w1.wpa_supplicant1" receive_type="signal"/>
        </policy>
        <policy group="netdev">
                <allow send_destination="fi.epitest.hostap.WPASupplicant"/>
                <allow send_interface="fi.epitest.hostap.WPASupplicant"/>

                <allow send_destination="fi.w1.wpa_supplicant1"/>
                <allow send_interface="fi.w1.wpa_supplicant1"/>
                <allow receive_sender="fi.w1.wpa_supplicant1" receive_type="signal"/>
        </policy>
        <policy context="default">
                <deny own="fi.epitest.hostap.WPASupplicant"/>
                <deny send_destination="fi.epitest.hostap.WPASupplicant"/>
                <deny send_interface="fi.epitest.hostap.WPASupplicant"/>

                <deny own="fi.w1.wpa_supplicant1"/>
                <deny send_destination="fi.w1.wpa_supplicant1"/>
                <deny send_interface="fi.w1.wpa_supplicant1"/>
                <deny receive_sender="fi.w1.wpa_supplicant1" receive_type="signal"/>
        </policy>
</busconfig> 
```

and my /etc/network/interfaces:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```
The actual settings for my SSID e.t.c will all be on NetworkManager related configs, i expect. 

Could i ask which linux kernel version you're running and see the output of **lsmod **with the device plugged in, please? (Let's check for competing modules or something or at least see what's at play)

---

### Post by laks2 on 2015-10-12
Thanks for the response :) My wpa_supplicant.conf file is located in the same spot as yours, and has similar contents. My network is definitely WPA2 AES, and the network manager settings reflect this. 

Kernel:  3.19.0-30-generic

Here is the output from lsmod:

```
 laks@writepad:~$ lsmodModule                  Size  Used by
snd_hda_codec_realtek    69632  1 
snd_hda_codec_generic    65536  1 snd_hda_codec_realtek
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         122880  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
uvcvideo               73728  0 
coretemp               16384  0 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
videobuf2_vmalloc      16384  1 uvcvideo
snd_rawmidi            28672  1 snd_seq_midi
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
v4l2_common            16384  1 videobuf2_core
joydev                 20480  0 
wl                   6148096  0 
serio_raw              16384  0 
videodev              139264  3 uvcvideo,v4l2_common,videobuf2_core
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28672  2 snd_pcm,snd_seq
media                  24576  2 uvcvideo,videodev
lpc_ich                20480  0 
rfcomm                 61440  0 
bnep                   20480  2 
bluetooth             430080  10 bnep,rfcomm
cfg80211              450560  1 wl
snd                    69632  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
shpchp                 32768  0 
soundcore              16384  2 snd,snd_hda_codec
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
parport_pc             32768  0 
ppdev                  20480  0 
mac_hid                16384  0 
lp                     16384  0 
parport                40960  3 lp,ppdev,parport_pc
ums_realtek            20480  0 
uas                    24576  0 
usb_storage            57344  2 uas,ums_realtek
psmouse               102400  0 
i915                  921600  3 
tg3                   159744  0 
pata_acpi              16384  0 
i2c_algo_bit           16384  1 i915
drm_kms_helper        114688  1 i915
ptp                    20480  1 tg3
drm                   286720  5 i915,drm_kms_helper
pps_core               20480  1 ptp
video                  20480  1 i915
wmi                    20480  0 

```

---

### Post by Hadaka on 2015-10-12
Hi, please copy and paste then post the output
one command at a time.
```
lspci -n | awk '/0280/ {print$3}'
cat /etc/default/crda | awk '/REGDOMAIN=/ {print}'
rfkill list all

```
After re-reading your thread, i think i know what may be causing you problems,
From a working wired connection open a terminal and do,,,
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
remove the wired connection....reboot...test wireless,
thanks

---

### Post by coffeecat on 2015-10-13
> **laks2 said:**
> I have a Lenovo S10e, running Elementary OS

*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by laks2 on 2015-10-18
thanks for the suggestion, unfortunately it had no effect. I'm still unable to connect

---

### Post by laks2 on 2015-10-18
```

14e3:4315

0: ideapad_wlan: Wireless Lan
                     Soft blocked: no
                     Hard blocked: no
1: ideapad_bluetooth: Bluetooth
                     Soft blocked: yes
                     Hard blocked: no

```

---

