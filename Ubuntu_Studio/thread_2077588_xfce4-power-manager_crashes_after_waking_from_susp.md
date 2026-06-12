---
title: "xfce4-power-manager crashes after waking from suspend"
date: 2012-10-28
forum: Ubuntu Studio
---

### Post by bumBumBUM on 2012-10-28
Hi, any ideas?

here is the apport.log created in /var/logs upon resuming:

> 


ERROR: apport (pid 4203) Mon Oct 29 04:15:18 2012: called for pid 3394, signal 11, core limit 0
ERROR: apport (pid 4203) Mon Oct 29 04:15:18 2012: executable: /usr/bin/xfce4-power-manager (command line "xfce4-power-manager")
ERROR: apport (pid 4203) Mon Oct 29 04:15:18 2012: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 4203) Mon Oct 29 04:15:18 2012: debug: session gdbus call: 
ERROR: apport (pid 4203) Mon Oct 29 04:15:18 2012: this executable already crashed 2 times, ignoring
I'm reading about .session files and not getting anywhere fast. Any ideas? This is on almost vanilla ubuntu studio 12.10 



the two other logs created are pm-suspend.log and pm-powersave.log

pm-suspend:

> Initial commandline parameters: 
Mon Oct 29 04:15:04 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:

/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux user-linux 3.5.0-17-lowlatency #18-Ubuntu SMP PREEMPT Tue Oct 9 20:04:43 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ums_realtek            17949  0 
uas                    17844  0 
usb_storage            44742  1 ums_realtek
michael_mic            12612  0 
arc4                   12529  0 
snd_hda_codec_idt      70209  1 
snd_hda_codec_hdmi     32007  1 
sp5100_tco             13697  0 
joydev                 17457  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
btusb                  18334  0 
uvcvideo               76749  0 
snd_seq_midi           13324  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
snd_rawmidi            30512  1 snd_seq_midi
videobuf2_vmalloc      12860  1 uvcvideo
ip6t_REJECT            12574  1 
videobuf2_memops       13368  1 videobuf2_vmalloc
xt_hl                  12521  6 
ip6t_rt                12558  3 
kvm                   418206  0 
lib80211_crypt_tkip    17379  0 
nf_conntrack_ipv6      14054  7 
nf_defrag_ipv6         13158  1 nf_conntrack_ipv6
snd_hda_intel          33491  6 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_codec         134212  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ipt_REJECT             12541  1 
psmouse                95552  0 
xt_LOG                 17349  10 
xt_limit               12711  13 
xt_tcpudp              12603  18 
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
xt_addrtype            12635  4 
xt_state               12578  14 
serio_raw              13215  0 
ip6table_filter        12815  1 
ip6_tables             27207  2 ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12649  0 
nf_nat                 25254  1 nf_nat_ftp
nf_conntrack_ipv4      14480  9 nf_nat
k10temp                13126  0 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
wl                   2573612  0 
nf_conntrack_ftp       13359  1 nf_nat_ftp
nf_conntrack           82633  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
ip_tables              26995  1 iptable_filter
x_tables               29711  13 ip6t_REJECT,xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211               14381  2 lib80211_crypt_tkip,wl
i2c_piix4              13167  0 
radeon                895653  2 
snd                    74638  22 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
ttm                    83595  1 radeon
drm_kms_helper         46784  1 radeon
drm                   275528  4 radeon,ttm,drm_kms_helper
parport_pc             32688  0 
rfcomm                 42523  4 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
wmi                    19070  1 hp_wmi
bnep                   18140  2 
i2c_algo_bit           13413  1 radeon
ppdev                  17073  0 
bluetooth             209256  11 btusb,rfcomm,bnep
mac_hid                13205  0 
video                  19335  0 
hp_accel               25976  0 
lis3lv02d              19829  1 hp_accel
input_polldev          13896  1 lis3lv02d
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
r8169                  61650  0 
microcode              22803  0 
             total       used       free     shared    buffers     cached
Mem:       3639640     695280    2944360          0      54280     343064
-/+ buffers/cache:     297936    3341704
Swap:            0          0          0

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Oct 29 04:15:05 CET 2012: performing suspend
Mon Oct 29 04:15:16 CET 2012: Awake.
Mon Oct 29 04:15:16 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting standby to 36 (3 minutes)

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:

/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Mon Oct 29 04:15:17 CET 2012: Finished.pm-powersave:

> Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pci_devices false:
Setting Host Bridge 0000:00:00.0 to on
Setting Audio device 0000:00:01.1 to on
Setting Audio device 0000:00:14.2 to on
Setting Host Bridge 0000:00:18.0 to on
Setting Host Bridge 0000:00:18.1 to on
Setting Host Bridge 0000:00:18.2 to on
Setting Host Bridge 0000:00:18.3 to on
Setting Host Bridge 0000:00:18.4 to on
Setting Host Bridge 0000:00:18.5 to on
Setting Host Bridge 0000:00:18.6 to on
Setting Host Bridge 0000:00:18.7 to on
Setting Wireless device 0000:03:00.0 to on
Setting Ethernet device 0000:07:00.0 to on

/usr/lib/pm-utils/power.d/pci_devices false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:
Setting SATA ALPM on host0 to max_performance...Done.

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/usb_bluetooth false:

/usr/lib/pm-utils/power.d/usb_bluetooth false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:
Turning powersave for eth1 off...Done.

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm true:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/usr/lib/pm-utils/power.d/95hdparm-apm true: success.
Running hook /usr/lib/pm-utils/power.d/anacron true:

/usr/lib/pm-utils/power.d/anacron true: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol true:

/usr/lib/pm-utils/power.d/disable_wol true: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave true:
Setting power savings for snd_hda_intel to 1...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode true:
Laptop mode enabled.

/usr/lib/pm-utils/power.d/laptop-mode true: success.
Running hook /usr/lib/pm-utils/power.d/pci_devices true:
Setting Host Bridge 0000:00:00.0 to auto
Setting Audio device 0000:00:01.1 to auto
Setting Audio device 0000:00:14.2 to auto
Setting Host Bridge 0000:00:18.0 to auto
Setting Host Bridge 0000:00:18.1 to auto
Setting Host Bridge 0000:00:18.2 to auto
Setting Host Bridge 0000:00:18.3 to auto
Setting Host Bridge 0000:00:18.4 to auto
Setting Host Bridge 0000:00:18.5 to auto
Setting Host Bridge 0000:00:18.6 to auto
Setting Host Bridge 0000:00:18.7 to auto
Setting Wireless device 0000:03:00.0 to auto
Setting Ethernet device 0000:07:00.0 to auto

/usr/lib/pm-utils/power.d/pci_devices true: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm true:

/usr/lib/pm-utils/power.d/pcie_aspm true: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm true:

/usr/lib/pm-utils/power.d/sata_alpm true: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave true:
**sched policy powersave ON

/usr/lib/pm-utils/power.d/sched-powersave true: success.
Running hook /usr/lib/pm-utils/power.d/usb_bluetooth true:

/usr/lib/pm-utils/power.d/usb_bluetooth true: success.
Running hook /usr/lib/pm-utils/power.d/wireless true:
Turning powersave for eth1 on...Done.

/usr/lib/pm-utils/power.d/wireless true: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer true:

/usr/lib/pm-utils/power.d/xfs_buffer true: not applicable.I guess the next place to try would be the xubuntu forum?


thanks for any advice,

bumBumBUM

---

### Post by bumBumBUM on 2012-11-04
the issue is solved. Patched packages are currently available in proposed...

[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1054907](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1054907)

---

