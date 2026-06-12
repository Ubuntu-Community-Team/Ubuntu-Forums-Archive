---
title: "after upgrade to 12.04 - kernel crash (iwlwifi - deep sleep / Oops: 0000 [#1] SMP)"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by miobrad on 2012-04-14
dear forum,

in advance - thank you very much for any insight/help! 

my wireless card used to shut down once in a while on 11.04 but not often enough for me to care enough to check why. well, yesterday i upgraded to 11.10 and then straight to 12.04 and that made the problem accute.

firstly, the wireless card shut down more often. secondly i got two kernel crashes! after investigating the kern.log i figure the problems are related.

possibly relevant HW specs:

Thinkpad x201i tablet
U3400 celeron 1.07 Ghz processor x 2
02:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)

here is the section from the kern.log that i think is relevant:

[ 8982.864140] e1000e 0000:00:19.0: PME# disabled
[ 8982.864303] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[10270.683937] thinkpad_acpi: EC reports that Thermal Table has changed
[10271.937935] e1000e 0000:00:19.0: PME# enabled
[10272.078620] iwlwifi 0000:02:00.0: **Queue 11 stuck for 2000 ms**.
[10272.078631] iwlwifi 0000:02:00.0: Current read_ptr 18 write_ptr 21
[10272.078637] iwlwifi 0000:02:00.0: On demand firmware reload
[10272.078729] iwlwifi 0000:02:00.0: **Error: Response NULL in 'REPLY_ADD_STA'**
[10272.078741] **HW problem - can not stop rx aggregation for tid 0 **
[10272.096212] iwlwifi 0000:02:00.0: **MAC is in deep sleep**!. CSR_GP_CNTRL = 0xFFFFFFFF
...
[10272.428280] ieee80211 phy0: Hardware restart was requested
[10274.425624] **iwlwifi 0000:02:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.**
[10274.425633] iwlwifi 0000:02:00.0: Current CMD queue read_ptr 140 write_ptr 141
[10274.425640]** HW problem - can not stop rx aggregation for tid 4**
[10274.454840] iwlwifi 0000:02:00.0: MAC is in deep sleep!. CSR_GP_CNTRL = 0xFFFFFFFF
...
[10274.540983] **BUG: unable to handle kernel paging request at fffffd00**
[10274.541076] IP: [<f9311734>] ieee80211_stop_tx_ba_cb_irqsafe+0x14/0x80 [mac80211]
[10274.541204] *pdpt = 0000000001938001 *pde = 000000000193d067 *pte = 0000000000000000 
[10274.541309]** Oops: 0000 [#1] SMP **
[10274.541357] Modules linked in: snd_hrtimer rfcomm bnep parport_pc ppdev binfmt_misc dm_crypt joydev arc4 snd_hda_codec_hdmi thinkpad_acpi snd_hda_codec_conexant snd_seq_midi snd_rawmidi snd_seq_midi_event psmouse snd_hda_intel iwlwifi snd_hda_codec snd_seq snd_hwdep mac80211 serio_raw uvcvideo btusb snd_pcm cfg80211 snd_seq_device bluetooth videodev intel_ips snd_timer mei(C) snd_page_alloc snd soundcore nvram tpm_tis mac_hid lp parport i915 drm_kms_helper drm e1000e i2c_algo_bit wmi video
[10274.542017] 
[10274.542042] Pid: 11936, comm: kworker/u:0 Tainted: G         C   3.2.0-23-generic-pae #36-Ubuntu LENOVO 2985FUG/2985FUG
[10274.542184] EIP: 0060:[<f9311734>] EFLAGS: 00010282 CPU: 1
[10274.542277] EIP is at ieee80211_stop_tx_ba_cb_irqsafe+0x14/0x80 [mac80211]
[10274.542364] EAX: 00000000 EBX: 00000000 ECX: 00000006 EDX: e92fe8a8
[10274.542444] ESI: 00000000 EDI: 00000006 EBP: d2663d5c ESP: d2663d4c
[10274.542523]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[10274.542592] Process kworker/u:0 (pid: 11936, ti=d2662000 task=d4b1b280 task.ti=d2662000)

thanks for any help in debugging! i have never filed a bug report, maybe this will be my first one, but i'll wait for some wisdom from the forums..

---

### Post by NHclimber on 2012-04-15
This thread [http://lists.debian.org/debian-kernel/2012/03/msg00393.html](http://lists.debian.org/debian-kernel/2012/03/msg00393.html)
seems to indicate that turning off ASPM ('pcie_aspm=off' on kernel cmd line) will workaround the issues your experiencing.

Post back if you don't know how to edit your kernel command line on boot.

---

### Post by miobrad on 2012-04-16
just saw your answer - thanks for the reply/help! i played around with the grub settings after seing some ASPM/ACPI related errors in my dmsg output and /var/log/kern.log . after searching the net i found various powersaving commands that i now use:

acpi_osi=Linux pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 drm.vblankoffdelay=1

i'm don't fully understand all of them, but i trust that they apply to my machine. with these settings i have not had a crash again, though i do not know how or why.

just double checked my kern.log and found an other error:

watchdog: error registering      /dev/watchdog (err=-16).

but i do not see anything not working as a result of it? ..

thanks again!

---

### Post by dino99 on 2012-04-16
network-manager in Precise is a nightmare, and i prefer using wicd instead

---

### Post by miobrad on 2012-04-17
i didn't think it could be such a high level app that causes the crash. i just googled it and found a comment where someone experienced the problems more at one place than an other, in relation to network manager. this is also the case with me. it happens more often at home and much less often at work.. anyways, it has not happened in the last 3 days, so i'll wait before doing anything about it..

---

