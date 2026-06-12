---
title: "Server sleeping at night"
date: 2005-02-23
forum: Server Platforms
---

### Post by VincenzoDiMassa on 2005-02-23
Hello ubuntu server forum people,
I installed a ubuntu warty server and imeediately updated it to hoary.
It is a server I can do experiments with, so hoary is fine.
Everything is set up in a way I like, and ubuntu helped me a lot.

But there are two big problems:
[list=1]
[*]if I upgrade the kernel to some 2.6.10 version the system crashes during network initialization (NAT rules maybe)
[*]every morning the system goes to a stanby like status even if apm, acpi... are disabled. The time the system goes offline is approx the time of the cron daily jobs.
[/list]

The kernel upgrade is not very important, but the problem with te system going offline every morning is driving me mad.

I checked the log /var/log/messages and all I can see is syslogd telling it is going to exit. This seems like some script/evnt is doing something nasty....

Can you help please?

Regards Vincenzo.

---

### Post by Rottweiler on 2005-02-23
[QUOTE=VincenzoDiMassa]... but the problem with te system going offline every morning is driving me mad.
 
I checked the log /var/log/messages and all I can see is syslogd telling it is going to exit. This seems like some script/evnt is doing something nasty....[/QUOTE]A couple of thoughts:

 1) Check BIOS power settings to make sure the BIOS isn't the one putting it to sleep.

2) If it's connected to a UPS, make sure the UPS isn't doing it's daily self test at that time and causing a power off.
 
3) Disable the daily cron jobs and see if the problem goes away. You'll at least know where to look or not look afterwards.

---

### Post by VincenzoDiMassa on 2005-02-23
[QUOTE=Rottweiler]A couple of thoughts:

 1) Check BIOS power settings to make sure the BIOS isn't the one putting it to sleep.
[/QUOTE]
The machine I installed ubuntu was installed for years with Mandrake 9.1. So bios should not be the problem.
[QUOTE=Rottweiler]
2) If it's connected to a UPS, make sure the UPS isn't doing it's daily self test at that time and causing a power off.
[/QUOTE]
Same as above.
[QUOTE=Rottweiler]
3) Disable the daily cron jobs and see if the problem goes away. You'll at least know where to look or not look afterwards.[/QUOTE]
This is what I wanted to do. But you know... one always hopes the problem he has has already been solved by someone else.
Another solution that comes in mind is to launch the cron jobs and look what happens.

Thank you very much for your suggestions.
Regards Vincenzo.

---

### Post by alastair on 2005-02-23
Checking the individual cron jobs might be worth it. 

Assuming this is "anacron" i.e. /etc/anacrontab and /etc/.cron.daily - it is worth trying to disable this completely.

You could perhaps comment out the cron.daily line in /etc/anacrontab and see if the problem persists. I don't think you need to restart cron for this (/etc/init.d/cron restart), but might need to.

Then .. if the problem goes away - try to find the problem job.

---

### Post by VincenzoDiMassa on 2005-02-24
I have done 
run-parts --report /etc/cron.daily 
and the system is still up and running.

The easy diagnostic test failed. Any new idea?
Maybe it is in same way related to problem #1 above.
Could it be a kernel issue? Maybe the kernel has some power saving feature that on my hardware should be disable by hand.

Should I post it somewere else? (Maybe it is OT here)

Regards, Vincenzo.

lspci shows:
```



0000:00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 MP [IGD4-2P] System Controller (rev 11)
0000:00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 MP [IGD4-2P] AGP Bridge
0000:00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-768 [Opus] ISA (rev 04)
0000:00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-768 [Opus] IDE (rev 04)
0000:00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-768 [Opus] ACPI (rev 03)
0000:00:09.0 USB Controller: NEC Corporation USB (rev 41)
0000:00:09.1 USB Controller: NEC Corporation USB (rev 41)
0000:00:09.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
0000:00:10.0 PCI bridge: Advanced Micro Devices [AMD] AMD-768 [Opus] PCI (rev 04)
0000:01:05.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
0000:02:04.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:02:05.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
0000:02:06.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
0000:02:08.0 PCI bridge: Intel Corp. 80960RM [i960RM Bridge] (rev 02)
0000:02:08.1 I2O: Intel Corp. 80960RM [i960RM Microprocessor] (rev 02)
0000:03:00.0 RAID bus controller: Promise Technology, Inc. PDC20276 (MBFastTrak133 Lite) (rev 01)
0000:03:01.0 RAID bus controller: Promise Technology, Inc. PDC20276 (MBFastTrak133 Lite) (rev 01)
0000:03:02.0 RAID bus controller: Promise Technology, Inc. PDC20276 (MBFastTrak133 Lite) (rev 01)



``` 

The loaded modules are.

```



ipt_multiport           2304  11
ipt_state               2304  63
ip_nat_tftp             3696  0
ip_nat_snmp_basic      10628  0
ip_nat_irc              4464  0
ip_nat_ftp              4976  0
ip_nat_amanda           2876  0
iptable_nat            22828  6 ip_nat_tftp,ip_nat_snmp_basic,ip_nat_irc,ip_nat_ftp,ip_nat_amanda
ip_conntrack_tftp       3860  0
ip_conntrack_irc       71604  1 ip_nat_irc
ip_conntrack_ftp       72116  1 ip_nat_ftp
ip_conntrack_amanda    69764  1 ip_nat_amanda
ip_conntrack           32640  10 ipt_state,ip_nat_tftp,ip_nat_irc,ip_nat_ftp,ip_nat_amanda,iptable_nat,ip_conntrack_tftp,ip_conntrack_irc,ip_conntrack_ftp,ip_conntrack_amanda
iptable_filter          3072  1
ip_tables              16896  4 ipt_multiport,ipt_state,iptable_nat,iptable_filter
ipv6                  230020  28
3c59x                  36776  0
snd_cmipci             30372  0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         11144  1 snd_pcm
snd_opl3_lib            9728  1 snd_cmipci
snd_timer              23172  2 snd_pcm,snd_opl3_lib
snd_hwdep               9120  1 snd_opl3_lib
gameport                4736  1 snd_cmipci
snd_mpu401_uart         7296  1 snd_cmipci
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  2 snd_opl3_lib,snd_rawmidi
snd                    50660  10 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd
ehci_hcd               27780  0
ohci_hcd               19460  0
usbcore               104292  4 ehci_hcd,ohci_hcd
hw_random               5652  0
pci_hotplug            30640  0
amd_k7_agp              7692  1
agpgart                31784  1 amd_k7_agp
pcspkr                  3816  0
rtc                    12216  0
floppy                 54996  0
ext3                  109544  1
jbd                    54552  1 ext3
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
tsdev                   7168  0
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
evdev                   9088  0
mousedev               10124  1
psmouse                17800  0
reiserfs              207600  1
ide_generic             1664  0
ide_disk               16768  4
pdc202xx_new           10012  3
amd74xx                13340  1
ide_core              125272  5 ide_cd,ide_generic,ide_disk,pdc202xx_new,amd74xx
unix                   25904  194
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb



```

---

### Post by alastair on 2005-02-24
Hard to tell.

Why not stop everything you can for a night i.e.

no cron.daily (anacron)
no networking
no iptables
as few services as possible
unload as many modules as possible (network,sound,usb etc.)
no X
etc.
Totally minimal - see if the problem persists overnight. If not - search for the culprit.

---

### Post by VincenzoDiMassa on 2005-05-06
[QUOTE=alastair]Hard to tell.

Why not stop everything you can for a night i.e.

no cron.daily (anacron)
no networking
no iptables
as few services as possible
unload as many modules as possible (network,sound,usb etc.)
no X
etc.
Totally minimal - see if the problem persists overnight. If not - search for the culprit.[/QUOTE]
 Thank you, 
The problem was the battery of the UPS.
There are many machines attached to the same UPS.
When in the morning cron jobs start on all the machines at the same time, the UPS dies.
Thank you very much for all your replies.

---

