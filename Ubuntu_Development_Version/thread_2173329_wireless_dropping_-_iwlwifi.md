---
title: "wireless dropping - iwlwifi"
date: 2013-09-09
forum: Ubuntu Development Version
---

### Post by miobrad on 2013-09-09
dear forum,

my wireless card (Intel Corporation Centrino Ultimate-N 6300) on my thinkapd X201T is giving my a headache. 
it was dropping very often during boot already, and only sometimes it would make it for maybe an hour or so and 
then disappear. one of the most common error messages i see when looking at the dmesg output is:

iwlwifi 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 2000ms

yesterday i installed 13.10 in the hope that it would change (the problems started with 13.04 i think, 
maybe it was already 12.10, but definitely after an distribution upgrade) but same thing again. 

so i did an other search and found that creating the file /etc/modprobe.conf with this line..:

options iwlwifi wd_disable=0

does improve the condition. i can now have the wireless working for hours but eventually it still fails. 
again i find the above mentioned error message.

i also tried creating a /etc/pm/config.d/config file with the following lines:

options iwlwifi bt_coex_active=0
options iwlwifi 11n_disable=1

but that made the system even more unstable, suspend/resume was extremly unstable with the system 
becoming unresponsive, so i deleted it again.

does anybody have the same problem? i think i have searched and tried all suggested solutions, 
maybe i overlooked something?

happy about any help/suggestions!

---

### Post by varunendra on 2013-09-09
> **miobrad said:**
> 
so i did an other search and found that creating the file **/etc/modprobe.conf** with this line..:

options iwlwifi wd_disable=0
....<snip>....
i also tried creating a **[COLOR="#FF0000"]/etc/pm/config.d/config[/COLOR]** file with the following lines:

options iwlwifi bt_coex_active=0
options iwlwifi 11n_disable=1

I don't think the last two options can make system unstable, maybe it was because they were in a wrong place, thus being used in a wrong way. You can have all these options in one line and the best place for the conf file is /etc/modprobe.d. Accordingly, I'd suggest to create a new one in this 'best' place and delete the other one (assuming it didn't exist before 'You' created it) :
```
echo "options iwlwifi wd_disable=0 bt_coex_active=0 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo rm /etc/modprobe.conf
```

Personally, I would recommend to try only one parameter at a time, more if one alone doesn't help, in this sequence -
[LIST=1]
[*]First only "swcrypto=1",
[*]Next, "swcrypto=1" and "wd_disable=0", since you have had better experience with that option,
[*]Next, also add "bt_coex_active=0" to above, or with just "swcrypto=1" if above didn't seem to improve things.
[*]"11n_disable=1" is something I would try in the last. Although it seems to help quite often, it is a compromise with N-channel speeds. But if your router doesn't use N-channel (or if you don't get that speed anyway..) then of course make it one of the first changes.
[/LIST]

If none of the above helps, please post the outputs of -
```
iwconfig
nm-tool
sudo iwlist scan
grep -iR [0-9a-z] /sys/module/iwlwifi/parameters
```

---

### Post by miobrad on 2013-09-10
wow, i had this problem for such a long time now and yesterday i decided to open up the laptop and take out/put back in the wireless. 
see if the contacts are all fine - i have good experience with doing that with my laptops. well, it did not help as such as the problem occured
again but i realized something - the problem only occurs if i carry the laptopo around. i used to never have the problem at work. i thought 
that was due to a different network setup, but at work my laptop just sat at the desk all day, and at home, where i have the problem, i walk
around with it. so after that i just tried to carry it gently, and true enough the wireless did not drop. on the other hand, it did not take much
shacking to get it to drop. 

so, i conclude - while my settings in the wrong place might have made the suspend/resume unstable, it seems obvious now that it is a
hardware/bad contact problem.

thank you so much for the comprehensive reply, i'm not sure if i should try any of it now. i did start but stopped again after i saw that 
i already had a /etc/modprobe.d/iwlwifi.conf file, this is the content:
```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```

your code would have overwritten that.. so, if i choose to try this (in case it turns out that i have problems not related
to the bad contact, i'm really not sure now) should i just overwrite this file, or should i add the things you suggested
at the start/end of this file?

ah well, there we go - carrying my laptop gently from now on :) 

thanks so much!

---

### Post by varunendra on 2013-09-10
> **miobrad said:**
> ..i saw that 
i already had a /etc/modprobe.d/iwlwifi.conf file, this is the content:
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

your code would have overwritten that.. so, if i choose to try this (in case it turns out that i have problems not related
to the bad contact, i'm really not sure now) should i just overwrite this file, or should i add the things you suggested
at the start/end of this file?

Thanks for bringing that to our attention. I was not aware of the presence of that file. But I'm not sure what might have created that file and whether it can do what it says in the comments (doesn't exist in 12.04, not sure about 13.04). If it is a system default file in 13.04, then by practical experience I can say that it does not do what it seems to be meant for.

However, to be on safe side, I'd suggest to just backup the file (in the unlikely case it is required during some particular operation, like a sleep/wakeup cycle), then create a fresh one. At least it will let us try what we intend to without doubts.
```
sudo mv /etc/modprobe.d/iwlwifi.conf iwlwifi.conf.bak
echo "options iwlwifi wd_disable=0 bt_coex_active=0 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```
...plus removing the other file as mentioned in my previous post.

You may already understand that you will need to unload - reload the iwldvm and iwlwifi modules, or reboot for the change to take effect.

**PS:**
While posting anything that is a code (e.g. the contents of the .conf file), you might wish to use 'Code' tags to make it clear and distinguished from the normal text. Please follow the "Using Code tags" link in my signature to see how. :)

---

### Post by mcellius on 2013-09-10
> wow, i had this problem for such a long time now and yesterday i decided  to open up the laptop and take out/put back in the wireless. 
see if the contacts are all fine - i have good experience with doing  that with my laptops. well, it did not help as such as the problem  occured
again but i realized something - the problem only occurs if i carry the  laptopo around. i used to never have the problem at work. i thought 
that was due to a different network setup, but at work my laptop just  sat at the desk all day, and at home, where i have the problem, i walk
around with it. so after that i just tried to carry it gently, and true  enough the wireless did not drop. on the other hand, it did not take  much
shacking to get it to drop.

I'm impressed!  That would be a very difficult problem to track down.  Congratulations on finding what was causing the problem (although it's probably more annoying because the fix will cost you a bit, at least).

---

### Post by miobrad on 2013-09-18
thank you very much. i did what you said and things improved a lot, and i played around toggling wd_disable but i am not sure what is better. eventually thought (but now only after days sometimes) it still fails.. 

one thing i wanted to ask, once the wirless drops, i have to restart the laptop for it to work again. when i do 

sudo rmmod iwldvm
sudo rmmod iwlwifi
sudo modprobe iwlwifi

all the modules will have been removed/reloaded but the wireless does not show up again. looking at what happens with dmesg:

```
[ 6218.927760] Intel(R) Wireless WiFi driver for Linux, in-tree:
[ 6218.927768] Copyright(c) 2003-2013 Intel Corporation
[ 6218.940304] iwlwifi 0000:02:00.0: Refused to change power state, currently in D3
[ 6218.940449] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 6218.940634] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[ 6218.949578] iwlwifi 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[ 6218.993274] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 6218.993284] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 6218.993288] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 6218.993292] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[ 6218.993297] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0xFFFFFFFF
[ 6218.993344] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 6219.010580] ------------[ cut here ]------------
[ 6219.010608] WARNING: CPU: 1 PID: 3509 at /build/buildd/linux-3.11.0/drivers/net/wireless/iwlwifi/pcie/trans.c:883 iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]()
[ 6219.010612] Timeout waiting for hardware access (CSR_GP_CNTRL 0xffffffff)
[ 6219.010614] Modules linked in: iwldvm(+) iwlwifi parport_pc(F) ppdev(F) bnep rfcomm bluetooth arc4(F) mac80211 intel_powerclamp coretemp kvm(F) joydev(F) binfmt_misc(F) snd_hda_codec_hdmi snd_hda_codec_conexant uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev microcode(F) snd_hda_intel snd_hda_codec psmouse(F) snd_hwdep(F) serio_raw(F) cfg80211 snd_pcm(F) intel_ips lpc_ich i915 snd_page_alloc(F) mei_me drm_kms_helper mei drm thinkpad_acpi nvram(F) snd_seq_midi(F) snd_seq_midi_event(F) i2c_algo_bit snd_rawmidi(F) wmi snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) tpm_tis mac_hid video(F) lp(F) parport(F) ahci(F) libahci(F) e1000e(F) ptp(F) pps_core(F) [last unloaded: iwlwifi]
[ 6219.010703] CPU: 1 PID: 3509 Comm: modprobe Tainted: GF       W    3.11.0-7-generic #13-Ubuntu
[ 6219.010707] Hardware name: LENOVO 2985FUG/2985FUG, BIOS 6QET53WW (1.23 ) 09/15/2010
[ 6219.010710]  00000000 00000000 eea31c50 c16313c4 eea31c90 eea31c80 c105268e f9404510
[ 6219.010720]  eea31cac 00000db5 f94042ec 00000373 f93f8276 f93f8276 eed7c000 eed7dea8
[ 6219.010730]  eea31cdc eea31c98 c10526e3 00000009 eea31c90 f9404510 eea31cac eea31cc0
[ 6219.010740] Call Trace:
[ 6219.010754]  [<c16313c4>] dump_stack+0x41/0x52
[ 6219.010763]  [<c105268e>] warn_slowpath_common+0x7e/0xa0
[ 6219.010778]  [<f93f8276>] ? iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]
[ 6219.010792]  [<f93f8276>] ? iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]
[ 6219.010798]  [<c10526e3>] warn_slowpath_fmt+0x33/0x40
[ 6219.010812]  [<f93f8276>] iwl_trans_pcie_grab_nic_access+0xc6/0xd0 [iwlwifi]
[ 6219.010824]  [<f93ec240>] iwl_write_prph+0x20/0x90 [iwlwifi]
[ 6219.010838]  [<f93f7d84>] iwl_pcie_apm_init+0x154/0x200 [iwlwifi]
[ 6219.010852]  [<f93f83dd>] iwl_trans_pcie_start_hw+0x4d/0x1c0 [iwlwifi]
[ 6219.010865]  [<f93edbe9>] ? __iwl_info+0x39/0x70 [iwlwifi]
[ 6219.010883]  [<f95c2846>] iwl_op_mode_dvm_start+0x206/0xb80 [iwldvm]
[ 6219.010894]  [<c1266785>] ? __create_file+0xd5/0x2a0
[ 6219.010907]  [<f93ec7ec>] _iwl_op_mode_start.isra.2+0x3c/0xa0 [iwlwifi]
[ 6219.010918]  [<f93ec8dc>] iwl_opmode_register+0x8c/0xb0 [iwlwifi]
[ 6219.010925]  [<f8e60000>] ? 0xf8e5ffff
[ 6219.010939]  [<f8e60035>] iwl_init+0x35/0x1000 [iwldvm]
[ 6219.010947]  [<c10020ca>] do_one_initcall+0xca/0x190
[ 6219.010957]  [<c10e3158>] ? tracepoint_module_notify+0x118/0x180
[ 6219.010963]  [<f8e60000>] ? 0xf8e5ffff
[ 6219.010971]  [<c104866f>] ? set_memory_nx+0x5f/0x70
[ 6219.010981]  [<c10b4a1e>] load_module+0x10ce/0x18d0
[ 6219.010990]  [<c10b52af>] SyS_init_module+0x8f/0xf0
[ 6219.011005]  [<c163eacd>] sysenter_do_call+0x12/0x28
[ 6219.011009] ---[ end trace 7742123bca97c64d ]---
[ 6219.028319] iwlwifi 0000:02:00.0: bad EEPROM/OTP signature, type=OTP, EEPROM_GP=0x00000007
[ 6219.028328] iwlwifi 0000:02:00.0: EEPROM not found, EEPROM_GP=0xffffffff
[ 6219.028333] iwlwifi 0000:02:00.0: Unable to init EEPROM

```

would you know form this what is going on? 
how do i reset the wireless card so that i don't have to reboot the laptop? 
which modules should i remove/reload?

thank you for any comments/hints!!!

---

### Post by varunendra on 2013-09-18
> **miobrad said:**
> 
```
[ 6219.028319] iwlwifi 0000:02:00.0: bad EEPROM/OTP signature, type=OTP, EEPROM_GP=0x00000007
[ 6219.028328] iwlwifi 0000:02:00.0: [COLOR="#FF0000"]EEPROM not found, EEPROM_GP=0xffffffff[/COLOR]
[ 6219.028333] iwlwifi 0000:02:00.0: [COLOR="#FF0000"]Unable to init EEPROM[/COLOR]

```

I'm out of my comfort zone at the moment, and mostly out of mind too.. so just a quick shot (guesses on explanation later..) - when it gets stuck like this, does a sleep - wake up cycle help? Problems caused by power save options are usually solved by this trick.

Shall take a closer look when I'm home again (maybe tonight, maybe tomorrow), and shall post if found a clue.

---

### Post by miobrad on 2013-09-18
thank you, i tried and went into suspend - it would wake up again. i restarted and the wireless was not working to begin with. 
the settings where:
/etc/modprobe.d$ cat iwlwifi.conf 
options iwlwifi wd_disable=1 bt_coex_active=0 11n_disable=1

so i set changing wd_disable=0 again and restarted, wireless worked. now i'm waiting for the next time it drops, 
i will then again try the whole cycle again (unload/reload the modules, look at dmesg and try to suspend/wake up)

thanks again!!

---

