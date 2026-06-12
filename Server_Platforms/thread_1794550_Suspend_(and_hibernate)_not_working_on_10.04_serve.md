---
title: "Suspend (and hibernate) not working on 10.04 server"
date: 2011-07-01
forum: Server Platforms
---

### Post by bjaanes on 2011-07-01
Hi,

I have a headless 10.04 ubuntu server ( running at home. Because I am a student I want to save some power by suspending the server when I really don't need it (school, sleep etc.). I have gotten WOL to work for me, BUT the suspend does not work.

I have tried pm-suspend and s2ram, but they both have same result; I lose all control (seems like a freeze) from my SSH, but it does not disconnect, and the server responds to pings. But I cant connect via ssh, or use the fileserver or any of the roles it has.

I assume there might be something locking it when it tries to suspend, but I really don't know where to start looking (logs and stuff). I have googled quite a bit, but almost all failed suspends are some funky laptop issues, and this is not...

Any tips, or some more info you guys need?

---

### Post by Toz on 2011-07-01
The log file is **/var/log/pm-suspend**.

---

### Post by a2j on 2011-07-01
it only takes a minute to shutdown/boot up...

---

### Post by bjaanes on 2011-07-01
Well, i want suspend - I've got my reasons. I didnt really ask for any alternatives to supsend, I just want suspend to work ;)

Here is output from my last try to suspend. I really don't see anything in particular...

```
Initial commandline parameters:
Fri Jul  1 15:26:30 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux retard01 2.6.32-32-ser                                                                                                                                                             ver #62-Ubuntu SMP Wed Apr 20 22:07:43 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
snd_hda_codec_analog    78702  1
fbcon                  39270  71
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  1
vgastate                9857  1 vga16fb
ipt_REJECT              2384  1
xt_comment              1032  2
ipt_LOG                 5370  5
xt_multiport            2794  2
xt_limit                2180  7
xt_tcpudp               2667  16
ipt_addrtype            2055  4
xt_state                1490  7
arc4                    1473  2
ip6table_filter         1712  1
ip6_tables             19428  1 ip6table_filter
nf_nat_irc              1577  0
nf_conntrack_irc        4429  1 nf_nat_irc
nf_nat_ftp              2513  0
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      12742  9 nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
nf_conntrack_ftp        7126  1 nf_nat_ftp
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,                                                                                                                                                             nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1841  1
nouveau               515227  0
snd_hda_intel          25805  0
rtl8187                53204  0
ttm                    60815  1 nouveau
ip_tables              18201  1 iptable_filter
mac80211              238832  1 rtl8187
led_class               3764  1 rtl8187
drm_kms_helper         30742  1 nouveau
snd_hda_codec          85663  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6778  1 snd_hda_codec
ppdev                   6375  0
x_tables               22361  10 ipt_REJECT,xt_comment,ipt_LOG,xt_multiport,xt_l                                                                                                                                                             imit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
parport_pc             29958  1
snd_pcm                87312  2 snd_hda_intel,snd_hda_codec
psmouse                64576  0
serio_raw               4950  0
cfg80211              148341  2 rtl8187,mac80211
eeprom_93cx6            1765  1 rtl8187
drm                   198470  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
i2c_nforce2             6099  0
asus_atk0110           10033  0
edac_core              45423  0
edac_mce_amd            9278  0
snd_timer              23617  1 snd_pcm
snd                    71074  6 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec                                                                                                                                                             ,snd_hwdep,snd_pcm,snd_timer
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
k8temp                  4040  0
lp                      9336  0
parport                37160  3 ppdev,parport_pc,lp
ohci1394               30260  0
ieee1394               94771  1 ohci1394
sata_sil24             12903  0
sata_nv                23714  5
pata_amd               11962  0
forcedeth              55624  0
             total       used       free     shared    buffers     cached
Mem:       4056916     437580    3619336          0      94292     106724
-/+ buffers/cache:     236564    3820352
Swap:      3004408          0    3004408
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
Allocated buffer at 0x11000 (base is 0x0)
ES: 0x1100 EBX: 0x0000
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Fri Jul  1 15:26:31 CEST 2011: performing suspend
```

I just write:
$ sudo pm-suspend


And then nothing happens, no new prompt. Its like its working, but nothing is really happening - and i cant use the server (have to press the reset button).

Any tips?

( And btw, sorry for not knowing the whereabout of the log file - its been a little while since I have used any Linux, just started up again. Still a bit rusty :/ )

---

### Post by Toz on 2011-07-01
The only thing of interest in the log file is that there aren't any resume hooks running. You mentioned that you can't resume the system, but how do you try to resume it? Do you press a key or press the power button once briefly? Does anything of interest show up in **/var/log/syslog** during the suspend cycle?

I also notice that you have an nvidia card. Which one? Do you have an **/etc/X11/xorg.conf** file? If so, can you post back the contents. And, can you post back the contents of **/var/log/Xorg.0.log**? 

One way to test and rule out the video driver is to boot in recovery mode (no X) and issue a **pm-suspend** at the command line and see if suspend/resume works.

---

### Post by bjaanes on 2011-07-01
Well, i basicly just assumed it didnt even suspend, on account of there not beeing any less power consumption (all fans, disk and "lights" still running). Also, as I said, the system respons to ping. 

However, I have now tried resuming with magic packets and pressing the power button, but still no response from file server or SSH. 

I assume no X is running on account of this beeing server installation with only command line. I have basicly just used the graphics card for a way to connect a moniter when I first installed the system. After that I have only connected via SSH. I didnt fint any xorg.conf file in the X11 directory. The nVidia card is a 9800GT if I am not mistaken (just threw something in that I had laying around)

I dont really get the feeling the system is suspended.

About the syslog file, this is what happend during the suspend:

```
Jul  2 00:14:48 retard01 kernel: [23427.747332] CPU0 attaching NULL sched-domain.
Jul  2 00:14:48 retard01 kernel: [23427.747337] CPU1 attaching NULL sched-domain.
Jul  2 00:14:48 retard01 kernel: [23427.790075] CPU0 attaching sched-domain:
Jul  2 00:14:48 retard01 kernel: [23427.790079]  domain 0: span 0-1 level MC
Jul  2 00:14:48 retard01 kernel: [23427.790081]   groups: 0 1
Jul  2 00:14:48 retard01 kernel: [23427.790086] CPU1 attaching sched-domain:
Jul  2 00:14:48 retard01 kernel: [23427.790088]  domain 0: span 0-1 level MC
Jul  2 00:14:48 retard01 kernel: [23427.790089]   groups: 1 0
Jul  2 00:14:48 retard01 kernel: [23427.822818] [UFW BLOCK] IN=eth0 OUT= MAC=*******************************SRC=************* DST=************ LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=6488 DF PROTO=TCP SPT=62693 DPT=135 WINDOW=8192 RES=0x00 SYN URGP=0
``` Just edited out the MAC and IP addresses

Anything to make from it?

---

### Post by Toz on 2011-07-01
No - nothing important there. What happens if you try to suspend directly - no pm-utils or uswsusp? As root,
```
echo mem > /sys/power/state
```

---

### Post by bjaanes on 2011-07-01
The exact same thing happens with that.

Anything else I can try, or somewhere else I can look? :S

---

### Post by Toz on 2011-07-01
I'm out of ideas. Might I suggest [https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting]("https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting") - a suspend/resume stress test that upon failure, will automatically create a bug report? It would be interesting to see what the bug report contains.

---

### Post by bjaanes on 2011-07-02
Hmm... Well I tried the script and it failed badly, but the script is supposed to ask me to upload a bug report - but Im guessing that might be because its headless :P

Either way, I didnt really find the log file for this. Know where to find it?

But I have noticed that the command "shutdown now" also appears to be failing in the same way as with suspend. Does that give you any more ideas. Any specific scripts that run both when shut down and suspended? "halt" or "poweroff" does however shut down just fine, but I have understood that those doesnt shut down as nice as the shutdown command :)

---

### Post by Toz on 2011-07-02
According to that web page, it should ask you to create a bug report when you restart. Maybe you need to restart the test? I just realized that there is a server-specific version of that test:```
sudo /usr/share/checkbox/scripts/suspend_test --server
```

To shutdown, try:```
shutdown -h now
```

There is also this page: [https://wiki.ubuntu.com/DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend") about setting up a trace to see exactly what is happening - trying to identify the driver that is preventing suspend.

---

### Post by bjaanes on 2011-07-02
"shutdown -h now" work fine from SSH.

I finally tried to attach a monitar and a keyboard to suspend directory (not via SSH) - and that worked just fine!

So suspend over SSH, not the best idea? :S


EDIT:
I just made a script that seems to be working fine:
```

#!/bin/bash
sleep 10
pm-suspend

exit

```

So i just run it like this:
```
sudo nohup script.sh &
```

That gives me time to log out of the session, even though I found out that I really didnt need to, but I want it to be somewhat clean =)

---

