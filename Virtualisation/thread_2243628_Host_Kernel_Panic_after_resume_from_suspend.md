---
title: "Host Kernel Panic after resume from suspend"
date: 2014-09-10
forum: Virtualisation
---

### Post by jaroon on 2014-09-10
I have my desktop current acting a kvm host and I discovered to great dismay that resuming from a suspended OS and starting up a kvm instance will result in a Host KP every time. Researching the issue I found this was an issue on Red Hat variants several years ago:

[https://bugzilla.redhat.com/show_bug.cgi?id=509809](https://bugzilla.redhat.com/show_bug.cgi?id=509809)

The steps listed there are the exact same needed to replicate my issue. The few tidbits of logs I have is a picture I have taken when I actually get output from the crash and the zero byte characters that are written to several log files in /var/log when a crash occurs.

Not sure what all information is needed to track this down however I did notice that lsmod produces different output from a fresh boot and from after a resume:

```
jar00n@lusus:~$ diff wat wut
1a2,5
> vhost_net              18104  0 
> vhost                  29009  1 vhost_net
> macvtap                18255  1 vhost_net
> macvlan                19134  1 macvtap
60c64
< nvidia              10675249  53 
---
> nvidia              10675249  59 
```

`wat' is `sudo lsmod` from a fresh boot and `wut' is `sudo lsmod' from after a resume. Attached is what I was able to capture from the KP event, most of the time I just get a blank screen and have to power cycle my desktop.

```
jar00n@lusus:~$ uname -a
Linux lusus 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

jar00n@lusus:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping	: 10
microcode	: 0xa07
cpu MHz		: 2000.000
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips	: 5666.14
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping	: 10
microcode	: 0xa07
cpu MHz		: 2000.000
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips	: 5666.14
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping	: 10
microcode	: 0xa07
cpu MHz		: 2000.000
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips	: 5666.14
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz
stepping	: 10
microcode	: 0xa07
cpu MHz		: 2000.000
cache size	: 6144 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bogomips	: 5666.14
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

jar00n@lusus:~$ lsmod
Module                  Size  Used by
usb_storage            62209  0 
cdc_acm                28803  0 
ipt_MASQUERADE         12880  3 
iptable_nat            13011  1 
nf_nat_ipv4            13263  1 iptable_nat
nf_nat                 21841  3 ipt_MASQUERADE,nf_nat_ipv4,iptable_nat
nf_conntrack_ipv4      15012  2 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_conntrack           12760  1 
nf_conntrack           96976  6 ipt_MASQUERADE,nf_nat,nf_nat_ipv4,xt_conntrack,iptable_nat,nf_conntrack_ipv4
ipt_REJECT             12541  6 
xt_CHECKSUM            12549  1 
iptable_mangle         12695  1 
xt_tcpudp              12884  16 
bridge                110833  0 
stp                    12976  1 bridge
llc                    14552  2 stp,bridge
ip6table_filter        12815  0 
ip6_tables             27025  1 ip6table_filter
iptable_filter         12810  1 
ip_tables              27239  3 iptable_filter,iptable_mangle,iptable_nat
ebtable_nat            12807  0 
ebtables               30913  1 ebtable_nat
x_tables               34059  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
dm_crypt               23177  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391136  10 bnep,rfcomm
snd_hda_codec_hdmi     46368  4 
gpio_ich               13476  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
snd_hda_codec_realtek    65580  1 
snd_usb_audio         153617  3 
videodev              134688  2 uvcvideo,videobuf2_core
snd_usbmidi_lib        29215  1 snd_usb_audio
joydev                 17381  0 
xpad                   18218  0 
ff_memless             13573  1 xpad
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102099  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  2 snd_usbmidi_lib,snd_seq_midi
dm_multipath           22873  0 
coretemp               13435  0 
scsi_dh                14882  1 dm_multipath
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13462  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  29 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
nvidia              10675249  65 
lpc_ich                21080  0 
soundcore              12680  1 snd
drm                   303102  2 nvidia
mac_hid                13205  0 
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
btrfs                 835954  0 
xor                    21411  1 btrfs
raid6_pq               97812  1 btrfs
libcrc32c              12644  1 btrfs
pata_acpi              13038  0 
hid_generic            12548  0 
pata_jmicron           12758  0 
psmouse               106678  0 
usbhid                 52570  0 
r8169                  67581  0 
mii                    13934  1 r8169
hid                   106148  2 hid_generic,usbhid

jar00n@lusus:~$ cat /etc/debian_version 
jessie/sid

jar00n@lusus:~$ cat /etc/issue
Ubuntu 14.04.1 LTS \n \l
```

Any advice or suggestions would be greatly appreciated.

--jar00n

---

