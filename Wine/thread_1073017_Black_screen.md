---
title: "Black screen"
date: 2009-02-17
forum: Wine
---

### Post by tommytrying2linux on 2009-02-17
Hi when i try and when Warcraft III, it just comes up as a black screen with sound, and i ultimately have to crash the game to get back to my desktop, heres what comes up in terminal. I've updated Wine and installed my video drivers through Envy.

Here's what comes up in Terminal
[http://pastebin.com/f27bb3d77](http://pastebin.com/f27bb3d77)

I've enter the command sudo lsmod and heres what comes up

> 
Module                  Size  Used by
nls_cp437              13696  1 
isofs                  40100  1 
udf                    88356  0 
crc_itu_t              10112  1 udf
af_packet              25728  2 
binfmt_misc            16904  1 
ipv6                  263972  14 
fglrx                1813960  30 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_ondemand       14988  2 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
pci_slot               12680  0 
video                  25232  0 
output                 11008  1 video
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
evdev                  17696  9 
pcspkr                 10624  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_hda_intel         384176  7 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  2 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              33724  0 
snd                    63268  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 14224  0 
agpgart                42184  2 fglrx,intel_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
soundcore              15328  2 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  1 
cdrom                  43168  1 sr_mod
pata_acpi              12160  0 
ata_piix               24580  0 
sd_mod                 42392  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  4 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_generic            12932  0 
sky2                   53380  0 
pata_jmicron           11136  1 
ahci                   37132  6 
libata                178208  5 pata_acpi,ata_piix,ata_generic,pata_jmicron,ahci
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  4 usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 


---

### Post by cogadh on 2009-02-17
Are you running any desktop effects? If so, that is likely the problem. Wine and desktop effects/Compiz don't get along well at all, which may present itself like this.

---

### Post by tommytrying2linux on 2009-02-17
Still seem to have no luck, i've tried turning off the visual effects in the appearance tab, and typing metacity --replace to get rid of emerald.

---

