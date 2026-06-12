---
title: "Xruns in jack, without any other programs open"
date: 2010-02-15
forum: Ubuntu Studio
---

### Post by Monona on 2010-02-15
So, I run qjackctl, start JACK, and proceed to get xruns at the rate of around 1/sec.

This is before I run any other audio programs.  When I load something else, it gets worse, and the audio is all chopped up with static (which isn't necessarily bad, but i want to do the chopping myself).

I've read around and tried stuff, and still can't get it working.  This is a new install of Hardy 8.04 with the realtime kernel.  2G RAM, Dual Core Pentium D 3GHz.  Here's what I've got:

~$ uname -r
2.6.24-27-rt

~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

/etc/security/limits.conf:
@audio - rtprio 99
@audio - nice -19
@audio - memlock unlimited

Jack settings:
Realtime-ticked (no other boxes ticked)
Priority: Default
Frames: 1024
Sample Rate: 44100
Periods: 2
Everything else is set to default.  I've changed the settings, and nothing seems to work.  Any thoughts?

---

### Post by AutoStatic on 2010-02-16
Hello Monona, could you post the outcome of **cat /proc/interrupts** ?

---

### Post by Monona on 2010-02-16
~$ cat /proc/interrupts
           CPU0       CPU1       
  0:        496          0   IO-APIC-edge      timer
  1:       8718          0   IO-APIC-edge      i8042
  7:          0          0   IO-APIC-edge      parport0
  8:          3          0   IO-APIC-edge      rtc
  9:          1          0   IO-APIC-fasteoi   acpi
 14:     282773          0   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:    2576519          0   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel, ivtv0
 17:      51494          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 19:     168934          0   IO-APIC-fasteoi   uhci_hcd:usb3
 20:      87367          0   IO-APIC-fasteoi   ohci1394, eth0
222:      47916          0   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:   52475442   53752124   Local timer interrupts
RES:      35035     194825   Rescheduling interrupts
CAL:      19425      16886   function call interrupts
TLB:       2801       2591   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

What does that all mean?  HDA Intel is my soundcard, right?  So what does it mean that it shares interrupts?

---

### Post by AutoStatic on 2010-02-16
> **Monona said:**
> What does that all mean?  HDA Intel is my soundcard, right?  So what does it mean that it shares interrupts?HDA Intel is your soundcard and it shares an IRQ with a USB port and a TV Card apparently. You could try unloading the kernel module for the TV Card (my bet is a **sudo modprobe -r ivtv** should unload it) and try running JACK again. And could you also post the output of **lsusb** and **lsmod** ?

---

### Post by raboofje on 2010-02-16
And perhaps post the output of [http://code.google.com/p/realtimeconfigquickscan/](http://code.google.com/p/realtimeconfigquickscan/) ?

---

### Post by Monona on 2010-02-17
I ran **sudo modprobe -r ivtv**, which unloaded ivtv0.  Jack still has consistent xruns, although maybe a few less.  We're talking every second or few.

~$ lsusb
Bus 005 Device 002: ID 1058:1001 Western Digital Technologies, Inc. External Hard Disk
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14592  1 
fat                    55196  1 vfat
ipv6                  275684  10 
binfmt_misc            13320  1 
af_packet              24196  2 
rfcomm                 43280  2 
l2cap                  26112  13 rfcomm
bluetooth              62628  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_conservative     8840  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
container               5760  0 
sbs                    15368  0 
dock                   11564  0 
sbshc                   7808  1 sbs
video                  19984  0 
output                  4736  1 video
battery                14596  0 
iptable_filter          3968  0 
ip_tables              14820  1 iptable_filter
x_tables               16644  1 ip_tables
ac                      7044  0 
sbp2                   24584  0 
lp                     13252  0 
wm8775                  6924  0 
cx25840                28176  0 
joydev                 13248  0 
tuner                  43168  0 
tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner
snd_hda_intel         346264  3 
snd_pcm_oss            42400  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78852  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  1 snd_hda_intel
snd_seq_dummy           4868  0 
i2c_core               25392  8 wm8775,cx25840,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761
v4l2_common            18432  3 wm8775,cx25840,tuner
snd_seq_oss            35968  0 
snd_seq_midi            9376  0 
ath_pci               101536  0 
wlan                  208368  1 ath_pci
snd_rawmidi            25632  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
ath_hal               192720  1 ath_pci
snd_seq                54992  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
snd                    57636  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              25492  0 
shpchp                 34708  0 
parport_pc             36516  1 
pci_hotplug            31776  1 shpchp
pcspkr                  4224  0 
parport                38600  3 ppdev,lp,parport_pc
evdev                  13312  4 
agpgart                34900  1 intel_agp
soundcore               9312  1 snd
ext3                  137864  1 
jbd                    49044  1 ext3
mbcache                 9856  1 ext3
sr_mod                 18084  0 
cdrom                  37152  1 sr_mod
sg                     36824  0 
sd_mod                 31152  5 
ata_piix               19716  0 
ata_generic             8452  0 
usbhid                 32640  0 
hid                    39040  1 usbhid
usb_storage            73792  1 
libusual               19392  1 usb_storage
ahci                   28804  2 
pata_acpi               8320  0 
ohci1394               34096  0 
libata                160496  4 ata_piix,ata_generic,ahci,pata_acpi
e100                   37772  0 
scsi_mod              153324  6 sbp2,sr_mod,sg,sd_mod,usb_storage,libata
ieee1394               95672  2 sbp2,ohci1394
mii                     6400  1 e100
ehci_hcd               37772  0 
uhci_hcd               26896  0 
usbcore               147372  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16924  0 
processor              37256  1 thermal
fan                     5636  0 
fuse                   51604  3

Is there a way to move the soundcard to a different IRQ?  Would that help?

And raboofje, what is the code you're suggesting?  I try to make it a habit not to just run random stuff.  ;)

---

### Post by AutoStatic on 2010-02-18
Thanks! CPU frequency scaling is probably causing your xruns. If 8.04 also has the CPU frequency scaling applet please add it to your Gnome panel (assuming you're using Gnome) and set both your CPU cores to  Performance. You could also try disabling CPU frequency scaling alltogether.
And the script of raboofje is perfectly safe, more info here: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

---

### Post by Monona on 2010-02-19
Here's the output of realTimeConfigQuickScan.pl:

Checking if you are root... no - good.
Finding current kernel config... found /boot/config-2.6.24-27-rt
Checking for Ingo Molnar's Real-Time Preemption... found - good.
Checking for high-resolution timers... found - good.
Checking for 1000hz clock... found - good.
Checking for High Resolution Timers... found - good.
Checking filesystem types... ok.
Checking tmpfs mounted on /tmp..  not found.
** Warning: no tmpfs partition mounted on /tmp
   For more information, see:
   - [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#tmpfs](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#tmpfs)
   - [http://lowlatency.linuxaudio.org](http://lowlatency.linuxaudio.org)
Checking filesystem 'noatime' parameter... 
** Warning: / does not have the 'noatime' parameter set
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems)
** Warning: /media/Elements does not have the 'noatime' parameter set
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems)
** Set $SOUND_CARD_IRQ to the IRQ of your soundcard to enable more checks.
   Find your sound card's IRQ by looking at '/proc/interrupts' and lspci.
Checking the ability to prioritize processes with (re)nice... yes - good.
Checking the ability to prioritize processes with rtprio... yes - good.
Checking whether you're in the 'audio' group... yes - good.
Checking for multiple 'audio' groups... no - good.
Checking access to the real-time clock... readable - good.
Checking access to the high precision event timer... not readable.
** Warning: /dev/hpet found, but not readable.
** make /dev/hpet readable by the 'audio' group
   For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#hpet](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#hpet)
Checking sysctl settings:
- checking inotify max_user_watches... >= 524288 - good.
Checking for resource-intensive background processes... none found - good.

And I have no idea what CPU frequency scaling is, or how to get the applet or disable it. 

And I am running Gnome.

Thanks!

---

### Post by AutoStatic on 2010-02-19
The output of the script looks good.
CPU frequency scaling simply means that your CPU runs slower when it has less to do in order to save power. If you right click on your Gnome panel, select 'Add to panel' and then 'CPU Frequency Scaling Monitor' an extra icon will appear in your panel. If you left click on that icon you can set the speed of your CPU. If you select 'Performance' your CPU will run at max speed for that session preventing any xruns that might get caused by your CPU scaling all the time.

---

### Post by Monona on 2010-02-21
CPU Frequency scaling is unsupported on my system.  I don't know if that's because it's Hardy, or it's dual-core, or what.  Wouldn't CPU frequency scaling only affect jack when it's initially turned on, and the xruns would go away once the CPU has scaled up?  Or am I way off base there?

Any other suggestions?  Is there a way to check if it's a hardware issue?

---

