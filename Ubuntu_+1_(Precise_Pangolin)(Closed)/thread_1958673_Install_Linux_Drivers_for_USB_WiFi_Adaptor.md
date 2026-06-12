---
title: "Install Linux Drivers for USB WiFi Adaptor"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mjhatten on 2012-04-14
I just bought a new USB WiFi adaptor.  It came with Linux drivers but I havent got a clue how to install them.  Here are the instructions from Readme file.  I'm a newby so I don't have a clue what to do.

Description:
=============
This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.


=======================================================================
Contents:
=============
Makefile	        : Makefile
*.c					: c files
*.h					: header files


=======================================================================
Features:
==========
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with 
   open or shared or WPA-PSK or WPA2-PSK authentication method. 
   NONE, WEP, TKIP and AES encryption. 


=======================================================================
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2870sta
	

Help......

---

### Post by theknightlinux on 2012-04-14
Hi there. Do you have Ubuntu 11.10 installed?

---

### Post by mebomechanicno1 on 2012-04-14
Yes, what version are you using and what also is the make and model of the wifi adapter?

---

### Post by mjhatten on 2012-04-14
I'm running 12.04.

Here is the data on the adaptor:


=======================================================================
ModelName:
===========
RT2870 Wireless Lan Linux Driver


=======================================================================
Driver lName:
===========
rt2870.o/rt2870.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Ralink Hardware:
===================
Ralink 802.11n Wireless LAN Card.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.

---

### Post by sandyd on 2012-04-14
> **mjhatten said:**
> I'm running 12.04.

Here is the data on the adaptor:


=======================================================================
ModelName:
===========
RT2870 Wireless Lan Linux Driver


=======================================================================
Driver lName:
===========
rt2870.o/rt2870.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Ralink Hardware:
===================
Ralink 802.11n Wireless LAN Card.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.
RT2870 should be supported since Jaunty
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/326621](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/326621)

Please post the output of:
Unity Dash -> Type in 'terminal' -> enter 'lsmod' in terminal

---

### Post by mjhatten on 2012-04-14
michael@michael-AOD255:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
uas                    18027  0 
usb_storage            49198  1 
joydev                 17693  0 
snd_hda_codec_realtek   223867  1 
rt2800usb              22684  0 
rt2800lib              58925  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
rt2x00usb              20762  1 rt2800usb
snd_seq_midi           13324  0 
rt2x00lib              55301  3 rt2800usb,rt2800lib,rt2x00usb
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
rfcomm                 47604  0 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
bluetooth             180104  10 rfcomm,bnep
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
arc4                   12529  2 
psmouse                87603  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
ath9k                 132390  0 
serio_raw              13211  0 
v4l2_compat_ioctl32    17128  1 videodev
mac80211              506816  4 rt2800lib,rt2x00usb,rt2x00lib,ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
i915                  468651  2 
cfg80211              205544  4 rt2x00lib,ath9k,mac80211,ath
binfmt_misc            17540  1 
drm_kms_helper         46978  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   242038  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
mac_hid                13253  0 
video                  19596  1 i915
wmi                    19256  1 acer_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41717  0 
michael@michael-AOD255:~$ ^C

---

### Post by theknightlinux on 2012-04-14
[SIZE=2][COLOR=Black]I believe you just need to enable the driver for your USB Adapter. Open up a terminal and type:

sudo modprobe rt2870sta or just: sudo modprobe rt2870 

Then type: gksudo gedit /etc/modules

A text editor should open up, at the end just type rt2870sta and then save it, close it and restart your computer.[/COLOR][/SIZE][SIZE=3][COLOR=#0000FF]
[/COLOR][/SIZE]

---

### Post by mjhatten on 2012-04-14
Got a "module not found" message on both modprobe commands.  But .... the unit appears to be working.  I was fooled because I used a <FN> + F3 to shut off the internal radio and it shut off the unit radio, too.  I turned the radios back on and got two connections.  I chose the Ralink Connection and disconnected the internal (Atheros) connection and am using it right now.  The only issue seems to be the power indicator.  It shows 30% but under Windows I see 100%.  That problem is for another day.

---

