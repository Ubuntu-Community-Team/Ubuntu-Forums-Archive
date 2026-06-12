---
title: "Fatal exception in interrupt"
date: 2008-09-06
forum: Server Platforms
---

### Post by vladk2k on 2008-09-06
Hi
I have a server bodged up from different parts, which has been acting up on me, delivering kernel panics.

The system specs are:
ECS KM400-M2 motherboard (VIA KM400 Northbridge)
AMD Semprin 2300+ (1.6 GHz)
Onboard Video (S3 Unichrome)
512 MB of DDR RAM
80GB Maxtor IDE HDD
Realtek RLT8139 NIC
Onboard Audio

I've had this problem since forever, but I always put the blame on the previous OS (Ubuntu Server 7.10 upgraded from 7.04, with ubuntu-desktop installed, deluge etc.) - thinking I somehow fudged up the config files.
What I did was fresh install of Ubuntu Server 8.04.1, configured Cups, Samba, Dhcp3-server, upgraded everything etc.
Nevertheless, I left the monitor plugged in, and in the morning - **bam**! Kernel panic

You have the screenshot below - I couldn't find anything in *kern.log*, *messages* or *dmesg.0* (I don't know where else to look)
[[IMG]http://img526.imageshack.us/img526/6656/p9060003gr6.th.jpg[/IMG]](http://img526.imageshack.us/my.php?image=p9060003gr6.jpg)

I want to say that this happened at about 5:04 AM (it's the last 'mark' in the kern.log file). Nobody was using the server at that time (none of its services, I mean), the only thing that was running is *rtorrent* in a *screen* session.
Processor heat is not a problem, I think (never exceeds 52 degrees Celsius). I could do a BIOS update (I have 1.0c, the latest is 1.0d) or deactivate some of its features (parallel port, onboard audio and LAN) but those were not in use when the kernel panic hit.

I don't know what else to do. Please help!

---

### Post by windependence on 2008-09-06
I'm gonna catch some crap for this but ECS stuff has never been know for "quality". I would pull all your peripheral cards except what you absolutely need (video). Pull all memory except for one stick. The start your server and run it for a while. If there is no kernel panic after the same amount of time as before, add each component back ONE AT A TIME, and run it for the same time period with each component installed. This is the only way to isolate hardware problems. If it kernel panics without any cards installed it's either memory or your mobo. At that point, pull the memory you have installed and install a different DIMM and try it.

Alternatively, you may want to try a different distro altogether or even a different OS like FreeBSD, just to make sure it isn't that your OS doesn't like your hardware.

Remember - when troubleshooting do ONLY one thing at a time, and test. That way, you can locate the problem with ease.

-Tim

---

### Post by vladk2k on 2008-09-06
I've tinkered around with the setup a bit. Some guy told me it looks like a network card problem (kernel-nic interface or something) but i haven't replaced that yet

I've disabled in BIOS sound, parallel port, IRQ monitoring for wakeups and everything that I'm not actively using (or going to use for a long time). I've kept the onboard NIC active, since I might use it in the future. I've also updated the BIOS with the latest (and probably last) available on the ECS website (1.0d)

Thing is, these kernel panics don't seem to appear after a set period of time. Sometimes they appear after 20-30 minutes, sometimes after two weeks or a month.

Will keep you posted if anything new appears.

---

