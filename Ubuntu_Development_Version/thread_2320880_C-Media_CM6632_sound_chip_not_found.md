---
title: "C-Media CM6632 sound chip not found"
date: 2016-04-18
forum: Ubuntu Development Version
---

### Post by Arlen_B_Taylor on 2016-04-18
I recently loaded Kubuntu 16.04 64bit onto computer with a MSI Z170A Gaming M9 ACK motherboard.  The audio on board is the CMedia Extreme Audio DAC.  Their website says that on support for Linux kernel 2.65 and later. I see that this audio chip is found on video cards and motherboards with Linux support.  I am not getting any sound out of the audio ports.  There is some sound that is passing through my hdmi port to my terminal, but I don't want to use that, I need to use the audio ports.  I need to find the drivers.

---

### Post by Yellow Pasque on 2016-04-19
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Arlen_B_Taylor on 2016-05-14
This is what came up from the ALSA Information Script:

```
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Sat May 14 18:52:03 UTC 2016


!!Linux Distribution
!!------------------

Ubuntu Yakkety Yak (development branch) \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu Yakkety Yak (development branch)" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 16.10" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/" UBUNTU_CODENAME=yakkety


!!DMI Information
!!---------------

Manufacturer:      MSI
Product Name:      MS-7966
Product Version:   1.0
Firmware Version:  1.40


!!Kernel Information
!!------------------

Kernel release:    4.4.0-22-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.4.0-22-generic
Library version:    1.1.0
Utilities version:  1.1.0


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xdfe60000 irq 332


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1f.3 0403: 8086:a170 (rev 31)
	Subsystem: 1462:d976
--
01:00.1 0403: 1002:aab0
	Subsystem: 1043:aab0


!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100300
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02
Node 0x04 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  2 May 13 20:34 /dev/snd/controlC1
crw-rw----  1 root audio 116,  4 May 13 20:34 /dev/snd/hwC1D0
crw-rw----  1 root audio 116,  3 May 14 12:38 /dev/snd/pcmC1D3p
crw-rw----  1 root audio 116,  1 May 13 20:34 /dev/snd/seq
crw-rw----  1 root audio 116, 33 May 13 20:34 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May 13 20:34 .
drwxr-xr-x 3 root root 160 May 13 20:34 ..
lrwxrwxrwx 1 root root  12 May 13 20:34 pci-0000:01:00.1 -> ../controlC1


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card 1 [HDMI]

Card hw:1 'HDMI'/'HDA ATI HDMI at 0xdfe60000 irq 332'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100300'
  Controls      : 7
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.HDMI {
	control.1 {
		iface CARD
		name 'HDMI/DP,pcm=3 Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.5 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface PCM
		device 3
		name ELD
		value '100005000010000100000000000000000000000009070700'
		comment {
			access 'read volatile'
			type BYTES
			count 24
		}
	}
	control.7 {
		iface PCM
		device 3
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
md4
nls_utf8
cifs
fscache
rfcomm
xt_CHECKSUM
iptable_mangle
ipt_MASQUERADE
nf_nat_masquerade_ipv4
iptable_nat
nf_nat_ipv4
nf_nat
nf_conntrack_ipv4
nf_defrag_ipv4
xt_conntrack
nf_conntrack
ipt_REJECT
nf_reject_ipv4
xt_tcpudp
bridge
stp
llc
ebtable_filter
ebtables
ip6table_filter
ip6_tables
iptable_filter
ip_tables
x_tables
pl2303
usbserial
bnep
binfmt_misc
joydev
input_leds
btusb
btrtl
arc4
nls_iso8859_1
8250_dw
i2c_designware_platform
i2c_designware_core
ath10k_pci
ath10k_core
ath
mac80211
i915_bpo
cfg80211
snd_hda_codec_hdmi
intel_ips
snd_hda_intel
snd_hda_codec
snd_hda_core
snd_hwdep
snd_pcm
intel_rapl
x86_pkg_temp_thermal
intel_powerclamp
coretemp
crct10dif_pclmul
crc32_pclmul
aesni_intel
aes_x86_64
lrw
gf128mul
snd_seq_midi
glue_helper
snd_seq_midi_event
ablk_helper
cryptd
snd_rawmidi
snd_seq
snd_seq_device
snd_timer
snd
soundcore
serio_raw
hci_uart
idma64
btbcm
btqca
virt_dma
btintel
bluetooth
mei_me
shpchp
mei
intel_lpss_pci
intel_lpss_acpi
intel_lpss
acpi_als
kfifo_buf
mac_hid
industrialio
acpi_pad
cuse
kvm_intel
kvm
irqbypass
parport_pc
ppdev
lp
parport
autofs4
hid_logitech
ff_memless
hid_generic
usbhid
uas
usb_storage
mxm_wmi
amdkfd
amd_iommu_v2
radeon
i2c_algo_bit
ttm
psmouse
drm_kms_helper
syscopyarea
sysfillrect
sysimgblt
alx
fb_sys_fops
ahci
mdio
drm
libahci
i2c_hid
hid
wmi
video
pinctrl_sunrisepoint
pinctrl_intel
fjes


!!Sysfs Files
!!-----------

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x185600f0
0x05 0x585600f0

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D0/hints:


!!ALSA/HDA dmesg
!!--------------

[    2.121454] [drm] Connector 0:
[    2.121454] [drm]   HDMI-A-1
[    2.121455] [drm]   HPD1
--
[    9.088784] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.088807] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    9.088911] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[    9.088912] snd_hda_intel 0000:01:00.1: Force to non-snoop mode
[    9.108622] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[    9.108981] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    9.135937] snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)
[    9.139238] snd_hda_intel 0000:00:1f.3: no codecs found!
[    9.148401] ath10k_pci 0000:04:00.0: enabling device (0000 -> 0002)
```


I don't find any mention of CM6632A.  I did find a datasheet at:  [http://www.arrivalelectronics.co.uk/uploads/files/46043CM6632A_Datasheet_v1.2.pdf](http://www.arrivalelectronics.co.uk/uploads/files/46043CM6632A_Datasheet_v1.2.pdf)

It states that CM6632A is a high-speed USB 2.0 high-speed audio processor that supports the latest USB Audio Device. This chip is 
located on the motherboard, for what it's worth. I am not sure what to do from here.

---

### Post by Yellow Pasque on 2016-05-14
```
[ 9.135937] snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)
[ 9.139238] snd_hda_intel 0000:00:1f.3: no codecs found!
```

---

### Post by howefield on 2016-05-15
Thread moved to the "*Ubuntu Development Version*" forum and code tags inserted to post.

---

### Post by Rustan on 2016-05-15
C-Media CM6632 USB chip not showing up
[http://www.spinics.net/lists/linux-usb/msg135659.html](http://www.spinics.net/lists/linux-usb/msg135659.html)

and
lsusb hangs
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1534856](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1534856)

It works fin on an older 3.12 kernel

---

