---
title: "Firewire Expresscard"
date: 2010-02-10
forum: Ubuntu Studio
---

### Post by aib007 on 2010-02-10
Hi, I would like to ask for a little help. I have a TC desktop konnect 6  firewire interface that is connected through an expresscard to my  Toshiba Satellite. I have tried all the possible commands but  unfortunately ubuntu studio doesn't see it. I am quite new and  unexperienced so this turned out into a really painful and traumatizing  experience. 
I have installed Ubuntu Studio 8.04, 9.04, also 64 Studio. The same  problem. I don't how I could see if the problem is the Expresscard, it's  TI so it should work (it works fine in Windows) or the firewire  soundcard. Under /dev there is no /raw1394... I have also tried with an edirol fa101, that i borrowed from a friend but it didn't show up in Jack control either. Please if anybody knows what I could do, give me some advice. 
 I already tried to use the sudo modprobe pciehp command, and it says  module not detected, also CONFIG_HOTPLUG_PCI_PCIE=y means the module  should be in the kernel. I would realy like to focus on making some  music, so please give any sugestions. 

Here is what I copied from the  system report, i am not sure if this means the Expresscard is only seen, or also installed: 

XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge
Property    Value
info.subsystem    pci
info.product    XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge
info.udi    /org/freedesktop/Hal/devices/pci_104c_8231
info.vendor    Texas Instruments
info.parent    /org/freedesktop/Hal/devices/pci_8086_2843
pci.product    XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge
pci.vendor_id    4172
pci.vendor    Texas Instruments
pci.product_id    33329
pci.device_protocol    0
pci.device_subclass    4
pci.subsys_vendor_id    0
pci.device_class    6
pci.subsys_product_id    0
pci.linux.sysfs_path     /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0
linux.hotplug_type    2
linux.subsystem    pci
linux.sysfs_path    /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0
XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link)
Property    Value
info.subsystem    pci
info.product    XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link)
info.vendor    Texas Instruments
info.parent    /org/freedesktop/Hal/devices/pci_104c_8231
info.linux.driver    ohci1394
info.udi    /org/freedesktop/Hal/devices/pci_104c_8235
pci.product    XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link)
pci.vendor_id    4172
pci.vendor    Texas Instruments
pci.product_id    33333
pci.device_protocol    16
pci.device_subclass    0
pci.subsys_vendor_id    22136
pci.device_class    12
pci.subsys_product_id    4660
pci.linux.sysfs_path     /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/0000:04:00.0
linux.hotplug_type    2
linux.subsystem    pci
linux.sysfs_path     /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/0000:04:00.0 
 

Please if anybody knows what I could do, give me some advice. 
I already tried to use the sudo modprobe pciehp command, and it says  module not detected, also CONFIG_HOTPLUG_PCI_PCIE=y means the module  should be in the kernel. I would realy like to focus on making some  music, so please give any sugestions.

---

### Post by mango42 on 2010-02-10
This page should help (I suspect your problem is to do with permissions):-

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

and

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

Although I haven't got that far yet with my firewire attempts. I'm almost envious that your setup is actually recognised ;-)

I would also recommend a fresh install of UbuntuStudio 9.10 as your quickest way back to music making...

---

### Post by AutoStatic on 2010-02-10
[http://ffado.org/?q=devicesupport%2Flist&filter0=t.c.+electronic&filter1=&op2=OR&filter2](http://ffado.org/?q=devicesupport%2Flist&filter0=t.c.+electronic&filter1=&op2=OR&filter2)

The Konnekt 8 works apparently: [http://ffado.org/?q=node/78](http://ffado.org/?q=node/78)
Let's hope the Konnekt 6 is more or less the same.

For starters, could you post the outcome of **lspci** in a terminal? You can copy the outcome with Shift+Ctrl+c and then paste it with Ctrl+v. And also the outcome of **lsmod** with the Expresscard inserted.

---

### Post by aib007 on 2010-02-11
> **mango42 said:**
> This page should help (I suspect your problem is to do with permissions):-

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

and

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

Although I haven't got that far yet with my firewire attempts. I'm almost envious that your setup is actually recognised ;-)

I would also recommend a fresh install of UbuntuStudio 9.10 as your quickest way back to music making...

Hi, thanks for the links, i tried everything I could find related to my problem before asking for help on the forum. I tried installing Ubuntu 9.10. No succes, when installing the software it halts on ttf-mscorefonts-installer, some files are missing and the dhcp is not working. In order to have the network available I need to write the "sudo pppoeconf" command in the terminal, and that is only after I boot into Ubuntum so at this point I cannot configure the network, my provider doesn't give me an ip, they say it is only generated automatically. And with no ttf-mscorefonts-installer there is a problem with creating the grub, and there my installation stops. 
I tried both the 64bit and 32bit installer, the problem is the same.. it is related to some microsoft fonts. In the mean time I had to reinstall windows as well, because it wasn't loading any more. I am reinstalling Ubuntu 9.04 write now. I had no problems installing it previously so I hope everything will be alright.

---

### Post by aib007 on 2010-02-11
> **AutoStatic said:**
> [http://ffado.org/?q=devicesupport%2Flist&filter0=t.c.+electronic&filter1=&op2=OR&filter2](http://ffado.org/?q=devicesupport%2Flist&filter0=t.c.+electronic&filter1=&op2=OR&filter2)

The Konnekt 8 works apparently: [http://ffado.org/?q=node/78](http://ffado.org/?q=node/78)
Let's hope the Konnekt 6 is more or less the same.

For starters, could you post the outcome of **lspci** in a terminal? You can copy the outcome with Shift+Ctrl+c and then paste it with Ctrl+v. And also the outcome of **lsmod** with the Expresscard inserted.

Hi, thanks for helping me. I will post the outcome of the lspci and lsmod commands as soon as I get my system working again. It is great news though to know that the konnect 8 is working, the win driver installer is the same for konnect 6 and 8...

---

### Post by cchhrriiss121212 on 2010-02-11
> **aib007 said:**
> Hi, thanks for the links, i tried everything I could find related to my problem before asking for help on the forum. I tried installing Ubuntu 9.10. No succes, when installing the software it halts on ttf-mscorefonts-installer, some files are missing and the dhcp is not working. In order to have the network available I need to write the "sudo pppoeconf" command in the terminal, and that is only after I boot into Ubuntum so at this point I cannot configure the network, my provider doesn't give me an ip, they say it is only generated automatically. And with no ttf-mscorefonts-installer there is a problem with creating the grub, and there my installation stops. 
I tried both the 64bit and 32bit installer, the problem is the same.. it is related to some microsoft fonts. In the mean time I had to reinstall windows as well, because it wasn't loading any more. I am reinstalling Ubuntu 9.04 write now. I had no problems installing it previously so I hope everything will be alright.

I had this problem installing 9.10 as did many others. All I needed to do was have a wired internet connection plugged in when installing.

---

### Post by aib007 on 2010-02-11
Well, the problem is with my network, I use a username and password to login, it's not my choice. The installer cannot configure dhcp automatically, and in order to install it manually I need an ip, and my internet provider sais it is only generated automatically. Well, in the mean time Ubuntu 9.04 is back in my life, and here is the outcome of the lspci command: 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
03:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 03)
04:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link) (rev 01)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

and this is lsmod:

root@ubuntu:~# lsmod
Module                  Size  Used by
xt_TCPMSS              12160  1 
xt_tcpmss              10112  1 
xt_tcpudp              11008  1 
iptable_mangle         10880  1 
ip_tables              19472  1 iptable_mangle
x_tables               23428  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
pppoe                  18240  2 
pppox                  11276  1 pppoe
i915                   65668  2 
drm                    96748  3 i915
ppdev                  15620  0 
bridge                 56468  0 
stp                    10500  1 bridge
bnep                   20352  2 
input_polldev          11912  0 
lp                     17732  0 
parport                42824  2 ppdev,lp
joydev                 18496  0 
snd_usb_audio          90528  0 
snd_usb_lib            24192  1 snd_usb_audio
arc4                    9856  2 
ecb                    10752  2 
snd_hwdep              15236  1 snd_usb_audio
snd_hda_intel         435508  2 
snd_seq_dummy          10756  0 
snd_seq_oss            38272  0 
rtl8187                53504  0 
snd_seq_midi           14336  0 
snd_pcm_oss            46464  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_rawmidi            29440  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_pcm                82436  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
mac80211              219896  1 rtl8187
snd_seq                57456  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                62484  0 
iTCO_wdt               19152  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29444  2 snd_pcm,snd_seq
serio_raw              13444  0 
eeprom_93cx6           10240  1 rtl8187
pcspkr                 10496  0 
iTCO_vendor_support    11652  1 iTCO_wdt
usbhid                 42592  0 
snd                    63140  16 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
cfg80211               38160  2 rtl8187,mac80211
soundcore              15584  1 snd
shpchp                 40596  0 
asus_laptop            24568  0 
intel_agp              34236  1 
video                  25360  0 
led_class              12036  1 asus_laptop
agpgart                42960  3 drm,intel_agp
output                 11008  1 video
8139too                32128  0 
8139cp                 27648  0 
mii                    13312  2 8139too,8139cp
ohci1394               38832  0 
ieee1394               95932  1 ohci1394
fbcon                  46368  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


I hope it makes some sense to you more than it does to me.

---

### Post by aib007 on 2010-02-11
And this is when the Expresscard is not plugged in:

root@ubuntu:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

and lsmod:
root@ubuntu:~# lsmod
Module                  Size  Used by
xt_TCPMSS              12160  1 
xt_tcpmss              10112  1 
xt_tcpudp              11008  1 
iptable_mangle         10880  1 
ip_tables              19472  1 iptable_mangle
x_tables               23428  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
pppoe                  18240  2 
pppox                  11276  1 pppoe
i915                   65668  2 
drm                    96748  3 i915
ppdev                  15620  0 
bridge                 56468  0 
stp                    10500  1 bridge
bnep                   20352  2 
input_polldev          11912  0 
lp                     17732  0 
parport                42824  2 ppdev,lp
joydev                 18496  0 
snd_usb_audio          90528  0 
snd_usb_lib            24192  1 snd_usb_audio
arc4                    9856  2 
ecb                    10752  2 
snd_hwdep              15236  1 snd_usb_audio
snd_hda_intel         435508  2 
snd_seq_dummy          10756  0 
snd_seq_oss            38272  0 
rtl8187                53504  0 
snd_seq_midi           14336  0 
snd_pcm_oss            46464  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_rawmidi            29440  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_pcm                82436  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
mac80211              219896  1 rtl8187
snd_seq                57456  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                62484  0 
iTCO_wdt               19152  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29444  2 snd_pcm,snd_seq
serio_raw              13444  0 
eeprom_93cx6           10240  1 rtl8187
pcspkr                 10496  0 
iTCO_vendor_support    11652  1 iTCO_wdt
usbhid                 42592  0 
snd                    63140  16 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
cfg80211               38160  2 rtl8187,mac80211
soundcore              15584  1 snd
shpchp                 40596  0 
asus_laptop            24568  0 
intel_agp              34236  1 
video                  25360  0 
led_class              12036  1 asus_laptop
agpgart                42960  3 drm,intel_agp
output                 11008  1 video
8139too                32128  0 
8139cp                 27648  0 
mii                    13312  2 8139too,8139cp
ohci1394               38832  0 
ieee1394               95932  1 ohci1394
fbcon                  46368  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by AutoStatic on 2010-02-11
> **aib007 said:**
> root@ubuntu:~#Did you enable the root account or did you use **sudo -s**? I hope the latter, if not, I would personally advise disabling the root account again.

> **aib007 said:**
> 04:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link) (rev 01)

...

ohci1394               38832  0 
ieee1394               95932  1 ohci1394The Firewire Expresscard is being recognised and the kernel module is loaded too. Did you go through these steps here: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) ?

---

### Post by aib007 on 2010-02-11
Hi. ;) sudo -s. 
Ok. I will tell you exactly what I did. 
First I enabled access to raw1394, (and also ticked the other boxes in Ubuntu Studio Controls)
Then I enabled sudo adduser <username> video;  sudo adduser <username> audio was already enabled. 
Then with sudo gedit /etc/udev/rules.d/65-permission-raw.rules it opend a blank file, i pasted KERNEL=="raw1394", OWNER="root", GROUP="video", MODE="660" into it and saved it.
When it typed sudo apt-get install ffado-dbus-server ffado-mixer-qt4 ffado-tools libffado1 ---- it said :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffado-dbus-server is already the newest version.
ffado-mixer-qt4 is already the newest version.
ffado-tools is already the newest version.
E: Couldn't find package libffado1

Then I under User Settings Account Properties I wanted to give access to my user, but audio was already enabled.
To this command ---- ls -al /dev/raw1394 ---- i get the response: 
crw-rw---- 1 root video 171, 0 2010-02-11 18:54 /dev/raw1394

to groups:
aib007 adm dialout cdrom tape audio video plugdev lpadmin netdev admin sambashare

Then I started jack, hw:0 interface, ... other options are plughw:0, /dev/audio, /dev/dsp
I saved, restarted and this is the outcome:
   p, li { white-space: pre-wrap; }  [COLOR=#990099]19:48:13.749 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]19:48:14.151 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]19:48:14.152 JACK is starting...[/COLOR]
 [COLOR=#990099]19:48:14.152 /usr/bin/jackd -R -dfirewire -dhw:0 -r48000 -p128 -n2 -i2 -o2[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 [COLOR=#999999]19:48:14.209 JACK was started with PID=15074.[/COLOR]
 loading driver ..
 03225952043:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 00:53:39
 03226189933: [31mError (bebob_avdevice.cpp)[  96] probe: Number of channels command failed
 [0m03226242779: [31mError (avc_avdevice.cpp)[  88] probe: Subunit info command failed
 [0mfirewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns
 [COLOR=#999999]19:48:14.880 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]19:48:14.881 Post-shutdown script...[/COLOR]
 [COLOR=#990099]19:48:14.882 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]19:48:15.300 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]19:48:16.424 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

### Post by AutoStatic on 2010-02-11
Looks good already. Two things:
- Try adding 'raw1394' to */etc/modules*
- Use '(default)' as the Interface, not 'plughw:0'. 'plughw:0' is an ALSA designation and Firewire uses FFADO, not ALSA.

---

### Post by aib007 on 2010-02-11
Well, raw1394 is already in /etc/modules.

I changed to default in Jack.

 p, li { white-space: pre-wrap; }  [COLOR=#999999]20:35:25.913 Startup script...[/COLOR]
 [COLOR=#990099]20:35:25.918 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]20:35:26.348 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]20:35:26.349 JACK is starting...[/COLOR]
 [COLOR=#990099]20:35:26.349 /usr/bin/jackd -R -dfirewire -r48000 -p128 -n2 -i2 -o2[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 [COLOR=#999999]20:35:26.394 JACK was started with PID=21873.[/COLOR]
 loading driver ..
 00588312100:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 00:53:39
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns
 [COLOR=#999999]20:35:26.835 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]20:35:26.836 Post-shutdown script...[/COLOR]
 [COLOR=#990099]20:35:26.839 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]20:35:27.253 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]20:35:28.577 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

I also installed libffado-dev ... I suppose it is the latest ffado

---

### Post by aib007 on 2010-02-11
I was just thinking that maybe updating the ffado driver with a newer one would help. But i can't find it :

aib007@ubuntu:~$ sudo apt-get install libffado1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libffado1

aib007@ubuntu:~$ sudo apt-get install libffado2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libffado2

---

### Post by aib007 on 2010-02-11
Or is an update not possible without a kernel update, i'm confused.

---

### Post by AutoStatic on 2010-02-11
You don't need to update. Karmic comes with libffado0 which is actually version 1.999 or something and you should be ok with that. But I now see you're on Jaunty, right? And even though you say raw1394 is in */etc/modules* I don't see it in the output of lsmod. Could you post your */etc/modules*? And the outcome of **ffado-test ListDevices** ?

---

### Post by aib007 on 2010-02-12
Hi, please excuse me for taking me so long to reply. I live in Bucharest, and last evening we had Air here, and I really wanted to see them, it was the first time I had this opportunity.
I think we might get it working, (actually you) :)

Here is ListDevices:
=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x000166040900170f  0x00000166  0x00000024   TC Electronic - DesktopKonnekt6
   1       0x010203040000078e  0x00010203  0x00000000   Linux - ohci1394  - 
no message buffer overruns

And etc/modules --- i'm not sure if it helps but there is no folder modules in /etc just this "document"
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
raw1394
lp

Thanks again, A

---

### Post by AutoStatic on 2010-02-12
> **aib007 said:**
> Hi, please excuse me for taking me so long to reply. I live in Bucharest, and last evening we had Air here, and I really wanted to see them, it was the first time I had this opportunity.
I think we might get it working, (actually you) :)No probs, besides, Air is cool.

> **aib007 said:**
> === 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x000166040900170f  0x00000166  0x00000024   TC Electronic - DesktopKonnekt6It's being properly recognised, that's hopeful. Now see if we can get it to work... 8-[

> **aib007 said:**
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
raw1394
lp*/etc/modules* is a file and raw1394 is in it but it doesn't get loaded, at least, it doesn't show up with **lsmod**.
What if you do it manually with **sudo modprobe raw1394** ? Does that return any errors? If not what does **lsmod | grep 1394** report?

---

### Post by aib007 on 2010-02-12
Yep, they are really good. And it was amazing to see 3 people with, well probably the best of all times, analog synths, four different guitars and a drum set make all the music you know.. really cool.
Back to the subject, in the mean time i read a little bit here, [http://ffado.org/?q=node/54](http://ffado.org/?q=node/54) and realized that the rule who gives permission to raw on my system had this content 
KERNEL=="raw1394", OWNER="root", GROUP="video", MODE="660"

and I changed it - I replaced "video" with "audio", and deleted Mode="660"

and reloaded the rules. Now the lsmod | grep 1394 shows this:

root@ubuntu:~# lsmod | grep raw1394
raw1394                33116  0 
ieee1394               95932  2 raw1394,ohci1394

---

### Post by AutoStatic on 2010-02-12
> **aib007 said:**
> Yep, they are really good. And it was amazing to see 3 people with, well probably the best of all times, analog synths, four different guitars and a drum set make all the music you know.. really cool.Yeah, the French got their stuff together, Phoenix, Air, Justice, Daft Punk... All amazing.

> **aib007 said:**
> Back to the subject, in the mean time i read a little bit here, [http://ffado.org/?q=node/54](http://ffado.org/?q=node/54) and realized that the rule who gives permission to raw on my system had this content 
KERNEL=="raw1394", OWNER="root", GROUP="video", MODE="660"

and I changed it - I replaced "video" with "audio", and deleted Mode="660"That shouldn't make any difference concerning the loading of the raw1394 module. The udev rule takes care of the permissions. Now the group owner will be audio instead of video. But you're a member of both groups so you're allowed to use the /dev/raw1394 device node either way around.

But what has JACK to say?

---

### Post by aib007 on 2010-02-12
Well no change with Jack:
 p, li { white-space: pre-wrap; }  loading driver ..
 00109289393:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 00:53:39
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns

and lsmod | grep raw 1394 after reboot:
raw1394                33116  0 
ieee1394               95932  2 raw1394,ohci1394
actually it's the same, well when video was the group owner i think it also listed ohci1394 between raw1394 and ieee1394

---

### Post by AutoStatic on 2010-02-12
> **aib007 said:**
>  firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewireIn most cases this means that there's something wrong with the raw1394 module as far as I know. Either the rights are not set properly or it didn't get loaded at all. But in your case the module is loaded so it has to be a permissions problem. What are the permissions of */dev/raw1394* now?

---

### Post by aib007 on 2010-02-12
Hi, I am not sure how this should be done, because previously I told you I am in the group audio and video.
aib007@ubuntu:~$ sudo adduser aib007 audio
The user `aib007' is already a member of `audio'.
aib007@ubuntu:~$ sudo adduser aib007 video
The user `aib007' is already a member of `video'.

However, I wasn't shore if the groups actually existed, so what I did -- in User Settings, Manage Groups, i with +Add Group i added audio and video to the list, I don't know if it was necessary. And now Jack shows this:
 p, li { white-space: pre-wrap; }  loading driver ..
 01502708482:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 00:53:39
 01502712824: [31mError (ieee1394service.cpp)[ 163] detectNbPorts: Could not get libraw1394 handle.
 This usually means:
  a) The device-node /dev/raw1394 doesn't exists because you don't have a
     (recognized) firewire controller.
   b) The modules needed aren't loaded. This is not in the scope of ffado but of
     your distribution, so if you have a firewire controller that should be
     supported and the modules aren't loaded, file a bug with your distributions
     bug tracker.
   c) You don't have permissions to access /dev/raw1394. 'ls -l /dev/raw1394'
     shows the device-node with its permissions, make sure you belong to the
     right group and the group is allowed to access the device.
 [0mfirewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire

in in the Terminal ffado-dbus-server:
02017562613:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
02017563836: Error (ieee1394service.cpp)[ 163] detectNbPorts: Could not get libraw1394 handle.
This usually means:
 a) The device-node /dev/raw1394 doesn't exists because you don't have a
    (recognized) firewire controller.
  b) The modules needed aren't loaded. This is not in the scope of ffado but of
    your distribution, so if you have a firewire controller that should be
    supported and the modules aren't loaded, file a bug with your distributions
    bug tracker.
  c) You don't have permissions to access /dev/raw1394. 'ls -l /dev/raw1394'
    shows the device-node with its permissions, make sure you belong to the
    right group and the group is allowed to access the device.
02017563851: Fatal (devicemanager.cpp)[ 161] initialize: Failed to detect the number of 1394 adapters. Is the IEEE1394 stack loaded (raw1394)?
02017563861: Error (ffado-dbus-server.cpp)[ 276] main: Could not initialize device manager
02017563907: Debug (ffado-dbus-server.cpp)[ 201] exitfunction: Debug output flushed...
no message buffer overruns

---

### Post by aib007 on 2010-02-12
permissions are:

aib007@ubuntu:~$ ls -al /dev/raw1394
crw-rw---- 1 root video 171, 0 2010-02-12 13:14 /dev/raw1394

---

### Post by AutoStatic on 2010-02-12
According to [http://ubuntuforums.org/showpost.php?p=8814319&postcount=18](http://ubuntuforums.org/showpost.php?p=8814319&postcount=18) you set the group to 'audio' and now it's 'video' again. It's getting a bit confusing :)

---

### Post by aib007 on 2010-02-12
It's ok. I left inside the rules only KERNEL=="raw1394", GROUP="audio"
and now it's 
aib007@ubuntu:~$ ls -al /dev/raw1394
crw-rw---- 1 root audio 171, 0 2010-02-12 15:57 /dev/raw1394

ffado-dbus-server:

02211207049:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
02211209060: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000018, length = 1
02211209133: Warning (ieee1394service.cpp)[ 328] initialize: Could not set SPLIT_TIMEOUT to min requested (1000000)
02211209164: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000018, length = 1
02211209202: Warning (ieee1394service.cpp)[ 332] initialize: Set SPLIT_TIMEOUT to min requested (1000000) did not succeed
02211211184: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
02211211281: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
02211211308: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
02211211341: Debug (Element.cpp)[ 121] show: Element DeviceManager
02211211362: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
02211211463:  (ffado-dbus-server.cpp)[ 312] main:  Starting DBUS service...
02211216424:  (ffado-dbus-server.cpp)[ 328] main:  Running... (press ctrl-c to stop & exit)
02211216561: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...

and Jack:

 p, li { white-space: pre-wrap; }  loading driver ..
 02326178308:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 00:53:39
 firewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns

---

### Post by aib007 on 2010-02-12
I think this might make more sense, after i loaded raw1394 module again,
=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x000166040900170f  0x00000166  0x00000024   TC Electronic - DesktopKonnekt6
   1       0x010203040000078e  0x00010203  0x00000000   Linux - ohci1394  - 

I got this output from ffado-dbus-server:

02771748093:  (ffado-dbus-server.cpp)[ 269] main:  Discovering devices...
02771751302: Debug (devicemanager.cpp)[ 332] discover: Starting discovery...
02771784450: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
02771786837: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
02771789101: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
02771791349: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
02771793602: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
02771841432: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
02771843811: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
02771846558: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
02771848811: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
02771851071: Debug (ieee1394service.cpp)[ 521] readNoLock: raw1394_read failed: node 0xFFC0, addr = 0x0000FFFFF0000480, length = 16
02771899910: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
02771899932: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
02771899940: Error (bebob_avdevice.cpp)[  96] probe: Number of channels command failed
02771926094: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
02771926129: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
02771947485: Error (ieee1394service.cpp)[ 702] doFcpTransaction: FCP transaction didn't succeed in 20 tries
02771947507: Warning (ieee1394service.cpp)[ 677] transactionBlock: FCP transaction failed
02771947515: Error (avc_avdevice.cpp)[  88] probe: Subunit info command failed
02771947545: Debug (devicemanager.cpp)[ 639] discover: Discovery finished...
02771947551: Debug (devicemanager.cpp)[1087] showDeviceInfo: ===== Device Manager =====
02771947558: Debug (Element.cpp)[ 121] show: Element DeviceManager
02771947562: Debug (devicemanager.cpp)[1095] showDeviceInfo: --- IEEE1394 Service  0 ---
Iso handler info:
Dumping IsoHandlerManager Stream handler information...
 State: 2
02771947619:  (ffado-dbus-server.cpp)[ 312] main:  Starting DBUS service...
02771953614:  (ffado-dbus-server.cpp)[ 328] main:  Running... (press ctrl-c to stop & exit)
02771953634: Debug (ffado-dbus-server.cpp)[ 331] main: dispatching...
^C02971235653: Debug (ffado-dbus-server.cpp)[ 334] main:  dispatcher exited...
02971235685: Debug (ffado-dbus-server.cpp)[ 336] main:  activity handled...
02971235704:  (ffado-dbus-server.cpp)[ 339] main:  Stopping...
02971351446:  (ffado-dbus-server.cpp)[ 353] main:  Bye.
02971351465: Debug (ffado-dbus-server.cpp)[ 201] exitfunction: Debug output flushed...
no message buffer overruns

and Jack:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]16:44:13.654 JACK was started with PID=29813.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 02793589049:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.40- built Feb 24 2009 00:53:39
 02793811491: [31mError (bebob_avdevice.cpp)[  96] probe: Number of channels command failed
 [0m02793855272: [31mError (avc_avdevice.cpp)[  88] probe: Subunit info command failed
 [0mfirewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns

---

### Post by AutoStatic on 2010-02-12
That looks better. Apparently FFADO has difficulties reading the number of channels. This is either because your device is not fully supported by the FFADO drivers you're using or because something else is in the way. Could you post the outcome of **cat /proc/interrupts** ?

---

### Post by aib007 on 2010-02-12
here it is:

           CPU0       CPU1       
  0:        505          7   IO-APIC-edge      timer
  1:       1724       1752   IO-APIC-edge      i8042
  8:          0          1   IO-APIC-edge      rtc0
  9:       3344       3302   IO-APIC-fasteoi   acpi
 12:     205045     205406   IO-APIC-edge      i8042
 14:      23359      23612   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:       2776       2754   IO-APIC-fasteoi   uhci_hcd:usb3, eth0
 18:    3587115    3586743   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7, ohci1394
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb6
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:       3157       3148   IO-APIC-fasteoi   HDA Intel
 23:          0          0   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
2299:      48082      47616   PCI-MSI-edge      i915@pci:0000:00:02.0
2300:       6243       6063   PCI-MSI-edge      ahci
2301:          0          0   PCI-MSI-edge      pciehp
NMI:          0          0   Non-maskable interrupts
LOC:    4777624    4655192   Local timer interrupts
RES:    1077345    1377585   Rescheduling interrupts
CAL:        898       1070   Function call interrupts
TLB:     448474     416832   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

---

### Post by AutoStatic on 2010-02-12
Looks ok, are you using any USB devices that might interfere?
And it's not your Firewire Expresscard, that one is fully supported: [http://ubuntuforums.org/showthread.php?t=1373579](http://ubuntuforums.org/showthread.php?t=1373579)

---

### Post by aib007 on 2010-02-12
I had a usb connected to the midi keyboard but the controller itself was not on. I unplugged it but there is no change.

---

### Post by aib007 on 2010-02-12
I've been reading about how to complie ffado from source. It doesn't seem to be to difficult. And on this page [http://subversion.ffado.org/wiki/CompileAndInstallFfado](http://subversion.ffado.org/wiki/CompileAndInstallFfado) I noticed there is an option which says enable dice, and this is the chip tc uses. Maybe I have to compile it from source in order to get it working?

---

### Post by AutoStatic on 2010-02-12
Then I fear you need a newer version of FFADO. You're on Jaunty right? Maybe it's an option to install Karmic, I wouldn't do an upgrade. Or maybe it's possible to just upgrade FFADO.

Edit: you could try compiling it from source. Make sure you remove libffado before doing **scons install** (see Warning #2). And also check if the sources come with a **scons uninstall** option, just in case things go wrong that might come in handy.

---

### Post by aib007 on 2010-02-12
Thanks a lot for being this patient all this time. I tried installing Karmic, unsuccessful however. Installation halted when installing ttf-mscorefonts I cannot establish internet access. It cannot load dhcp  and the installer needs internet connection to download the ttf-mscorefonts. I called the internet provider to find out what the ip, dns are, and they said it is generated automatically, and I have to use a password and username. After reinstalling Jaunty, I checked the ip within the terminal, but i'm not sure if it would work on the installer, if the dhcp cannot be found. And if I succeed installing it, is the ffado driver updated or would I still have to compile from source.. what do you think?

---

### Post by trulan on 2010-02-12
You could try installing ffado from this ppa - this is for Jaunty but looks like a good upgrade. [https://launchpad.net/~frasten/+archive/ppa?field.series_filter=jaunty](https://launchpad.net/~frasten/+archive/ppa?field.series_filter=jaunty)

---

### Post by AutoStatic on 2010-02-12
> **trulan said:**
> You could try installing ffado from this ppa - this is for Jaunty but looks like a good upgrade. [https://launchpad.net/~frasten/+archive/ppa?field.series_filter=jaunty](https://launchpad.net/~frasten/+archive/ppa?field.series_filter=jaunty)Ah the frasten PPA has it. I'm with trulan, I would try giving that a go.
And concerning your network issue, it's a bug in the installer of Ubuntu Studio 9.10. You could work around it by installing a plain Karmic and install Ubuntu Studio on top of that or by retrying installing Ubuntu Studio a couple of times. If I'm correct the bug consists of the fact that the installer wants to download the actual fonts from the internet but it sometimes uses wrong or non-existent mirrors where those fonts reside.

---

### Post by MIJ-VI on 2010-07-14
> **aib007 said:**
> Thanks a lot for being this patient all this time. _I tried installing Karmic, unsuccessful however. Installation halted when installing ttf-mscorefonts I cannot establish internet access. It cannot load dhcp  and the installer needs internet connection to download the ttf-mscorefonts._ I called the internet provider to find out what the ip, dns are, and they said it is generated automatically, and I have to use a password and username. After reinstalling Jaunty, I checked the ip within the terminal, but i'm not sure if it would work on the installer, if the dhcp cannot be found. And if I succeed installing it, is the ffado driver updated or would I still have to compile from source.. what do you think?

Hi aib007.

'Half a year too late but the [OP in this thread]("http://www.talkbass.com/forum/showthread.php?t=599271") explains one way how to install Ubuntu Studio 9.10 on a PC which doesn't have an Internet connection.

BTW. What kind of chip controls the express card slot in your notebook? (I've read that express card slot chips made by Agere Systems Inc. aren't good for digital audio but ones made by Intel are.)

---

