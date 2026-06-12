---
title: "Ubuntu 16.04 Baytrail tablet DSI1 dark screen"
date: 2016-05-22
forum: Ubuntu Phone and Tablet
---

### Post by bmw-man on 2016-05-22
Hello,
I was able to install Ubuntu 16.04 on my WinBook TW802 tablet. Everything went straight forward with the latest ubuntu, no issues with grub and 32bit UEFI. The main issue I am having right now is the tablet screen gets dark after boot. External monitor on HDMI works fine. I believe the issue is with the backlight setting. I've been reading all kinds of forums for the past 2 weeks and still no luck. I believe 16.04 comes with the latest Intel i915 drivers already. I also tried many different kernels, including 3.8, 3.9, 4.0, 4.3, 4.3.4, 4.4, and the latest 4.6. The only way to get the screen to turn on is when booting with **i915.modeset=0** but then the image is sideways and I can't turn it to landscape mode.

I've been reading that there might be a patch I need to do on the kernel, but I'm not sure what/how to do that. Below is some info about my system:

**xrandr**
```
[HTML]Screen 0: minimum 8 x 8, current 2720 x 1280, maximum 32767 x 32767
DSI1 connected 800x1280+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x1280      60.00*+
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1920x1080+800+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1440x576      50.00  
   1024x768      75.08    70.07    60.00  
   1440x480      60.00    59.94  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    66.67    60.00    59.94  
   720x400       70.08  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

**lspci**
```
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0f)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0f)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0f)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0f)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0f)
```

**xinput**
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=7    [slave  pointer  (2)]
&#9116;   &#8627; Goodix Capacitive TouchScreen               id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; LITE-ON Technology USB NetVista Full Width Keyboard.    id=8    [slave  keyboard (3)]
    &#8627; gpio-keys                                   id=10    [slave  keyboard (3)]

```

[B]dmesg
```
[/B]
[   31.659468] WARNING: CPU: 0 PID: 1020 at drivers/gpu/drm/i915/intel_display.c:12324 check_crtc_state+0x8e7/0x1010 [i915]()
[   31.659472] pipe state doesn't match!
[   31.659474] Modules linked in: ax88179_178a usbnet mii nls_iso8859_1 intel_rapl intel_soc_dts_thermal intel_soc_dts_iosf intel_powerclamp pn544_mei coretemp mei_phy pn544 kvm_intel snd_soc_sst_baytrail_pcm hci snd_soc_sst_ipc nfc kvm snd_soc_sst_dsp joydev snd_soc_sst_byt_rt5640_mach gpio_keys crc32_pclmul aesni_intel aes_x86_64 glue_helper lrw gf128mul ablk_helper cryptd snd_intel_sst_acpi snd_soc_rt5640 snd_intel_sst_core cm3218(OE) snd_soc_rl6231 snd_soc_sst_mfld_platform snd_soc_core snd_seq_midi snd_seq_midi_event snd_rawmidi snd_compress ac97_bus snd_pcm_dmaengine bmc150_accel snd_seq snd_pcm snd_seq_device cm3218x snd_timer industrialio_triggered_buffer kfifo_buf snd industrialio soundcore goodix_backport(OE) battery mei_txe lpc_ich mei iosf_mbi dw_dmac rfkill_gpio mac_hid dw_dmac_core soc_button_array
[   31.659566]  snd_soc_sst_acpi i2c_designware_platform 8250_dw spi_pxa2xx_platform i2c_designware_core acpi_pad parport_pc ppdev lp parport autofs4 hid_generic usbhid hid mmc_block i915 i2c_algo_bit drm_kms_helper drm video sdhci_acpi sdhci
[   31.659599] CPU: 0 PID: 1020 Comm: Xorg Tainted: G        W  OE   4.2.0 #2
[   31.659603] Hardware name: WinBook TW802/TW802, BIOS 1.00 IA32 11/24/2014
[   31.659607]  ffffffffa01a76c8 ffff880074e93798 ffffffff81789eb9 0000000080000001
[   31.659615]  ffff880074e937e8 ffff880074e937d8 ffffffff810629dc ffff880074e937e0
[   31.659622]  ffff880075e74b50 ffff880075e74800 ffff880035c06000 0000000000000001
[   31.659629] Call Trace:
[   31.659639]  [<ffffffff81789eb9>] dump_stack+0x4f/0x7b
[   31.659647]  [<ffffffff810629dc>] warn_slowpath_common+0x8c/0xd0
[   31.659653]  [<ffffffff81062a68>] warn_slowpath_fmt+0x48/0x50
[   31.659688]  [<ffffffffa0138b17>] check_crtc_state+0x8e7/0x1010 [i915]
[   31.659730]  [<ffffffffa014c6f7>] intel_modeset_check_state+0x227/0xbe0 [i915]
[   31.659765]  [<ffffffffa0146a29>] ? __intel_set_mode+0x939/0xb80 [i915]
[   31.659802]  [<ffffffffa014de61>] intel_crtc_set_config+0x541/0x5a0 [i915]
[   31.659827]  [<ffffffffa004870e>] drm_mode_set_config_internal+0x6e/0x110 [drm]
[   31.659849]  [<ffffffffa004ce40>] drm_mode_setcrtc+0x190/0x4f0 [drm]
[   31.659867]  [<ffffffffa003d7a8>] drm_ioctl+0x1a8/0x650 [drm]
[   31.659874]  [<ffffffff8118f795>] ? do_wp_page+0x235/0x620
[   31.659882]  [<ffffffff811e44e2>] do_vfs_ioctl+0x2c2/0x4a0
[   31.659887]  [<ffffffff811ee55a>] ? __fget+0x7a/0xb0
[   31.659893]  [<ffffffff811e473f>] SyS_ioctl+0x7f/0x90
[   31.659900]  [<ffffffff81072149>] ? SyS_rt_sigprocmask+0x89/0xb0
[   31.659906]  [<ffffffff8179096e>] entry_SYSCALL_64_fastpath+0x12/0x71
[   31.659912] ---[ end trace 11a920db2ca0a6d3 ]---
[   33.534860] [drm:check_crtc_state [i915]] *ERROR* mismatch in dpll_hw_state.dpll (expected 0x20002000, found 0x20000000)
[   33.534872] ------------[ cut here ]------------
[   33.534909] WARNING: CPU: 2 PID: 1020 at drivers/gpu/drm/i915/intel_display.c:12324 check_crtc_state+0x8e7/0x1010 [i915]()
[   33.534912] pipe state doesn't match!
[   33.534915] Modules linked in: ax88179_178a usbnet mii nls_iso8859_1 intel_rapl intel_soc_dts_thermal intel_soc_dts_iosf intel_powerclamp pn544_mei coretemp mei_phy pn544 kvm_intel snd_soc_sst_baytrail_pcm hci snd_soc_sst_ipc nfc kvm snd_soc_sst_dsp joydev snd_soc_sst_byt_rt5640_mach gpio_keys crc32_pclmul aesni_intel aes_x86_64 glue_helper lrw gf128mul ablk_helper cryptd snd_intel_sst_acpi snd_soc_rt5640 snd_intel_sst_core cm3218(OE) snd_soc_rl6231 snd_soc_sst_mfld_platform snd_soc_core snd_seq_midi snd_seq_midi_event snd_rawmidi snd_compress ac97_bus snd_pcm_dmaengine bmc150_accel snd_seq snd_pcm snd_seq_device cm3218x snd_timer industrialio_triggered_buffer kfifo_buf snd industrialio soundcore goodix_backport(OE) battery mei_txe lpc_ich mei iosf_mbi dw_dmac rfkill_gpio mac_hid dw_dmac_core soc_button_array
[   33.535009]  snd_soc_sst_acpi i2c_designware_platform 8250_dw spi_pxa2xx_platform i2c_designware_core acpi_pad parport_pc ppdev lp parport autofs4 hid_generic usbhid hid mmc_block i915 i2c_algo_bit drm_kms_helper drm video sdhci_acpi sdhci
[   33.535045] CPU: 2 PID: 1020 Comm: Xorg Tainted: G        W  OE   4.2.0 #2
[   33.535048] Hardware name: WinBook TW802/TW802, BIOS 1.00 IA32 11/24/2014
[   33.535053]  ffffffffa01a76c8 ffff880074e93798 ffffffff81789eb9 0000000080000001
[   33.535061]  ffff880074e937e8 ffff880074e937d8 ffffffff810629dc ffff880074e937e0
[   33.535068]  ffff880075e74b50 ffff880075e74800 ffff880035c06000 0000000000000001
[   33.535075] Call Trace:
[   33.535087]  [<ffffffff81789eb9>] dump_stack+0x4f/0x7b
[   33.535095]  [<ffffffff810629dc>] warn_slowpath_common+0x8c/0xd0
[   33.535101]  [<ffffffff81062a68>] warn_slowpath_fmt+0x48/0x50
[   33.535136]  [<ffffffffa0138b17>] check_crtc_state+0x8e7/0x1010 [i915]
[   33.535178]  [<ffffffffa014c6f7>] intel_modeset_check_state+0x227/0xbe0 [i915]
[   33.535214]  [<ffffffffa0146a29>] ? __intel_set_mode+0x939/0xb80 [i915]
[   33.535250]  [<ffffffffa014de61>] intel_crtc_set_config+0x541/0x5a0 [i915]
[   33.535276]  [<ffffffffa004870e>] drm_mode_set_config_internal+0x6e/0x110 [drm]
[   33.535298]  [<ffffffffa004ce40>] drm_mode_setcrtc+0x190/0x4f0 [drm]
[   33.535316]  [<ffffffffa003d7a8>] drm_ioctl+0x1a8/0x650 [drm]
[   33.535325]  [<ffffffff811e44e2>] do_vfs_ioctl+0x2c2/0x4a0
[   33.535331]  [<ffffffff811ee55a>] ? __fget+0x7a/0xb0
[   33.535337]  [<ffffffff811e473f>] SyS_ioctl+0x7f/0x90
[   33.535344]  [<ffffffff81072149>] ? SyS_rt_sigprocmask+0x89/0xb0
[   33.535350]  [<ffffffff8179096e>] entry_SYSCALL_64_fastpath+0x12/0x71
[   33.535356] ---[ end trace 11a920db2ca0a6d4 ]---
[   33.546850] [drm:check_crtc_state [i915]] *ERROR* mismatch in dpll_hw_state.dpll (expected 0x20002000, found 0x20000000)
[   33.546861] ------------[ cut here ]------------
[   33.546897] WARNING: CPU: 2 PID: 1020 at drivers/gpu/drm/i915/intel_display.c:12324 check_crtc_state+0x8e7/0x1010 [i915]()
[   33.546900] pipe state doesn't match!
[   33.546903] Modules linked in: ax88179_178a usbnet mii nls_iso8859_1 intel_rapl intel_soc_dts_thermal intel_soc_dts_iosf intel_powerclamp pn544_mei coretemp mei_phy pn544 kvm_intel snd_soc_sst_baytrail_pcm hci snd_soc_sst_ipc nfc kvm snd_soc_sst_dsp joydev snd_soc_sst_byt_rt5640_mach gpio_keys crc32_pclmul aesni_intel aes_x86_64 glue_helper lrw gf128mul ablk_helper cryptd snd_intel_sst_acpi snd_soc_rt5640 snd_intel_sst_core cm3218(OE) snd_soc_rl6231 snd_soc_sst_mfld_platform snd_soc_core snd_seq_midi snd_seq_midi_event snd_rawmidi snd_compress ac97_bus snd_pcm_dmaengine bmc150_accel snd_seq snd_pcm snd_seq_device cm3218x snd_timer industrialio_triggered_buffer kfifo_buf snd industrialio soundcore goodix_backport(OE) battery mei_txe lpc_ich mei iosf_mbi dw_dmac rfkill_gpio mac_hid dw_dmac_core soc_button_array
[   33.546995]  snd_soc_sst_acpi i2c_designware_platform 8250_dw spi_pxa2xx_platform i2c_designware_core acpi_pad parport_pc ppdev lp parport autofs4 hid_generic usbhid hid mmc_block i915 i2c_algo_bit drm_kms_helper drm video sdhci_acpi sdhci
[   33.547029] CPU: 2 PID: 1020 Comm: Xorg Tainted: G        W  OE   4.2.0 #2
[   33.547033] Hardware name: WinBook TW802/TW802, BIOS 1.00 IA32 11/24/2014
[   33.547037]  ffffffffa01a76c8 ffff880074e93798 ffffffff81789eb9 0000000080000001
[   33.547045]  ffff880074e937e8 ffff880074e937d8 ffffffff810629dc ffff880074e937e0
[   33.547052]  ffff880075e74b50 ffff880075e74800 ffff880035c06000 0000000000000001
[   33.547059] Call Trace:
[   33.547069]  [<ffffffff81789eb9>] dump_stack+0x4f/0x7b
[   33.547077]  [<ffffffff810629dc>] warn_slowpath_common+0x8c/0xd0
[   33.547083]  [<ffffffff81062a68>] warn_slowpath_fmt+0x48/0x50
[   33.547118]  [<ffffffffa0138b17>] check_crtc_state+0x8e7/0x1010 [i915]
[   33.547160]  [<ffffffffa014c6f7>] intel_modeset_check_state+0x227/0xbe0 [i915]
[   33.547195]  [<ffffffffa0146a29>] ? __intel_set_mode+0x939/0xb80 [i915]
[   33.547231]  [<ffffffffa014de61>] intel_crtc_set_config+0x541/0x5a0 [i915]
[   33.547256]  [<ffffffffa004870e>] drm_mode_set_config_internal+0x6e/0x110 [drm]
[   33.547278]  [<ffffffffa004ce40>] drm_mode_setcrtc+0x190/0x4f0 [drm]
[   33.547296]  [<ffffffffa003d7a8>] drm_ioctl+0x1a8/0x650 [drm]
[   33.547304]  [<ffffffff8108cdb2>] ? get_parent_ip+0x12/0x60
[   33.547311]  [<ffffffff811e44e2>] do_vfs_ioctl+0x2c2/0x4a0
[   33.547316]  [<ffffffff811ee55a>] ? __fget+0x7a/0xb0
[   33.547322]  [<ffffffff811e473f>] SyS_ioctl+0x7f/0x90
[   33.547328]  [<ffffffff81072149>] ? SyS_rt_sigprocmask+0x89/0xb0
[   33.547335]  [<ffffffff8179096e>] entry_SYSCALL_64_fastpath+0x12/0x71
[   33.547340] ---[ end trace 11a920db2ca0a6d5 ]---
[   33.562853] [drm:check_crtc_state [i915]] *ERROR* mismatch in dpll_hw_state.dpll (expected 0x20002000, found 0x20000000)
[   33.562862] ------------[ cut here ]------------
[   33.562899] WARNING: CPU: 1 PID: 1020 at drivers/gpu/drm/i915/intel_display.c:12324 check_crtc_state+0x8e7/0x1010 [i915]()
[   33.562902] pipe state doesn't match!
[   33.562906] Modules linked in: ax88179_178a usbnet mii nls_iso8859_1 intel_rapl intel_soc_dts_thermal intel_soc_dts_iosf intel_powerclamp pn544_mei coretemp mei_phy pn544 kvm_intel snd_soc_sst_baytrail_pcm hci snd_soc_sst_ipc nfc kvm snd_soc_sst_dsp joydev snd_soc_sst_byt_rt5640_mach gpio_keys crc32_pclmul aesni_intel aes_x86_64 glue_helper lrw gf128mul ablk_helper cryptd snd_intel_sst_acpi snd_soc_rt5640 snd_intel_sst_core cm3218(OE) snd_soc_rl6231 snd_soc_sst_mfld_platform snd_soc_core snd_seq_midi snd_seq_midi_event snd_rawmidi snd_compress ac97_bus snd_pcm_dmaengine bmc150_accel snd_seq snd_pcm snd_seq_device cm3218x snd_timer industrialio_triggered_buffer kfifo_buf snd industrialio soundcore goodix_backport(OE) battery mei_txe lpc_ich mei iosf_mbi dw_dmac rfkill_gpio mac_hid dw_dmac_core soc_button_array
[   33.563000]  snd_soc_sst_acpi i2c_designware_platform 8250_dw spi_pxa2xx_platform i2c_designware_core acpi_pad parport_pc ppdev lp parport autofs4 hid_generic usbhid hid mmc_block i915 i2c_algo_bit drm_kms_helper drm video sdhci_acpi sdhci
[   33.563035] CPU: 1 PID: 1020 Comm: Xorg Tainted: G        W  OE   4.2.0 #2
[   33.563038] Hardware name: WinBook TW802/TW802, BIOS 1.00 IA32 11/24/2014
[   33.563042]  ffffffffa01a76c8 ffff880074e93798 ffffffff81789eb9 0000000080000001
[   33.563050]  ffff880074e937e8 ffff880074e937d8 ffffffff810629dc ffff880074e937e0
[   33.563057]  ffff880075e74b50 ffff880075e74800 ffff880035c06000 0000000000000001
[   33.563065] Call Trace:
[   33.563076]  [<ffffffff81789eb9>] dump_stack+0x4f/0x7b
[   33.563085]  [<ffffffff810629dc>] warn_slowpath_common+0x8c/0xd0
[   33.563091]  [<ffffffff81062a68>] warn_slowpath_fmt+0x48/0x50
[   33.563126]  [<ffffffffa0138b17>] check_crtc_state+0x8e7/0x1010 [i915]
[   33.563169]  [<ffffffffa014c6f7>] intel_modeset_check_state+0x227/0xbe0 [i915]
[   33.563204]  [<ffffffffa0146a29>] ? __intel_set_mode+0x939/0xb80 [i915]
[   33.563240]  [<ffffffffa014de61>] intel_crtc_set_config+0x541/0x5a0 [i915]
[   33.563265]  [<ffffffffa004870e>] drm_mode_set_config_internal+0x6e/0x110 [drm]
[   33.563288]  [<ffffffffa004ce40>] drm_mode_setcrtc+0x190/0x4f0 [drm]
[   33.563306]  [<ffffffffa003d7a8>] drm_ioctl+0x1a8/0x650 [drm]
[   33.563315]  [<ffffffff811e44e2>] do_vfs_ioctl+0x2c2/0x4a0
[   33.563321]  [<ffffffff811ee55a>] ? __fget+0x7a/0xb0
[   33.563327]  [<ffffffff811e473f>] SyS_ioctl+0x7f/0x90
[   33.563334]  [<ffffffff81072149>] ? SyS_rt_sigprocmask+0x89/0xb0
[   33.563340]  [<ffffffff8179096e>] entry_SYSCALL_64_fastpath+0x12/0x71
[   33.563346] ---[ end trace 11a920db2ca0a6d6 ]---
[   40.933946] FAT-fs (mmcblk1p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.

```

Any ideas what else should I try? Appreciate any help!

---

### Post by bmw-man on 2016-05-23
Anyone?

---

### Post by donquichot2016 on 2016-05-25
Have you tried adding **i915.force_backlight_pmic=1** to grub?

I guess xrandr (rotating the screen) is disabled by the **i915.modeset=0** option. Have you tried rotating manually with xrandr?:
```
xrandr --output DSI1  --rotate left
```
If you remove the **modeset** option from grub and reboot, does the screen come on after about 10 minutes?

---

### Post by bmw-man on 2016-05-27
I tried both suggestions with no luck. Booting with **i915.modeset=0** and then try **xrandr --output DSI1  --rotate left** produces an error. Booting with **i915.force_backlight_pmic=1** does nothing. Also waited 20min with each option, the screen never comes on. I found other suggestions in different threads and also tried this below:

acpi_backlight=vendor
video.use_bios_initial_backlight=0
video.use_native_backlight=1


In /etc/rc.local, just before exit 0, put a line setpci -s 00:02.0 F4.B=00

Any other ideas? Thanks!

---

### Post by Bashing-om on 2016-05-27
bmw-manl Uh Huh ;

> 
Any other ideas? Thanks!

Bay Trail == intel_idle.max_cstate=1 , as a boot parameter.
See: [http://ubuntuforums.org/showthread.php?t=2320259](http://ubuntuforums.org/showthread.php?t=2320259)

Try this as a boot parameter and advise on the result.

[INDENT][INDENT]the power of many
[/INDENT][/INDENT]

---

### Post by bmw-man on 2016-05-27
I already have [COLOR=#000000]**intel_idle.max_cstate=1** as boot parameter since I first installed the OS. Baytrail hardware freezes constantly without it. I don't think it has anything to do with the graphics, but I might be wrong.[/COLOR]

---

### Post by bmw-man on 2016-06-09
bump?

---

### Post by bmw-man on 2016-10-01
After hours of installing/rebooting/testing I found kernel 3.13.11. The Tablet screen (shows as VGA-1) and external HDMI work great, including dual display. The issue is that nothing else works, and there are no drivers for wifi/touchscreen/bluetooth for that old kernel. I can get all that working under 4.2 or higher, but then the screen is not working anymore. 

Is there a way to take some files/settings from 3.13 and copy to 4.2 kernel? I feel that I am close but still no luck.

---

