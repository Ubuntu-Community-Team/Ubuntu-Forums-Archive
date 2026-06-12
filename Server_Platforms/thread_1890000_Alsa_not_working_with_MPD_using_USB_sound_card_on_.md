---
title: "Alsa not working with MPD using USB sound card on Ubuntu Server 64bit"
date: 2011-12-02
forum: Server Platforms
---

### Post by jwkite on 2011-12-02
I have had the same setup for over two years, and it has worked successfully. Now, however, I cannot make my system work as expected.

I am running MPD on a headless 64bit server. I recently upgraded to 11.10, but this setup failed just prior to the upgrade. The output of the audio is running through a wireless transmitter that is an external USB sound card. I have tested the transmitter on my desktop and it works perfectly. However, I cannot get it to work on the server. Either I have a problem with Alsa or my configuration in MPD is incorrect.

Pertinent section from MPD configuration file:

audio_output {
        type "alsa"
        name "My ALSA Device"
        device "hw:0,0" # optional
        #format "44100:16:2" # optional
        #mixer_device "default" # optional
        #mixer_control "PCM" # optional
        #mixer_index "0" # optional
}

Output of alsa info script:

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Wed Nov 30 05:36:06 UTC 2011

!!Linux Distribution
!!------------------

Ubuntu 11.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.10"

!!DMI Information
!!---------------

Manufacturer: Supermicro
Product Name: C2SBA
Product Version: 0123456789

!!Kernel Information
!!------------------

Kernel release: 3.0.0-13-server
Operating System: GNU/Linux
Architecture: x86_64
Processor: x86_64
SMP Enabled: Yes

!!ALSA Version
!!------------

Driver version: 1.0.24
Library version: 1.0.24.1
Utilities version: 1.0.24.2

!!Loaded ALSA modules
!!-------------------

snd_usb_audio

!!Sound Servers on this system
!!----------------------------

No sound servers found.

!!Soundcards recognised by ALSA
!!-----------------------------

 1 [L2000 ]: USB-Audio - Lyra Wireless 2.0.00
                      Thomson multimedia, Inc. Lyra Wireless 2.0.00 at usb-0000:00:1d.1-1, full speed

!!PCI Soundcards installed in the system
!!--------------------------------------

!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: model=generic

!!Loaded sound module options
!!--------------------------

!!Module: snd_usb_audio
 async_unlink : Y
 device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
 enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
 id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
 ignore_ctl_error : N
 index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
 nrpacks : 8
 pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
 vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1

!!USB Mixer information
!!---------------------------
--startcollapse--

USB Mixer: usb_id=0x069b3008, ctrlif=0, ctlerr=0
Card: Thomson multimedia, Inc. Lyra Wireless 2.0.00 at usb-0000:00:1d.1-1, full speed
  Unit: 7
    Control: name="Tone Control - Treble", index=0
    Info: id=7, control=5, cmask=0x0, channels=1, type="S8"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 7
    Control: name="Tone Control - Bass", index=0
    Info: id=7, control=3, cmask=0x0, channels=1, type="S8"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 7
    Control: name="PCM Playback Volume", index=0
    Info: id=7, control=2, cmask=0x3, channels=2, type="S16"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 7
    Control: name="PCM Playback Switch", index=0
    Info: id=7, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--

!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116, 3 Nov 30 00:25 /dev/snd/controlC1
crw-rw---- 1 root audio 116, 2 Nov 30 00:25 /dev/snd/pcmC1D0p
crw-rw---- 1 root audio 116, 1 Nov 30 00:25 /dev/snd/seq
crw-rw---- 1 root audio 116, 33 Nov 30 00:25 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root 60 Nov 30 00:25 .
drwxr-xr-x 4 root root 160 Nov 30 00:25 ..
lrwxrwxrwx 1 root root 12 Nov 30 00:25 usb-Thomson_multimedia__Inc._Lyra_Wireless_2.0.00-00 -> ../controlC1

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 60 Nov 30 00:25 .
drwxr-xr-x 4 root root 160 Nov 30 00:25 ..
lrwxrwxrwx 1 root root 12 Nov 30 00:25 pci-0000:00:1d.1-usb-0:1:1.0 -> ../controlC1

!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:240: no soundcards found...

ARECORD

arecord: device_list:240: no soundcards found...

!!Amixer output
!!-------------

!!-------Mixer controls for card 1 [L2000]

Invalid card number.
Usage: amixer <options> [command]

Available options:
  -h,--help this help
  -c,--card N select the card
  -D,--device N select the device, default 'default'
  -d,--debug debug mode
  -n,--nocheck do not perform range checking
  -v,--version print version of this program
  -q,--quiet be quiet
  -i,--inactive show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin Read and execute commands from stdin sequentially

Available commands:
  scontrols show all mixer simple controls
  scontents show contents of all mixer simple controls (default command)
  sset sID P set contents for one mixer simple control
  sget sID get contents for one mixer simple control
  controls show all controls for given card
  contents show contents of all controls for given card
  cset cID P set control contents for one control
  cget cID get control contents for one control
Invalid card number.
Usage: amixer <options> [command]

Available options:
  -h,--help this help
  -c,--card N select the card
  -D,--device N select the device, default 'default'
  -d,--debug debug mode
  -n,--nocheck do not perform range checking
  -v,--version print version of this program
  -q,--quiet be quiet
  -i,--inactive show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin Read and execute commands from stdin sequentially

Available commands:
  scontrols show all mixer simple controls
  scontents show contents of all mixer simple controls (default command)
  sset sID P set contents for one mixer simple control
  sget sID get contents for one mixer simple control
  controls show all controls for given card
  contents show contents of all controls for given card
  cset cID P set control contents for one control
  cget cID get control contents for one control

!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--

!!All Loaded Modules
!!------------------

Module
ip6table_filter
ip6_tables
ipt_MASQUERADE
iptable_nat
nf_nat
nf_conntrack_ipv4
nf_defrag_ipv4
xt_state
nf_conntrack
ipt_REJECT
xt_CHECKSUM
iptable_mangle
xt_tcpudp
iptable_filter
ip_tables
x_tables
kvm_intel
kvm
nfsd
nfs
lockd
fscache
auth_rpcgss
nfs_acl
sunrpc
snd_usb_audio
snd_pcm
snd_page_alloc
snd_hwdep
snd_usbmidi_lib
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
i915
snd_timer
bridge
snd_seq_device
stp
snd
drm_kms_helper
drm
soundcore
dm_multipath
ppdev
w83627ehf
i2c_algo_bit
hwmon_vid
tpm_tis
parport_pc
video
coretemp
lp
parport
usbhid
hid
pata_it821x
e1000e
ahci
libahci

!!ALSA/HDA dmesg
!!------------------

Thank you for your help.

---

