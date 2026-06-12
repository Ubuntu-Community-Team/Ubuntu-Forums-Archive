---
title: "Network shuts off after removal of Monitor/Kbd/mouse"
date: 2004-12-22
forum: Server Platforms
---

### Post by kousik on 2004-12-22
Hi. After a successful use of ubuntu as a desktop, I wanted to make it a server. It is sort of a build server, where several users ssh in and do programming. I hope to run more servers later, but right now sshd is what it is running.

Once the installation was complete, I removed the keyboard, monitor and mouse. Only network cables (2 ethernet cards) and power cable is on. The system will work smoothly for a few hours (idle overnight), and after that the network gets shut down. I can't ping, and ssh connections close. The only way to bring the machine back is to visit the data center, connect kbd, monitor, mouse. Immediately things start working (no reboot required). Since network is out, I can't really examine the machine remotely, and if I connect the peripherals, everything starts working. 

There is nothing suspicious in /var/log. If you want me to look for some specific message, let me know and I'll post. 

The hardware is a HP xw4100 desktop, if it helps. Is any kernel module doing this? Here's the lsmod, should I unload any?
[FONT=Courier New]
**kousik@zedtwo:~ $** sudo lsmod
Module                  Size  Used by
isofs                  37340  0 
udf                    93508  0 
proc_intf               4128  0 
cpufreq_powersave       1952  0 
cpufreq_userspace       7072  0 
freq_table              4512  0 
button                  6808  0 
ac                      5036  0 
battery                 9612  0 
ipv6                  273988  22 
8139cp                 21792  0 
8139too                27008  0 
mii                     5280  2 8139cp,8139too
crc32                   4512  2 8139cp,8139too
tg3                    87428  0 
snd_intel8x0           36524  0 
snd_ac97_codec         68772  1 snd_intel8x0
snd_pcm_oss            53864  0 
snd_mixer_oss          19744  1 snd_pcm_oss
snd_pcm                99552  2 snd_intel8x0,snd_pcm_oss
snd_timer              26756  1 snd_pcm
snd_page_alloc         11688  2 snd_intel8x0,snd_pcm
gameport                5024  1 snd_intel8x0
snd_mpu401_uart         8416  1 snd_intel8x0
snd_rawmidi            25664  1 snd_mpu401_uart
snd_seq_device          8296  1 snd_rawmidi
snd                    57828  9 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10688  1 snd
ata_piix                8228  0 
libata                 40676  1 ata_piix
scsi_mod              125412  1 libata
ehci_hcd               32068  0 
uhci_hcd               33008  0 
usbcore               119044  4 ehci_hcd,uhci_hcd
pci_hotplug            34716  0 
intel_mch_agp          10544  0 
intel_agp              22336  1 
agpgart                34316  3 intel_mch_agp,intel_agp
md                     50184  0 
dm_mod                 58592  1 
capability              4744  0 
commoncap               7392  1 capability
nvidia               4822836  12 
parport_pc             35680  1 
lp                     11044  0 
parport                42216  2 parport_pc,lp
ide_cd                 42180  0 
cdrom                  39808  1 ide_cd
evdev                   9696  0 
tsdev                   7488  0 
mousedev               10480  1 
psmouse                19976  0 
reiserfs              245488  4 
ext2                   72616  0 
ext3                  126344  0 
jbd                    68952  1 ext3
mbcache                10148  2 ext2,ext3
ide_generic             1632  0 
ide_disk               19136  6 
piix                   13504  1 
ide_core              138896  4 ide_cd,ide_generic,ide_disk,piix
unix                   30800  215 
fan                     4204  0 
thermal                13232  0 
processor              18272  1 thermal
font                    8576  0 
vesafb                  6784  0 
cfbcopyarea             3936  1 vesafb
cfbimgblt               3296  1 vesafb
cfbfillrect             3840  1 vesafb[/FONT]

Thanks for any help,
Kousik.

---

### Post by Hellsteeth on 2004-12-22
Unlikely to be monitor or mouse. Most likely it will be the keyboard. Are you unplugging the keyboard with the pc switched on? This can easily give grief.
If so, try disabling the "Halt on all errors" in the BIOS and rebooting without the keyboard, monitor and mouse.

As a test you could also just leave the keyboard connected only and see if this works. If leaving the keyboard is not an option, I have seen dummy keyboard plugs that fit in the PS/2 keyboard slot that fools the pc into thinking their is a keyboard there when it is not.

---

### Post by britishtrident on 2005-01-04
Yes Hellsteeth is 100% correct most nix system freeze if the keyboard is unplugged on a running system also unplugging and re plugging a keyboard or mouse on the ps2 ports  can cause serious damage to  the motherboard ports. For my firewall PC I normally just boot without mouse keyboard or monitor but  on occaision   I use a KVM switch  but a dummy keyboard adpator  or PS2 to USB keyboard dongle would work also.

---

