---
title: "wecam not found by guest distro (Ubuntu)"
date: 2008-12-19
forum: Virtualisation
---

### Post by meharts on 2008-12-19
Hi folks:p I feel terrible about starting a new thread about something that has been discussed to death......sorry. I have gone round in circles for days now but not getting anywhere!

I have Windows XP Pro as my host and have installed Ubuntu 8.10 as the guest in vmware. Vmware seems to be finding my Logitech quickcam pro 4000 but not ubuntu?

I have run lsusb

> 
bookie@bookie-desktop:~/Installs/qc-usb-0.6.6$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




The result of lsmod

> 

bookie@bookie-desktop:~/Installs/qc-usb-0.6.6$ lsmod
Module                  Size  Used by
videodev               41344  0 
v4l1_compat            22404  1 videodev
ohci_hcd               31888  0 
isofs                  40100  1 
udf                    88356  0 
crc_itu_t              10112  1 udf
iptable_nat            13448  0 
xt_limit               10372  0 
xt_tcpudp              11008  0 
iptable_mangle         10880  0 
ipt_LOG                13700  0 
ipt_MASQUERADE         10752  0 
nf_nat                 25368  2 iptable_nat,ipt_MASQUERADE
xt_DSCP                11264  0 
ipt_REJECT             11136  0 
nf_conntrack_irc       13348  0 
nf_conntrack_ftp       15652  0 
nf_conntrack_ipv4      21900  3 iptable_nat,nf_nat
xt_state               10112  0 
nf_conntrack           72032  7 iptable_nat,ipt_MASQUERADE,nf_nat,nf_conntrack_irc,nf_conntrack_ftp,nf_conntrack_ipv4,xt_state
binfmt_misc            16904  1 
af_packet              25728  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,sco,rfcomm,l2cap
ppdev                  15620  0 
acpiphp                30228  0 
ipv6                  263972  10 
speedstep_lib          12676  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
pci_slot               12552  0 
video                  25104  0 
output                 11008  1 video
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22916  9 iptable_nat,xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,ip_tables
lp                     17156  0 
evdev                  17696  6 
serio_raw              13444  0 
psmouse                45200  0 
pcspkr                 10624  0 
snd_ens1371            30880  4 
gameport               19468  1 snd_ens1371
snd_ac97_codec        111652  1 snd_ens1371
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  2 snd_pcm_oss
snd_pcm                83204  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  2 snd
snd_page_alloc         16136  1 snd_pcm
container              11520  0 
ac                     12292  0 
button                 14224  0 
i2c_piix4              16144  0 
intel_agp              33724  1 
i2c_core               31892  1 i2c_piix4
shpchp                 37908  0 
pci_hotplug            35236  2 acpiphp,shpchp
agpgart                42184  1 intel_agp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  1 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
ata_piix               24580  1 
pcnet32                39684  0 
usbcore               148848  4 ohci_hcd,ehci_hcd,uhci_hcd
mii                    13440  1 pcnet32
libata                177312  3 ata_generic,pata_acpi,ata_piix
mptspi                 25224  2 
mptscsih               43904  1 mptspi
mptbase                86628  2 mptspi,mptscsih
scsi_transport_spi     30592  1 mptspi
scsi_mod              155212  7 sr_mod,sd_mod,sg,libata,mptspi,mptscsih,scsi_transport_spi
dock                   16656  2 acpiphp,libata
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
bookie@bookie-desktop:~/Installs/qc-usb-0.6.6$ 




I haven't tried to run webcams in virtual before...so I haven't a clue what I should do to get this working?

Can someone give me some pointers please!

meharts

---

### Post by dubfazer on 2008-12-23
First thing you will have to do is to "connect" the USB device to the virtual machine. From the vmware workstation GUI. 
Click on the VM menu : VM / Removable devices / USB Devices .

You should see your logitech web cam there. Click on the correct USB device and you will see a "tick" or check beside it to show that it is connected. Click again (removing the tick, and it will be disconnected).

Once connected to the VM, you will then need to get the camera working. There are already posts in different threads for this. Try installing easycam as a start (search for it in synaptic)

---

