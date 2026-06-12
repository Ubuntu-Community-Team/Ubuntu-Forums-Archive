---
title: "Ubuntu 16.04 Sever freezes every day"
date: 2016-07-29
forum: Server Platforms
---

### Post by manuel42 on 2016-07-29
Hi,
I'm having lots of trouble with a server running UBUNTU Server 16.04. It freezes in a daily basis, mostly at night, when there are not users connected or processes running.

I don't have any clue about what could be the cause. I've already run memtest (no errors detected) and can't find nothing relevant on logs (I guess someone with appropiate skills could find something).

When my headless server freezes, it can behave in different ways:

- No SSH access at all (it asks for user/pass but then doesn't respond)
- Samba is out. SSH works very slowly. Power off or reboot commands doesn't respond. Systemd process is consuming huge amount of CPU but Kill the process doesn't work. Sometimes (very rare) even file system turns read-only ¿¿??

Any advice about where could I look for some clues about what is happening would be appreciated.

Thanks!

---

### Post by mastablasta on 2016-07-29
> **manuel42 said:**
>  Sometimes (very rare) even file system turns read-only ¿¿??


it goes into read only mode if there is an issue on disk. run smart to check the  system disk state (disk might be failing).

---

### Post by manuel42 on 2016-07-29
Hi mastablasta,

Thanks for the hint. This server has two drives so I've checked both using smartctl (long and short tests): "No Errors Logged".

:confused:

Regards.

---

### Post by Graham_Willis on 2016-07-30
Just copy the system to a VM, let it run for some time and check if you'll observe the same behaviour. If not - try to generate the same kind of traffic that's going on on the production machine and re-check the results. If the copied system behaves strangely, then you already know that it's a software problem. If not - then it might be or it might be not. But then, if it's feasible. try to cut off all the traffic on the firewall at night and see if it helps. If doesn't - try to killing processes (before the problem appears), perhaps you have a rogue service.

---

### Post by gordintoronto on 2016-07-30
What motherboard? I have a 7-year-old Gigabyte board which requires acpi=off.

Do you monitor CPU and memory usage?

---

### Post by MAFoElffen on 2016-07-31
Freezing on what hardware and running what services? (make, Model, CPU, RAM, Disk spec's; Services)

From the previous posts, I gather that you are running  at elast Samba(?) or at least connected to a Samba Share.

On servers that freeze intermittently, or no apparent reason-- CPU, RAM, Disk. Hard to diagnose a frozen machine when it is frozen, so check or generate logs to determine the events leading up to the frozen state. Of course, you need to check that you do not have a full disk, before you can generate additional logging, or else you just add to that problem.

Does that make sense? Those are hints, which can be expanded upon, if needed.

---

### Post by manuel42 on 2016-08-01
Thanks for your help [COLOR=#000000]Graham_Willis, [/COLOR][COLOR=#000000]gordintoronto and [/COLOR][COLOR=#000000]MAFoElffen.

This is a 1 year old ASUS desktop machine, 8 GB ram, 2TB HDD (with at least 1.8 free). This issues began after upgrade to 16.04. There where no issues with 14.04.

RAM tests where OK, as well as HDD tests. CPU and RAM usage are never over 50%.

This server is used as fileserver (Samba) and as a MySQL server. Today I'm going to try stopping Samba and check if it still freezes.

I guess I'll downgrade this server this week if I don't find how to fix it.

Thanks again. Your help is sincerely appreciated.

Regards.[/COLOR]

---

### Post by mastablasta on 2016-08-01
> **manuel42 said:**
> 

Thanks for the hint. This server has two drives so I've checked both using smartctl (long and short tests): "No Errors Logged".

.

you can use various diagnostic distros. i use ultimatebootcd to do various tests.

SMART status might be ok but you should check the values. if they are too much off for a young hard disk then it could indicate issues eventhough smart check is good. so far i had only 2 issues - small sample, so i am maybe not qualified to talk too much about this. one disk was failing with cliking and i couldn't boot always, smart was mostly good, one number was a bit off. exchanging the disk solved the issue.  next one was flash driver which keep dropping into read only. checking it with smart tools didn't reveal anything. specialised USB check software showed errors. so i had to resque the os from it and copy what i managed to save to new USB flash drive. all works well now.

---

### Post by MAFoElffen on 2016-08-01
Since you have verified that you have good disk, and plenty of disk... then create a cron job to append the top-5 stats from TOP, to a log file, every 5 minutes. Once a day, "move" (rename the file with the date) the file for review and cleanup.

That way you can see what the system was doing before it crashes, leading up to that crash. That way you can see if an application was building up on resources that it was not releasing... Like I said, you cannot get those machine sate stats from "memory" from a frozen machine, but if you log them, so they stay as persistent... another would be to check journalctl. 

Those are things I do, when trying to track something like that.. Of course, some crashes are just intermittently rouge.(and frustrating when trying to track down.) You could always use a management utility to track and log. But you would essentially be doing the same right?

---

### Post by manuel42 on 2016-08-02
I'm learning a lot these days :-) Thanks again. I know I'll find out the issue and fix it.

I've just found a new BIOs update to fix stability issues, so I've updated it. I'm also doing some research about diagnostic distros as mastablasta suggested, as well as the cron job to record stats until system halts (good one MAFoElffen!).

Maybe it's just fixed with the bios update. We'll know tomorrow! :-)

Regards.

---

### Post by manuel42 on 2016-08-03
Ok, this morning the server was KO again. :(

But, I found at syslog something just at the point where system problems begun. I don't have any idea what to do with this, but it looks like something is wrong with hardware. Make any sense to consider some issue with BIOS setup?

PS: I already did a downgrade to Ubuntu 14.04 as you can see without success.

> 

Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413098] ------------[ cut here ]------------Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413104] WARNING: CPU: 0 PID: 0 at /build/linux-lts-wily-Ejb_ce/linux-lts-wily-4.2.0/kernel/watchdog.c:311 watchdog_overflow_callback+0x8b/0xb0()
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413105] Watchdog detected hard LOCKUP on cpu 0
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413106] Modules linked in: iptable_filter ip_tables x_tables eeepc_wmi asus_wmi snd_hda_codec_hdmi sparse_keymap snd_hda_codec_realtek ppdev snd_hda_codec_generic lp nouveau intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd serio_raw mxm_wmi ttm drm_kms_helper snd_hda_intel drm btusb snd_hda_codec btrtl btbcm btintel snd_hda_core i2c_algo_bit bluetooth snd_hwdep snd_pcm snd_timer snd lpc_ich soundcore mei_me mei shpchp wmi 8250_fintek parport_pc parport video mac_hid uas usb_storage psmouse ahci r8169 libahci mii
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413127] CPU: 0 PID: 0 Comm: swapper/0 Not tainted 4.2.0-42-generic #49~14.04.1-Ubuntu
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413128] Hardware name: ASUS All Series/B85M-E, BIOS 2309 06/22/2016
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413129]  0000000000000000 ffff88021dc05b00 ffffffff817bc281 ffff88021dc05b50
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413130]  ffffffff81aa33b0 ffff88021dc05b40 ffffffff8107998a 0000000000000000
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413131]  ffff8802143a8800 0000000000000000 0000000000000000 ffff88021dc05c40
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413132] Call Trace:
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413133]  <NMI>  [<ffffffff817bc281>] dump_stack+0x63/0x81
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413139]  [<ffffffff8107998a>] warn_slowpath_common+0x8a/0xc0
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413140]  [<ffffffff81079a06>] warn_slowpath_fmt+0x46/0x50
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413141]  [<ffffffff8112c1ab>] watchdog_overflow_callback+0x8b/0xb0
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413143]  [<ffffffff8116f3ac>] __perf_event_overflow+0x8c/0x1c0
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413144]  [<ffffffff8116feb4>] perf_event_overflow+0x14/0x20
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413146]  [<ffffffff8103444e>] intel_pmu_handle_irq+0x1ce/0x450
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413149]  [<ffffffff8102b026>] perf_event_nmi_handler+0x26/0x40
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413150]  [<ffffffff810195fd>] nmi_handle+0x7d/0x120
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413152]  [<ffffffff81019bcf>] default_do_nmi+0xbf/0x110
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413153]  [<ffffffff81019d05>] do_nmi+0xe5/0x160
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413155]  [<ffffffff817c59d1>] end_repeat_nmi+0x1a/0x1e
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413157]  [<ffffffff810c1380>] ? native_queued_spin_lock_slowpath+0x160/0x170
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413158]  [<ffffffff810c1380>] ? native_queued_spin_lock_slowpath+0x160/0x170
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413160]  [<ffffffff810c1380>] ? native_queued_spin_lock_slowpath+0x160/0x170
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413160]  <<EOE>>  <IRQ>  [<ffffffff817b5c08>] queued_spin_lock_slowpath+0xb/0xf
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413164]  [<ffffffff817c34c7>] _raw_spin_lock_irqsave+0x37/0x40
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413186]  [<ffffffffc05452bf>] nvkm_fantog_update+0x4f/0x120 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413197]  [<ffffffffc05453e5>] nvkm_fantog_set+0x35/0x40 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413207]  [<ffffffffc054493f>] nvkm_fan_update+0xef/0x1b0 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413215]  [<ffffffffc0544a59>] nvkm_therm_fan_set+0x19/0x20 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413224]  [<ffffffffc05441fd>] nvkm_therm_update+0xad/0x2d0 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413232]  [<ffffffffc054443a>] nvkm_therm_alarm+0x1a/0x20 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413242]  [<ffffffffc054794f>] nv04_timer_alarm_trigger+0x11f/0x160 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413250]  [<ffffffffc0547a05>] nv04_timer_alarm+0x75/0xd0 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413259]  [<ffffffffc0545381>] nvkm_fantog_update+0x111/0x120 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413267]  [<ffffffffc05453aa>] nvkm_fantog_alarm+0x1a/0x20 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413275]  [<ffffffffc054794f>] nv04_timer_alarm_trigger+0x11f/0x160 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413283]  [<ffffffffc0547ac4>] nv04_timer_intr+0x64/0x80 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413293]  [<ffffffffc053eb28>] nvkm_mc_intr+0xf8/0x150 [nouveau]
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413294]  [<ffffffff810d0da4>] handle_irq_event_percpu+0x44/0x1d0
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413296]  [<ffffffff810d0f79>] handle_irq_event+0x49/0x70
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413297]  [<ffffffff810d40dd>] handle_edge_irq+0x9d/0x150
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413298]  [<ffffffff81018255>] handle_irq+0x25/0x40
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413299]  [<ffffffff817c62f1>] do_IRQ+0x51/0xe0
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413300]  [<ffffffff817c426b>] common_interrupt+0x6b/0x6b
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413301]  <EOI>  [<ffffffff8165b838>] ? cpuidle_enter_state+0xd8/0x250
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413304]  [<ffffffff8165b814>] ? cpuidle_enter_state+0xb4/0x250
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413305]  [<ffffffff8165b9e7>] cpuidle_enter+0x17/0x20
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413306]  [<ffffffff810ba332>] call_cpuidle+0x32/0x60
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413307]  [<ffffffff8165b9c3>] ? cpuidle_select+0x13/0x20
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413308]  [<ffffffff810ba5f7>] cpu_startup_entry+0x297/0x360
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413310]  [<ffffffff817ac1ac>] rest_init+0x7c/0x80
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413312]  [<ffffffff81d5311f>] start_kernel+0x4b0/0x4bd
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413313]  [<ffffffff81d52a54>] ? set_init_arg+0x57/0x57
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413314]  [<ffffffff81d52120>] ? early_idt_handler_array+0x120/0x120
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413315]  [<ffffffff81d525ee>] x86_64_start_reservations+0x2a/0x2c
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413316]  [<ffffffff81d5272d>] x86_64_start_kernel+0x13d/0x14c
Aug  2 20:06:39 ubuntuserver kernel: [ 7731.413317] ---[ end trace 973127c512d8ad8e ]---




---

### Post by MAFoElffen on 2016-08-03
Still have that log? What were the previous 20 lines before that? (So I can see anything related to the modules that were loaded at that time...)

And what revision # is your B85M-E mother board? Just looking at the change logs on their BIOS updates.

---

### Post by manuel42 on 2016-08-03
Sure!

You'll see in this log this entries:

Aug  2 20:00:01 ubuntuserver CRON[2536]: (manuel) CMD (/home/manuel/scripts/./report) - Script where I send evey hour an email attaching the output of "top -n 1 -b".

I received that output at 18h perfectly. But at 19h and 20h I just received a 0kb file with no data, so I guess the issue we are looking for begun between 18h and 19h.

Thats the log between 18h and what I already shared.

> 
Aug  2 18:00:01 ubuntuserver CRON[1463]: (manuel) CMD (/home/manuel/scripts/./report)
Aug  2 18:00:02 ubuntuserver sSMTP[1476]: Creating SSL connection to host
Aug  2 18:00:02 ubuntuserver sSMTP[1476]: SSL connection using RSA_AES_128_CBC_SHA1
Aug  2 18:00:05 ubuntuserver sSMTP[1476]: Sent mail for manuel@localhost (221 2.0.0 closing connection k3sm3294592wjf.7 - gsmtp) uid=1000 username=manuel outbytes=19443
Aug  2 18:09:01 ubuntuserver CRON[1504]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Aug  2 18:17:01 ubuntuserver CRON[1543]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  2 18:39:01 ubuntuserver CRON[1859]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Aug  2 19:00:02 ubuntuserver CRON[2037]: (manuel) CMD (/home/manuel/scripts/./report)
Aug  2 19:00:02 ubuntuserver sSMTP[2049]: Creating SSL connection to host
Aug  2 19:00:02 ubuntuserver sSMTP[2049]: SSL connection using RSA_AES_128_CBC_SHA1
Aug  2 19:00:04 ubuntuserver sSMTP[2049]: Sent mail for manuel@localhost (221 2.0.0 closing connection c16sm3919084wme.4 - gsmtp) uid=1000 username=manuel outbytes=2217
Aug  2 19:09:01 ubuntuserver CRON[2068]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Aug  2 19:17:01 ubuntuserver CRON[2108]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  2 19:39:01 ubuntuserver CRON[2386]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Aug  2 20:00:01 ubuntuserver CRON[2536]: (manuel) CMD (/home/manuel/scripts/./report)
Aug  2 20:00:01 ubuntuserver sSMTP[2548]: Creating SSL connection to host
Aug  2 20:00:01 ubuntuserver sSMTP[2548]: SSL connection using RSA_AES_128_CBC_SHA1
Aug  2 20:00:04 ubuntuserver sSMTP[2548]: Sent mail for manuel@localhost (221 2.0.0 closing connection xa2sm3750492wjc.0 - gsmtp) uid=1000 username=manuel outbytes=2217


Regards.

---

### Post by manuel42 on 2016-08-03
> **MAFoElffen said:**
> And what revision # is your B85M-E mother board? Just looking at the change logs on their BIOS updates.

I'm trying to figure out where can I find the revision #, but didn't find yet.

Edited: I found something. Hope is what you asked for

> 
# dmidecode 2.12
SMBIOS 2.7 present.


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASUSTeK COMPUTER INC.
        Product Name: B85M-E
**        Version: Rev X.0x**
        Serial Number: 150749136306354
        Asset Tag: To be filled by O.E.M.
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: To be filled by O.E.M.
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0


---

### Post by QDR06VV9 on 2016-08-03
One method:
```
inxi -M
```

---

### Post by manuel42 on 2016-08-03
Thanks runrickus!

That's it:

> 

Machine:   System: ASUS product: All Series
           Mobo: ASUSTeK model: B85M-E version: Rev X.0x serial: 150749136306354
           Bios: American Megatrends version: 2309 date: 06/22/2016




---

### Post by manuel42 on 2016-08-04
Fixed! :D

After an Nvidia driver update, it looks like server is stable again. I'm not sure if it was just the graphic card driver or not, because with the driver I installed the lighter version of unity desktop (with --no-install-recommends argument) and I don't know for sure if that fixed in other way the issue.

The important thing: server was ok this morning and I can take may summer holidays...

[LIST=1]
[*]Without worries about this particular issue
[*]With several interesting and collateral stuff I've learned along the proccess
[*]With my first experience at Ubuntu forums, that has been great.
[/LIST]

Lots of thanks for your help and support!

Regards.

---

### Post by manuel42 on 2016-08-04
Bonus track:

For the record, these are the steps I followed, with a GeForce GT 730:

```


sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt-get install nvidia-340
sudo apt-get install --no-install-recommends ubuntu-desktop
sudo shutdown -r now


```

Regards.

---

### Post by mastablasta on 2016-08-04
> **manuel42 said:**
> GeForce GT 730

this card should work flawlesly on linux. and for many it does. however i too had issues i battled for 4 or 5 days. couldn't get it to boot, loaded and unloaded various drivers. and in the end i returned it to the shop. many companies manfucature it but it seem some do not do a good job.

---

