---
title: "Ubuntu Server Randomly Disconnecting/Crashing"
date: 2011-06-25
forum: Server Platforms
---

### Post by jzollo on 2011-06-25
I'm having a rather frustrating issue with my Ubuntu Server.

I just built a new AMD Phenom II X4 based machine

Very randomly, I will lose my connection to the server. All running services stop responding, samba shares become inaccessible, apache doesn't serve webpages, ftp will not connect, etc. I'm not very good at diagnosing issues with Linux just yet so I am asming you guys for assistance.

I'm not sure if this has anything to do with it, but on every login screen (when I login physically at the computer) I see this message, "SP5100 TCO timer: mmio address 0xb8fe00 already in use", again not sure if this is related.

From kern.log ...

Jun 25 16:37:42 Epsilon kernel: [    7.280531] SP5100 TCO timer: mmio address 0xb8fe00 already in use

I ran a Memtest and everything checked out, i'm just unsure how to proceed at this point and would appreciate any advice you guys could offer.

---

### Post by tgalati4 on 2011-06-26
At the console:

dmesg | tail -f

This will dump system messages in real time.  Now log into your server from remote machines and stress it a little.  When it locks up, look at the console and post what gets dumped.

If nothing gets posted, then your ethernet card may be failing.  Try installing another card and see if improves.

---

### Post by OvermindDL1 on 2011-06-27
I have the exact same issue, but with a Phenom II x6 and more information.

I also get this message on startup, unsure if related, takes a *long* time to boot up since Natty, used to take like one minute overall, now takes 5 to 10 since the Natty upgrade, with all the extra time spent is just displaying this message:  SP5100 TCO timer: mmio address 0xb8fe00 already in use

Then anywhere from an hour to weeks later, seemingly irrespective of load or programs run it just seems to start locking up in an odd way.  First programs start freezing, apache freezes, the gui freezes if one is running, keyboard/ mouse become unresponsive, not even the caps/scroll/num lock will toggle, and the screen usually, but not always, turns into pure garbage, colored lines all over it, *but* if I ssh in quickly (which I usually still can even with the keyboard being unresponsive) I can get in and issue a 'shutdown -r now' and it reboots.  If I wait too long then the whole thing locks up so much that even the lights on the case stop blinking and all activity ceases.

I first figured that it might be the ram so I replaced it with a known working and memtest86'd (overnight) 16gig set and that did not help or hurt anything.

I am not on location right now but will be later today; any thoughts?

EDIT:  Oh, and yes, I have tried a new network card as well.

---

### Post by jzollo on 2011-06-27
Overmind, do you by any chance do you have an Asus M4A88TD-V EVO/USB3 motherboard?

tgalati4, here is the information you requested, 

```
Jun 26 15:02:57 Delta kernel: [    9.313812] [drm] Connector 1:
Jun 26 15:02:57 Delta kernel: [    9.313813] [drm]   DVI-D
Jun 26 15:02:57 Delta kernel: [    9.313814] [drm]   HPD1
Jun 26 15:02:57 Delta kernel: [    9.313815] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
Jun 26 15:02:57 Delta kernel: [    9.313816] [drm]   Encoders:
Jun 26 15:02:57 Delta kernel: [    9.313817] [drm]     DFP3: INTERNAL_KLDSCP_LVTMA
Jun 26 15:02:57 Delta kernel: [    9.320077] type=1400 audit(1309114977.011:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=545 comm="apparmor_parser"
Jun 26 15:02:57 Delta kernel: [    9.320088] type=1400 audit(1309114977.011:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=501 comm="apparmor_parser"
Jun 26 15:02:57 Delta kernel: [    9.320309] type=1400 audit(1309114977.011:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=545 comm="apparmor_parser"
Jun 26 15:02:57 Delta kernel: [    9.320323] type=1400 audit(1309114977.011:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=501 comm="apparmor_parser"
Jun 26 15:02:57 Delta kernel: [    9.320458] type=1400 audit(1309114977.011:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=545 comm="apparmor_parser"
Jun 26 15:02:57 Delta kernel: [    9.320477] type=1400 audit(1309114977.011:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=501 comm="apparmor_parser"
Jun 26 15:02:57 Delta kernel: [    9.365847] hda_codec: ALC892: BIOS auto-probing.
Jun 26 15:02:57 Delta kernel: [    9.373872] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Jun 26 15:02:57 Delta kernel: [    9.378378] EDAC amd64: DRAM ECC disabled.
Jun 26 15:02:57 Delta kernel: [    9.378401] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jun 26 15:02:57 Delta kernel: [    9.378402]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jun 26 15:02:57 Delta kernel: [    9.378403]  (Note that use of the override may cause unknown side effects.)
Jun 26 15:02:57 Delta kernel: [    9.379865] [drm] radeon: power management initialized
Jun 26 15:02:57 Delta kernel: [    9.438837] [drm] fb mappable at 0xF0141000
Jun 26 15:02:57 Delta kernel: [    9.438838] [drm] vram apper at 0xF0000000
Jun 26 15:02:57 Delta kernel: [    9.438839] [drm] size 5242880
Jun 26 15:02:57 Delta kernel: [    9.438840] [drm] fb depth is 24
Jun 26 15:02:57 Delta kernel: [    9.438840] [drm]    pitch is 5120
Jun 26 15:02:57 Delta kernel: [    9.450222] Console: switching to colour frame buffer device 160x64
Jun 26 15:02:57 Delta kernel: [    9.453313] fb0: radeondrmfb frame buffer device
Jun 26 15:02:57 Delta kernel: [    9.453314] drm: registered panic notifier
Jun 26 15:02:57 Delta kernel: [    9.453319] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
Jun 26 15:02:57 Delta kernel: [    9.453562] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 26 15:02:57 Delta kernel: [    9.453591] HDA Intel 0000:01:05.1: setting latency timer to 64
Jun 26 15:02:57 Delta kernel: [    9.751083] r8169 0000:04:00.0: eth0: link down
Jun 26 15:02:57 Delta kernel: [    9.751092] r8169 0000:04:00.0: eth0: link down
Jun 26 15:02:57 Delta kernel: [    9.751421] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 26 15:02:57 Delta kernel: [    9.823560] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Jun 26 15:02:57 Delta kernel: [   10.095049] type=1400 audit(1309114977.781:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=741 comm="apparmor_parser"
Jun 26 15:02:57 Delta kernel: [   10.095067] type=1400 audit(1309114977.781:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=742 comm="apparmor_parser"
Jun 26 15:02:57 Delta kernel: [   10.095187] type=1400 audit(1309114977.781:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=740 comm="apparmor_parser"
Jun 26 15:02:57 Delta kernel: [   10.095427] type=1400 audit(1309114977.781:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=740 comm="apparmor_parser"
Jun 26 15:03:01 Delta kernel: [   13.476348] r8169 0000:04:00.0: eth0: link up
Jun 26 15:03:01 Delta kernel: [   13.476671] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 26 15:03:11 Delta kernel: [   23.910035] eth0: no IPv6 routers present
Jun 26 16:09:53 Delta kernel: [ 4025.543764] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 26 16:18:58 Delta kernel: [ 4571.119109] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jun 26 17:11:53 Delta kernel: [ 7745.658124] usb 5-1: USB disconnect, address 2
Jun 26 17:11:53 Delta kernel: [ 7745.658133] usb 5-1.2: USB disconnect, address 3
Jun 26 17:11:53 Delta kernel: [ 7746.060245] usb 5-1.3: USB disconnect, address 4
Jun 26 17:21:13 Delta kernel: Kernel logging (proc) stopped.
Jun 26 17:21:13 Delta kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun 26 17:21:22 Delta kernel: [ 8314.357673] audit_printk_skb: 6 callbacks suppressed
Jun 26 17:21:22 Delta kernel: [ 8314.357681] type=1400 audit(1309123282.046:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=13054 comm="apparmor_parser"
Jun 26 17:21:22 Delta kernel: [ 8314.881144] r8169 0000:04:00.0: eth0: link down
Jun 26 17:21:22 Delta kernel: [ 8314.881158] r8169 0000:04:00.0: eth0: link down
Jun 26 17:21:22 Delta kernel: [ 8314.882264] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 26 17:21:26 Delta kernel: [ 8318.667577] r8169 0000:04:00.0: eth0: link up
Jun 26 17:21:26 Delta kernel: [ 8318.668661] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 26 17:21:30 Delta kernel: Kernel logging (proc) stopped.
Jun 26 17:21:30 Delta kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun 26 17:21:36 Delta kernel: [ 8328.790069] eth0: no IPv6 routers present

```
Looks like eth0 is going down randomly. I'll put in a PCI gigabit card tonight and we'll see if that does anything. Is there any way this could be a driver issue? I'd hate to have to RMA this sucker.

I noticed that Asus has a LAN driver on their website, might be worth a shot to install.

---

### Post by OvermindDL1 on 2011-06-27
As a matter of fact, I do not, it is a Gigabyte.  It has a 1gbit network adapter, but that is not being used, I hooked up a 100mbit USB one for testing and the problem still occurs, still using that one.  My dmesg is attached as a zip (txt inside).

---

### Post by jzollo on 2011-06-28
I was able to resolve my issues by following this little guide here, turns out the driver Ubuntu loads by default for the Realtek RTL8111/8168 is bad.

[http://wookie.co.nz/wordpress/rebuild-realtek-r8168-module-for-ubuntu/](http://wookie.co.nz/wordpress/rebuild-realtek-r8168-module-for-ubuntu/)

A few things to note though, you will need to run the following commands while you still have your connection up...

sudo apt-get install make
sudo apt-get install gcc

---

### Post by OvermindDL1 on 2011-06-28
I have the Realtek 8111D, awesome research.  I shall give that link a try when I ssh in later today.

EDIT:  So based on reading the linked thread in the above link, this driver bug is a few years old, how is it not fixed yet?!?

---

