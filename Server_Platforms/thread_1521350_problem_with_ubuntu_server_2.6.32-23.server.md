---
title: "problem with ubuntu server 2.6.32-23.server"
date: 2010-06-30
forum: Server Platforms
---

### Post by iaw4 on 2010-06-30
warning---2.6.32-23-server was pushed out to me today.  it failed to mount my software raid partitions (ext4).  going back to 2.6.32 solved my problem.  not sure if others are affected.


the working modules are

Module                  Size  Used by
btrfs                 476442  0 
zlib_deflate           21834  1 btrfs
crc32c                  2983  1 
libcrc32c               1244  1 btrfs
ufs                    73714  0 
qnx4                    7736  0 
hfsplus                77415  0 
hfs                    46853  0 
minix                  29315  0 
ntfs                   97846  0 
vfat                   10802  0 
msdos                   7936  0 
fat                    55062  2 vfat,msdos
jfs                   184632  0 
xfs                   539798  0 
exportfs                4202  1 xfs
reiserfs              243344  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
ipt_MASQUERADE          1863  1 
iptable_nat             5219  1 
nf_nat                 19501  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      12980  4 iptable_nat,nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
xt_state                1490  1 
nf_conntrack           73934  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT              2384  2 
xt_tcpudp               2667  4 
iptable_filter          2791  1 
ip_tables              18358  2 iptable_nat,iptable_filter
x_tables               22429  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
bridge                 53152  0 
stp                     2171  1 bridge
kvm_intel              46296  0 
kvm                   286360  1 kvm_intel
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_realtek   278890  1 
snd_hda_intel          25645  2 
snd_hda_codec          85663  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6778  1 snd_hda_codec
snd_pcm_oss            41234  0 
snd_mixer_oss          16107  1 snd_pcm_oss
snd_pcm                87216  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31027  0 
snd_seq_midi            5829  0 
radeon                739595  3 
snd_rawmidi            23052  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
ttm                    60815  1 radeon
snd_seq                57353  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23521  2 snd_pcm,snd_seq
drm_kms_helper         30710  1 radeon
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   198226  5 radeon,ttm,drm_kms_helper
snd                    70818  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
i2c_algo_bit            6024  1 radeon
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
psmouse                64608  0 
xhci                   40958  0 
serio_raw               4950  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
asus_atk0110           10033  0 
raid10                 21290  0 
raid456                54720  0 
async_raid6_recov       5945  1 raid456
async_pq                3891  2 raid456,async_raid6_recov
raid6_pq               80147  2 async_raid6_recov,async_pq
async_xor               3111  3 raid456,async_raid6_recov,async_pq
hid_apple               5418  0 
usbhid                 40988  0 
hid                    83376  2 hid_apple,usbhid
ohci1394               30260  0 
xor                     4685  1 async_xor
ieee1394               94675  1 ohci1394
async_memcpy            1537  2 raid456,async_raid6_recov
async_tx                2545  5 raid456,async_raid6_recov,async_pq,async_xor,async_memcpy
sky2                   48803  0 
raid1                  22130  2 
raid0                   6778  1 
multipath               7149  0 
linear                  4158  0

---

