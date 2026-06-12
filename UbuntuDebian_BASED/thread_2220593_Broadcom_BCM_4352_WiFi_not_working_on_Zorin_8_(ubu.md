---
title: "Broadcom BCM 4352 WiFi not working on Zorin 8 (ubuntu based)"
date: 2014-04-28
forum: Ubuntu/Debian BASED
---

### Post by keratos2 on 2014-04-28
I'm moving from Windows7 to linux and have installed Zorin v8.1 as this is supposed to be most friendly linux for windows users. I love it. Speed is excellent. However, the wifi doesnt work. After much googling I managed to use some "apt-get install" command to install some bcm kernel sources and drivers. It was just one package - [FONT=Ubuntu Mono]bcmwl-kernel-source
[/FONT]
This installed a "wl" driver and I have a connection, however, it is crap and no where near as reliable or good as the connection in windows 7. I know its not the hardware because it works fine under windows7. I sit in my chair next to the router and get one bar. I used to get 5 bars. This translates to -55db and -32db respectively. 

How to install the LATEST broadcom propietary driver ? I have no idea what version of ubuntu I'm on - sorry - but I'm supposed to be on some ubuntu base (saucy appears in the /etc/apt files)

I'm loosing the will to live so can someone please help - if you could avoid posting just that I "suggest" or "try" or 'google" or  something like this, I'd be obliged - what I need is someone who is an expert in this field and has the answer. Thank you for your kind understanding.

---

### Post by chili555 on 2014-04-28
>  if you could avoid posting just that I "suggest" or "try" or 'google" or something like this, I'd be obliged - what I need is someone who is an expert in this field and has the answer. I can asssure you that noone here runs Zorin, has a Broadcom 4352 and _*knows *_the answer. If you'd like to wait around and hope one appears, as you continue to lose your will to live, you are certainly welcome to do so. There are two or three people here that know quite a bit about Broadcom wireless and I modestly include myself there. If you'd like for me to suggest some things that I've learned in 20,000+ posts (not all on this forum) and twelve years in Linux, I will be happy to help. If you want me to swear to you that two clicks and your problems are solved, I just can't do that.

Please tell us more about your device. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn -d 14e4:
sudo dpkg -s bcmwl-kernel-source
```The latter command is intended to tell us the version of your driver. I suspect it is 6.30.223.141. For comparison, the latest version at Broadcom's site is here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) As you can see, it's the same.

There may be other things we can do aside from the usual Windows technique of installing yet another driver.

---

### Post by keratos2 on 2014-04-29
thank you Sir Chill!
what I was trying to avoid was a non-value add response ,  as I have had many times in forums, like "oh it works for me have you tried reinstalling" - which increases "their" post count (kudos) , places my thread out of the "zero responses" bucket and is to be frank and candid if I may, absolutely unhelpful crap - I dont know why they bother.

Aside,
I dont know how you learn all this, the cryptic linux commands,  and even able to predict my driver, which is indeed as you indicated. As requested...

(p.s. Im using the "wl" driver which ive provided the modinfo response to if it helps?)

```
az@daz-VPCF11S1E:~$ lspci -nn -d 14e4:
02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
daz@daz-VPCF11S1E:~$ ^C
daz@daz-VPCF11S1E:~$ 


sudo dpkg -s bcmwl-kernel-source
[sudo] password for daz: 
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 5662
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 6.30.223.141+bdcom-0ubuntu1
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d*sv*sd*bc02sc80i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>
daz@daz-VPCF11S1E:~$ 

daz@daz-VPCF11S1E:~$ modinfo wl
filename:       /lib/modules/3.11.0-17-generic/updates/wl.ko
license:        MIXED/Proprietary
srcversion:     F09EC4762307349676747C4
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string
daz@daz-VPCF11S1E:~$
```

---

### Post by chili555 on 2014-04-29
> I dont know how you learn all this, the cryptic linux commands, and even able to predict my driver, which is indeed as you indicated. It's a long, sad story. I need to get a life or, at least, a less weird hobby! Sadly, I mess with Broadcoms and Ubuntu and Mint for several hours a day, every day for no compensation. Sad. 

You have a working, although badly, driver and hardware combination. Frankly, that's half or more of the battle. Let's see if there are any clues in the logs that help us:```
dmesg | grep -e wlan -e wl -e 80211
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```There are some things I've learned over the years that may help. 

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit.

---

### Post by keratos2 on 2014-04-29
My router is AC56U with stock f/w (latest from ASUS website)

My laptop is 12 inches from the router; it has the BCM4352 a/c card which is a dual channel dual stream and routinely connects via Windows 7 at 300mpbs on N and 865mbps on AC. On linux however, its derisory. A meagre 144mbps on N and 375 on AC. Again, 12 inches from the router.

I have tried the options you suggested and it made little difference to the link speeds. I'm getting 144mbps and I'm 12 inches away from the router.

Two networks on the router, a "N" and and "AC" network. one called "TILLY" one called "BELLA". TILLY is 5GHZ, BELLA is 20/40 (but tried the tweaks you suggested).


root@daz-VPCF11S1E:/home/daz# dmesg | grep -e wlan -e wl -e 80211
[   21.944960] cfg80211: Calling CRDA to update world regulatory domain
[   21.993920] lib80211: common routines for IEEE802.11 drivers
[   21.993924] lib80211_crypt: registered algorithm 'NULL'
[   22.530710] wl: module license 'MIXED/Proprietary' taints kernel.
[   22.532516] wl: module verification failed: signature and/or required key missing - tainting kernel
[   22.563695] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   22.603849] lib80211_crypt: registered algorithm 'TKIP'
[   22.674010] cfg80211: World regulatory domain updated:
[   22.674014] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.674016] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.674017] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.674019] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.674020] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.674022] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.480002] cfg80211: Calling CRDA to update world regulatory domain
[ 1674.486672] cfg80211: World regulatory domain updated:
[ 1674.486679] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1674.486684] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.486689] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.486693] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1674.486697] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1674.486701] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1676.900908] cfg80211: Calling CRDA to update world regulatory domain
[ 1676.905196] cfg80211: World regulatory domain updated:
[ 1676.905203] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1676.905208] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1676.905212] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1676.905216] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1676.905220] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1676.905224] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7546.167928] cfg80211: Calling CRDA to update world regulatory domain
[ 7546.173716] cfg80211: World regulatory domain updated:
[ 7546.173723] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7546.173728] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7546.173733] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7546.173737] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7546.173741] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7546.173744] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7919.295815] cfg80211: Calling CRDA to update world regulatory domain
[ 7919.303566] cfg80211: World regulatory domain updated:
[ 7919.303573] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7919.303578] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7919.303582] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7919.303586] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7919.303590] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7919.303594] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7926.190710] cfg80211: Calling CRDA to update world regulatory domain
[ 7926.195664] cfg80211: World regulatory domain updated:
[ 7926.195671] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7926.195676] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7926.195680] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7926.195684] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7926.195688] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7926.195692] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8138.393398] cfg80211: Calling CRDA to update world regulatory domain
[ 8138.398572] cfg80211: World regulatory domain updated:
[ 8138.398579] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8138.398584] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8138.398588] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8138.398592] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8138.398596] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8138.398600] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8176.097646] cfg80211: Calling CRDA to update world regulatory domain
[ 8176.100976] cfg80211: World regulatory domain updated:
[ 8176.100981] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8176.100984] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8176.100987] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8176.100990] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8176.100993] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8176.100996] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8176.281409] INFO @wl_cfg80211_scan : system busy : scan for "TILLY" canceled
[ 8176.314959] WARNING: CPU: 0 PID: 10337 at /build/buildd/linux-3.11.0/net/wireless/sme.c:658 __cfg80211_connect_result+0x408/0x410 [cfg80211]()
[ 8176.314963] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth binfmt_misc nvidia(POF) joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev lib80211_crypt_tkip wl(POF) snd_hda_codec_hdmi coretemp kvm_intel kvm lib80211 cfg80211 drm i7core_edac edac_core snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_page_alloc dm_multipath snd_seq_midi_event scsi_dh sony_laptop snd_rawmidi microcode snd_seq psmouse serio_raw snd_seq_device snd_timer snd lpc_ich soundcore mac_hid lp parport btrfs zlib_deflate raid6_pq libcrc32c dm_raid45 xor dm_mirror dm_region_hash dm_log vesafb firewire_ohci ahci sdhci_pci firewire_core libahci sky2 sdhci crc_itu_t video
[ 8176.315070] Workqueue: cfg80211 cfg80211_event_work [cfg80211]
[ 8176.315147]  [<ffffffffa03e1a98>] __cfg80211_connect_result+0x408/0x410 [cfg80211]
[ 8176.315167]  [<ffffffffa03c1544>] cfg80211_process_wdev_events+0x194/0x1c0 [cfg80211]
[ 8176.315187]  [<ffffffffa03c15b0>] cfg80211_process_rdev_events+0x40/0x90 [cfg80211]
[ 8176.315204]  [<ffffffffa03bd01e>] cfg80211_event_work+0x1e/0x30 [cfg80211]
[ 8245.975948] cfg80211: Calling CRDA to update world regulatory domain
[ 8245.981774] cfg80211: World regulatory domain updated:
[ 8245.981781] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8245.981786] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8245.981791] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8245.981794] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8245.981798] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8245.981802] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8381.387192] cfg80211: Calling CRDA to update world regulatory domain
[ 8381.392328] cfg80211: World regulatory domain updated:
[ 8381.392335] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8381.392340] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8381.392345] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8381.392349] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8381.392353] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8381.392357] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8386.698380] cfg80211: Calling CRDA to update world regulatory domain
[ 8386.703662] cfg80211: World regulatory domain updated:
[ 8386.703669] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8386.703674] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8386.703679] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8386.703683] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8386.703686] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8386.703690] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8470.584208] cfg80211: Calling CRDA to update world regulatory domain
[ 8470.589428] cfg80211: World regulatory domain updated:
[ 8470.589435] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8470.589440] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8470.589445] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8470.589449] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8470.589453] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8470.589457] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8475.801543] cfg80211: Calling CRDA to update world regulatory domain
[ 8475.805462] cfg80211: World regulatory domain updated:
[ 8475.805469] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8475.805474] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8475.805479] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8475.805483] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8475.805487] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8475.805491] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
root@daz-VPCF11S1E:/home/daz# 


root@daz-VPCF11S1E:/home/daz# cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
Apr 29 18:26:04 daz-VPCF11S1E NetworkManager[949]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 29 18:26:04 daz-VPCF11S1E NetworkManager[949]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Apr 29 18:26:05 daz-VPCF11S1E NetworkManager[949]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 29 18:26:05 daz-VPCF11S1E NetworkManager[949]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Apr 29 18:26:05 daz-VPCF11S1E NetworkManager[949]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 29 18:26:05 daz-VPCF11S1E NetworkManager[949]: <info> Policy set 'TILLY' (eth1) as default for IPv4 routing and DNS.
Apr 29 18:26:05 daz-VPCF11S1E NetworkManager[949]: <info> DNS: starting dnsmasq...
Apr 29 18:26:05 daz-VPCF11S1E NetworkManager[949]: <warn> dnsmasq not available on the bus, can't update servers.
Apr 29 18:26:05 daz-VPCF11S1E NetworkManager[949]: <error> [1398792365.645142] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr 29 18:26:05 daz-VPCF11S1E NetworkManager[949]: <warn> DNS: plugin dnsmasq update failed
Apr 29 18:26:05 daz-VPCF11S1E NetworkManager[949]: <info> Writing DNS information to /sbin/resolvconf
Apr 29 18:26:06 daz-VPCF11S1E NetworkManager[949]: <info> Activation (eth1) successful, device activated.
Apr 29 18:26:06 daz-VPCF11S1E NetworkManager[949]: <warn> dnsmasq appeared on DBus: :1.48
Apr 29 18:26:06 daz-VPCF11S1E NetworkManager[949]: <info> Writing DNS information to /sbin/resolvconf
Apr 29 18:26:24 daz-VPCF11S1E NetworkManager[949]: <info> (eth1): IP6 addrconf timed out or failed.
Apr 29 18:26:24 daz-VPCF11S1E NetworkManager[949]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 29 18:26:24 daz-VPCF11S1E NetworkManager[949]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 29 18:26:24 daz-VPCF11S1E NetworkManager[949]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 29 18:26:39 daz-VPCF11S1E NetworkManager[949]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.35': no such name
Apr 29 18:26:39 daz-VPCF11S1E NetworkManager[949]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.35': no such name
root@daz-VPCF11S1E:/home/daz# 


I tried UK in reg domain which was not accepted, so then I changed to EU , which didnt make much difference

root@daz-VPCF11S1E:/home/daz# iw reg get
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
root@daz-VPCF11S1E:/home/daz# iw reg set UK
root@daz-VPCF11S1E:/home/daz# iw reg get
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
root@daz-VPCF11S1E:/home/daz# iw reg set UK
root@daz-VPCF11S1E:/home/daz# iw reg set EU
root@daz-VPCF11S1E:/home/daz# iw reg get
country EU:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS

I'm fairly confident Chilli, that I saw a 300mbps link on Mint , using same laptop, same router, same locations - different kernel/modules though? It was Mint 16. But I'd like to crack this if we can?

I'd like to resolve the 2.4GHZ and N network first, then move to the 5GHZ AC network if I can ?

From the /var/log output, there is something in there about TKIP - should this not be AES ? The router is set to WPA2-Personal/AES

Once again, I'm stargazy as the sheer command of linux you have!

---

### Post by chili555 on 2014-04-29
You mean this?>  lib80211_crypt: registered algorithm 'TKIP'It does seem suspicious. If the router is set to WPA2-AES, then I frankly don't understand this unless the driver starts at the lowest common denominator and ramps up after the driver and hardware negotiate with the router. I would expect to see this, but we do not:> lib80211_crypt: registered algorithm 'CCMP'I feel a little embarrassed to ask, but just in the interest of completeness, please check again that each and every place that allows a selection in the router is selected AES. > I tried UK in reg domain which was not accepted,UK is not an available selection on the list. Did you try GB?

There are clear differences in my case between 00 and US:> chili@T410:~$ sudo iw reg set 00
chili@T410:~$ sudo iw reg get
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
chili@T410:~$ sudo iw reg set US
chili@T410:~$ sudo iw reg get
country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)
Whether those differences translate to better connectivity seems to be hit and miss. Some swear it cures all ills; some swear it doesn't help anything! Since it seems to help in some cases, I keep it on my list of techniques to try. 

Except for here, where the driver had a big stumble, I see nothing remarkable and therefor fixable:> [ 8176.314959] WARNING: CPU: 0 PID: 10337 at /build/buildd/linux-3.11.0/net/wireless/sme.c:658 __cfg80211_connect_result+0x408/0x410 [cfg80211]()
[ 8176.314963] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth binfmt_misc nvidia(POF) joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev lib80211_crypt_tkip wl(POF) snd_hda_codec_hdmi coretemp kvm_intel kvm lib80211 cfg80211 drm i7core_edac edac_core snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_page_alloc dm_multipath snd_seq_midi_event scsi_dh sony_laptop snd_rawmidi microcode snd_seq psmouse serio_raw snd_seq_device snd_timer snd lpc_ich soundcore mac_hid lp parport btrfs zlib_deflate raid6_pq libcrc32c dm_raid45 xor dm_mirror dm_region_hash dm_log vesafb firewire_ohci ahci sdhci_pci firewire_core libahci sky2 sdhci crc_itu_t video
[ 8176.315070] Workqueue: cfg80211 cfg80211_event_work [cfg80211]
[ 8176.315147] [<ffffffffa03e1a98>] __cfg80211_connect_result+0x408/0x410 [cfg80211]
[ 8176.315167] [<ffffffffa03c1544>] cfg80211_process_wdev_events+0x194/0x1c0 [cfg80211]
[ 8176.315187] [<ffffffffa03c15b0>] cfg80211_process_rdev_events+0x40/0x90 [cfg80211]
[ 8176.315204] [<ffffffffa03bd01e>] cfg80211_event_work+0x1e/0x30 [cfg80211]I really have but one more suggestion. You are running a 3.11 kernel which, I believe, corresponds to Ubuntu 13.10. You might try a live DVD for Ubuntu 14.04, which runs kernel version 3.13, to see if the behavior is improved.> I'm stargazy as the sheer command of linux you have!After a decade or so, I've heard everything, more or less, and I'm happiest when a new device and new technology come along to learn about and therefore be helpful to the next person with a question. I fear my skill is very narrow in a highly specialized area. You don't see me answering questions about video cards or sound or VPN or printers!

---

### Post by keratos2 on 2014-04-29
Ah, so you are  a specialist. 

Yes, the TKIP presence seems strange. I might obtain the cfg80211 code and see if I can determine how to force AES/CCMP

There are only two places in the router where crypt is set and they're both AES.

reg settings had the following effect@
root@daz-VPCF11S1E:/home/daz# iw reg get
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
root@daz-VPCF11S1E:/home/daz# iw reg set GB
root@daz-VPCF11S1E:/home/daz# iw reg get
country GB:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR
root@daz-VPCF11S1E:/home/daz# 

not sure if the changes do anything' its not perceivable to me if it is/does?

---

### Post by keratos2 on 2014-04-30
Hey Chilli,
Well this is embarassing
Turns out the router is not providing x2 streams on the 2.4GHz band. 5GHz is okay. Max connect link speed is around 144Mbps across three laptops with different wifi h/w and O/Ss. Tried another 1200ac router and I was able to get link speeds of 300Mbps on 2.4GHz. So its the router that is the problem, or to be specific the wireless h/w element.
Returning the router.

---

### Post by chili555 on 2014-04-30
No embarrassment needed here. You didn't wire the router nor QC the final product.

Please update us because I am sure there are searchers that will be interested in the eventual AC performance of the device and the Broadcom driver. Me, too!

---

### Post by Elfy on 2014-04-30
*Thread moved to **Other OS/Distro Support**.*

---

### Post by keratos2 on 2014-04-30
Will do. New router should be here by Friday and I will post an update

---

### Post by keratos2 on 2014-05-06
Update for ya...

New router installed - same result.

So I went back to basics and downloaded the source tar ball for the USB AC56U 802.11ac adapter (uses BCM4352 branded rtl8812 chipset). The source code includes wide chipset support but here I was simply interested in the 8812AU.ko module - selfish I know !

I first compiled against a 3.11 kernel , to no avail. Lots of warnings about pointers undeclared and sure enough the include files were not defining the expected structures.

So I moved back to a 3.8 kernel widely supported amongst distro's at their previous version. 

Voila! This worked a treat. 
 
I installed the driver and the system fired up with a detailed log in dmesg (which I need to examine in slow time). Link speed was reported at 876Mbps , but this didnt change despit le where I went in the home. However, what surprised me was the sheer performance. I'm getting around 400Mbps of realisic throughput which isnt bad for astated 876 max link speed.

On windows 7 the same USB stick topped out at around 85Mbps, with windows reporting a link speed of 175Mbps.

This linux driver IS AMAZING and quite why windowze cannot extract the same performance is bizzare but unsurprising given Microsoft's marketing strategies.

So all in all, a job well done and a perfect driver and hardware combo working flawlessly on the 5GHz band 40MHz frequency averaging 400Mbps up/down throughput. 

If some admin/mod  wants the instructions for a sticky I'd be happy to provide otherwise its a lot of work to be cast off down the thread annals to disappear forever.

---

### Post by chili555 on 2014-05-06
> uses BCM4352 branded rtl8812 chipsetWhat?? A Broadcom branded Realtek chip? >  USB AC56U 802.11acIsn't this the router?

I'm corn-fused.

---

### Post by keratos2 on 2014-05-06
sorry mate, 

okay , to clarify,

ASUS have decided to badge their 1200AC router as "RT-AC56U" and their 1200AC USB adapter "USB-AC56U" . simplez! 

And yep, a rtl chipse, in a broadcom device, integrated by the OEM (Asus) into their USB stick. You couldnt write it !! And ASUS release the OSS for this so must have known people would catch on, but alas their probably safe as most dumbdown users opt for the unsecure, bloated, archaic windowze platform and probably never realise nor care.

---

### Post by chili555 on 2014-05-06
> 1200AC USB adapter "USB-AC56UI see.You are no longer using the internal PCI:> Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)Which 8812au driver did you compile? I can compile this, albeit with a few warnings but no errors, in 14.04: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)

---

### Post by keratos2 on 2014-05-06
Same reported chipset in both mini PCI-e and USB.

 I used a USB adapter to test the setup out in the process of doing so found an excellent combo that works fine with outstanding performance. Router is on the ground floor in one corner, I'm on the second floor (or third including ground) in another corner, getting 85% signal with -44dbm attn.

I complied the one from ASUS website. works a treat on a 3.8 kernel, got it working in Zorin, Netrunner, WattOS, but not in 14.04 ubuntu or any 3.11 kernel. I didnt try the github version but from what you say that seems to work. But I aint changing this power combo any time soon.

---

### Post by gus_pappas on 2014-07-11
> **keratos2 said:**
> I'm moving from Windows7 to linux and have installed Zorin v8.1 as this is supposed to be most friendly linux for windows users. I love it. Speed is excellent. However, the wifi doesnt work. After much googling I managed to use some "apt-get install" command to install some bcm kernel sources and drivers. It was just one package - [FONT=Ubuntu Mono]bcmwl-kernel-source
[/FONT]
This installed a "wl" driver and I have a connection, however, it is crap and no where near as reliable or good as the connection in windows 7. I know its not the hardware because it works fine under windows7. I sit in my chair next to the router and get one bar. I used to get 5 bars. This translates to -55db and -32db respectively. 

How to install the LATEST broadcom propietary driver ? I have no idea what version of ubuntu I'm on - sorry - but I'm supposed to be on some ubuntu base (saucy appears in the /etc/apt files)

I'm loosing the will to live so can someone please help - if you could avoid posting just that I "suggest" or "try" or 'google" or  something like this, I'd be obliged - what I need is someone who is an expert in this field and has the answer. Thank you for your kind understanding.
You may be picking up someone's signal. Sometimes wifi automatically switches to a weak ,nearby ,neighboring signal ,without noticing.

---

### Post by keratos2 on 2014-07-11
> **gus_pappas said:**
> You may be picking up someone's signal. Sometimes wifi automatically switches to a weak ,nearby ,neighboring signal ,without noticing.

What utter rubbish.

You clearly need to learn about WiFi and encryption

---

### Post by lisati on 2014-07-12
Let's keep this thread on topic: there are more ways of protecting a network than just the usual password protection available through WEP and WPA.

---

### Post by keratos2 on 2014-07-12
Yes agreed. MAC filter, SSID filter, .... Etc
But the point I was making is not so much the methods, more that one simply cannot 'pickup' (infer connect) to a network 'automatically' ... Unless it's completely unsecured and open
But you knew that.
The post was rather uninsightful

---

### Post by lisati on 2014-07-12
This topic has drifted, and the OP hasn't been back for a couple of months.

Thread closed.

---

