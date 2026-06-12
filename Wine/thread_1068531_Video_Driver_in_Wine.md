---
title: "Video Driver in Wine"
date: 2009-02-13
forum: Wine
---

### Post by DesChamos on 2009-02-13
I was trying to play TF2 under Hardy Heron 8.04 Ubuntu with Wine 1.1.14.  I had added the -dxlevel 81 flag as well.  It loaded the main menu with sound but the screen was entirely black.  With sound, I was able to navigate to the exit run.  I had done some research, and unchecked pixel shading.  After doing this, the game gave me a loading screen, with the main menu background image, and then a dialog box saying that I needed pixel shading 1.1.  After this I looked up some more things.  I tried to install a video driver with envy, but I have neither nVidia nor ATI.  I have a crappy on-board chip:

Mobile Intel(R) 4 Series Express Chipset Family

Is there a driver for my chip, or is there another fix for my problem?

---

### Post by ilioscio on 2009-02-13
can you post the output of ```
sudo lsmod
```

---

### Post by DesChamos on 2009-02-13
```
Module                  Size  Used by
i915                   32512  2 
drm                    82452  3 i915
af_packet              23812  2 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
ppdev                  10372  0 
ipv6                  267908  14 
acpi_cpufreq           10796  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
joydev                 13120  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
psmouse                40336  0 
snd_usb_audio          83936  2 
evdev                  13056  11 
uvcvideo               58116  0 
serio_raw               7940  0 
pcspkr                  4224  0 
snd_hda_intel         346136  5 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
snd_pcm                78596  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_usb_lib            18432  1 snd_usb_audio
snd_seq_dummy           4868  0 
hci_usb                16540  2 
snd_hwdep              10500  2 snd_usb_audio,snd_hda_intel
snd_seq_oss            35584  0 
bluetooth              61028  7 rfcomm,l2cap,hci_usb
usb_storage            73792  0 
ieee80211_crypt_tkip    11648  0 
snd_seq_midi            9376  0 
libusual               19236  1 usb_storage
wl                   1077908  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
snd_rawmidi            25760  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  19856  0 
output                  4736  1 video
wmi_acer                9644  0 
snd                    56996  27 snd_usb_audio,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_usb_lib,snd_seq_dummy,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
battery                14212  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
ac                      6916  0 
button                  9232  0 
intel_agp_ich9m        23700  1 
agpgart                34760  3 drm,intel_agp_ich9m
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
usbhid                 32128  0 
hid                    38784  1 usbhid
ahci                   28548  2 
libata                159600  1 ahci
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
r8169                  33156  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  10 snd_usb_audio,uvcvideo,snd_usb_lib,hci_usb,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
```

---

### Post by Dizzle7677 on 2009-02-13
You may want to add these keys/strings to your registry if you don't already have them.

REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"Multisampling"="disabled"
"OffscreenRenderingMode"="backbuffer" <--or "fbo" ... do some testing. 
"PixelShaderMode"="enabled"
"RenderTargetLockMode"="auto"
"UseGLSL"="enabled" <--since you're using dxlevel 81 you can set this to 'disabled' for testing.
"VertexShaderMode"="hardware"
"VideoMemorySize"="256" <-- change to your vid mem size in MB
"VideoPciDeviceID"=dword:""<-- you get these from 'lspci -n'
"VideoPciVendorID"=dword:"" <-- "" "" adjust accordingly

See the [Wine Registry Wiki]("http://wiki.winehq.org/UsefulRegistryKeys"). 
Try different Dxlevels .. 95 & 90 with glsl 'enabled/'disabled'.

---

### Post by DesChamos on 2009-02-13
Thanks for the reply!

I modified the registry.  The output of lspci -n was 
```
00:00.0 0600: 8086:2a40 (rev 07)
00:02.0 0300: 8086:2a42 (rev 07)
00:02.1 0380: 8086:2a43 (rev 07)
00:1a.0 0c03: 8086:2937 (rev 03)
00:1a.1 0c03: 8086:2938 (rev 03)
00:1a.7 0c03: 8086:293c (rev 03)
00:1b.0 0403: 8086:293e (rev 03)
00:1c.0 0604: 8086:2940 (rev 03)
00:1c.1 0604: 8086:2942 (rev 03)
00:1c.2 0604: 8086:2944 (rev 03)
00:1c.3 0604: 8086:2946 (rev 03)
00:1c.4 0604: 8086:2948 (rev 03)
00:1c.5 0604: 8086:294a (rev 03)
00:1d.0 0c03: 8086:2934 (rev 03)
00:1d.1 0c03: 8086:2935 (rev 03)
00:1d.2 0c03: 8086:2936 (rev 03)
00:1d.3 0c03: 8086:2939 (rev 03)
00:1d.7 0c03: 8086:293a (rev 03)
00:1e.0 0604: 8086:2448 (rev 93)
00:1f.0 0601: 8086:2919 (rev 03)
00:1f.2 0106: 8086:2929 (rev 03)
00:1f.3 0c05: 8086:2930 (rev 03)
00:1f.6 1180: 8086:2932 (rev 03)
02:00.0 0280: 14e4:4328 (rev 03)
03:00.0 0200: 10ec:8136 (rev 02)
```
so I made "VideoPciDeviceID" 0x2a42 and "VideoPciVendorID" 0x8086.  After that I tried playing around the settings you suggested.  Whenever "OffscreenRenderingMode" was "fbo" the game loaded two intro things (valve and powered by source) and then closed after that.  I then tried a bunch of different things (playing dxlevel 81, 90, 95 with Use GLSL enabled/disabled) and all of them had the same error.  It played the two intro movies and loaded the main menu with a cursor visible and music and sounds playing.  However, there was no video from the game itself.

Also, regarding the video card, steam now pops with an "Unknown Video Card" warning.  This happened before on windows, but I don't know if its the same error.  Either way it has some info so I'll add it:
Driver Details:
Description: Direct3D HAL
Version: 6.14.7.0

---

### Post by Dizzle7677 on 2009-02-13
After a quick search ... found [this post]("http://ubuntuforums.org/showthread.php?t=733173") which may explain things with Intel hardware.

---

