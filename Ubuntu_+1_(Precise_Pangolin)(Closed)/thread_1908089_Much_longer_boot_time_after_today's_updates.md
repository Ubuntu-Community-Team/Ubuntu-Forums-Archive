---
title: "Much longer boot time after today's updates?"
date: 2012-01-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2012-01-12
Is anyone else seeing this?

I've found consistently (much) longer boot times with PP (64 bit) after today's updates. Finally booted up my OO install (32 bit) on the same box and found boot time to be normal so it seems to me it's something to do with today's PP updates.

Posting this from OO and haven't checked the PP logs yet, but I remember seeing some **nsswitch**-related updates and I wonder if that has something to do with it. Or maybe it's just me.

EDIT: Nothing to do with the 3.2.1 kernel btw.

EDIT2: Should probably have mentioned that this is with the xorg-edgers and ricotz-testing ppas.

---

### Post by kaldor on 2012-01-12
Working as normal here.

---

### Post by paul_in_london on 2012-01-13
> **kaldor said:**
> Working as normal here.

Thanks for the feedback. Are you using any PPAs?

Maybe it's a peculiarity of my setup or just a temporary glitch.

Just updated a 12.04 virtual machine (32 bit) and the boot time seemed to be normal after the updates or not significantly longer than yesterday anyway.

Will look at it again later when I have more time.

---

### Post by dino99 on 2012-01-13
have some issue too since kernel 8-15 is used (the changelog relates lot of tweaks) and i beleive i've found the good bios settings (but not sure yet, that asus mobo give me often headaches :()

---

### Post by effenberg0x0 on 2012-01-13
I'm not seeing such effect after updates. I have no PPAs added. I would check if, for any reason, modem-manager is back. It's the one thing that caused boot delays for me this cycle.

Maybe Bootchart can give us some clue?

---

### Post by dino99 on 2012-01-13
have had hard time at usb detection, i've tried every usb settings in the bios but that bios is so ugly :(

---

### Post by clivejo on 2012-01-13
Me too, on investigation it was waiting on Network Configuration.  It took almost 2 minutes extra to boot.

---

### Post by paul_in_london on 2012-01-13
> **clivejo said:**
> Me too, on investigation it was waiting on Network Configuration.  It took almost 2 minutes extra to boot.

Can't test it right now myself, but what happens if you boot an earlier kernel (say 3.2.0-7)? I don't think I actually tried one < 3.2.0-8.15. I do know it was the same for me with 3.2.1 from ppa mainline.

---

### Post by effenberg0x0 on 2012-01-13
@Dino I am using a ASUS Motherboard. What BIOS/USB settings are you having problems with? As far as I can remember right now, I have disable FullSpeed-12Mbps (using HiSpeed 480Mbps), enabled EHCI Hand-Off, set legacy on "Auto" to 10x USB 2.0/1.1 and Enabled USB 3.0 OnBoard Controller for 2x USB 3.0/2.0. Other related settings are PnP'OS (yes), ACPI2.0 (Yes), APIC (Yes), APM (Yes). That's all I have that somehow messes with USB (I think).

---

### Post by clivejo on 2012-01-13
> **paul_in_london said:**
> Can't test it right now myself, but what happens if you boot an earlier kernel (say 3.2.0-7)? I don't think I actually tried one < 3.2.0-8.15. I do know it was the same for me with 3.2.1 from ppa mainline.

I haven't tried as I dont want to reboot incase it breaks!  Busy doing other stuff right now.  I just remember it taking ages to boot so I removed the quiet option and watched the text boot output.  It said Waiting for Network Configuration, then about a minute later said Waiting another 60 seconds ....  After about two minutes it continued on its merry way and desktop seems stable enough.  One thing that did strike me as odd, in the wireless networks I have numerous network connections named Hotspot 1, Hotspot 2, and so on.  Up to about 19, Ive never seen this before!

---

### Post by clivejo on 2012-01-14
Just booted into Linux 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64.  Same delay at Network Configuration.  

When I got into my desktop, it would not connect to my wireless network.

---

### Post by kaldor on 2012-01-14
> **paul_in_london said:**
> Thanks for the feedback. Are you using any PPAs?

Maybe it's a peculiarity of my setup or just a temporary glitch.

Just updated a 12.04 virtual machine (32 bit) and the boot time seemed to be normal after the updates or not significantly longer than yesterday anyway.

Will look at it again later when I have more time.

I was using the unity staging PPA at the time. However, I am using a very vanilla 12.04 setup.

Today the boot time was very much okay, but the desktop took 30 seconds to load. I was staring at the wallpaper until eventually everything decided to pop up. Might have something to do with it, but I am unsure.

---

### Post by cariboo on 2012-01-14
My system seems to be booting OK:

[[IMG]http://i.imgur.com/yjJl1l.png[/IMG]](http://imgur.com/yjJl1)

---

### Post by clivejo on 2012-01-15
How would I find out what its waiting on?

---

### Post by paul_in_london on 2012-01-15
> **clivejo said:**
> How would I find out what its waiting on?

Hold down the shift key when the BIOS loads to get the GRUB menu, edit your GRUB menu entry before you boot and remove "quiet" and "splash" from the kernel line.

In my case it spends a LONG time waiting for network configuration.

I tried booting 3.2.0-7 last night and experienced the same problem.

---

### Post by clivejo on 2012-01-15
Ah never mind found it.

If I comment out the line "auto lo" in  **/etc/network/interfaces **seems to solve the problem.

Anyone else verify this?

---

### Post by clivejo on 2012-01-15
> **paul_in_london said:**
> Hold down the shift key when the BIOS loads to get the GRUB menu, edit your GRUB menu entry before you boot and remove "quiet" and "splash" from the kernel line.

In my case it spends a LONG time waiting for network configuration.

I tried booting 3.2.0-7 last night and experienced the same problem.

Sorry didn't explain myself, I was looking for more detailed logs to try and find the problem.  Waiting for Network Configuration doesn't give me much to work on! 

Can you try commenting out the line and see if that solves it on your box?

---

### Post by paul_in_london on 2012-01-15
> **clivejo said:**
> Sorry didn't explain myself, I was looking for more detailed logs to try and find the problem.  Waiting for Network Configuration doesn't give me much to work on! 

Can you try commenting out the line and see if that solves it on your box?

I can test the effect, but it's not a good idea to comment out that line because "local" network capability is needed by some programs.

---

### Post by clivejo on 2012-01-15
> **paul_in_london said:**
> I can test the effect, but it's not a good idea to comment out that line because "local" network capability is needed by some programs.

I understand that, just trying to narrow down the problem.  We obviously are talking about the same issue if that 'fixes' it for you too.

Have you only two line in your file ??  I have the following :
```
auto lo
iface lo inet loopback
```Correct me if I'm wrong but isn't the second line defining the loopback too?  Why do we need those two lines?

**ifconfig** reports 
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1092 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1092 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:144467 (144.4 KB)  TX bytes:144467 (144.4 KB)

```

---

### Post by paul_in_london on 2012-01-15
> **clivejo said:**
> I understand that, just trying to narrow down the problem.  We obviously are talking about the same issue if that 'fixes' it for you too.

Have you only two line in your file ??  I have the following :
```
auto lo
iface lo inet loopback
```Correct me if I'm wrong but isn't the second line defining the loopback too?  Why do we need those two lines?

**ifconfig** reports 
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1092 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1092 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:144467 (144.4 KB)  TX bytes:144467 (144.4 KB)

```

This is mine:

```
paul@precise-64:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
paul@precise-64:~$
```

Let me hunt around a bit.

---

### Post by ventrical on 2012-01-15
download bootchart from synaptic and you will get the screens Cariboo907 gets.

---

### Post by clivejo on 2012-01-15
> **ventrical said:**
> download bootchart from synaptic and you will get the screens Cariboo907 gets.

Thanks, will do

---

### Post by ventrical on 2012-01-15
and you will find them in:

/var/log/bootchart/

---

### Post by ventrical on 2012-01-15
it has dogged a little bit..

---

### Post by paul_in_london on 2012-01-15
Comment #40 on this page nailed it for some people, but didn't apply in my case:

```
https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/856810
```

Still looking...

---

### Post by clivejo on 2012-01-15
Ok I installed Bootchart

92s with the line commented out 

195s with out.

So that's like a 103 seconds delay to the boot process, just by having that one line!  Any idea what's causing it?

What is the process nmbd?

There is a huge difference in time from nmbd starts and the next process sh starts on the delayed boot.

---

### Post by zika on 2012-01-15
Did You try to boot with &#8222;lo&#8220; disabled? In great percentage of cases You'll end up either (if You're lucky) in recovery mode or (in most cases) chroot-ing...
Maybe You will get through boot with only &#8222;auto lo&#8220; disabled, but with both... 
Turn NM off:
```
echo "manual" | sudo tee -a /etc/init/network-manager.override
echo "manual" | sudo tee -a /etc/init/modem-manager.override
```
Make a proper /etc/network/interfaces
```
:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```
and /etc/resolv.conf```
:~$ cat /etc/resolv.conf
nameserver whatever_You've_set-up
```
Remove mn-applet from startup-applications and live ever after...
Once You get an(other) urge to tweak You could think of static address...

---

### Post by clivejo on 2012-01-15
It seems to be something to do with Samba and the loopback device, from what I can work out.

---

### Post by VMC on 2012-01-15
> **clivejo said:**
> It seems to be something to do with Samba and the loopback device, from what I can work out.

What kind of network do you have? NFS share. How about network card?

Mine booted in 18 seconds.

> ifconfig
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:9b:e8:4d  
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2cb:4eff:fe9b:e84d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16531 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20844834 (20.8 MB)  TX bytes:2174334 (2.1 MB)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146266 (146.2 KB)  TX bytes:146266 (146.2 KB)


---

### Post by clivejo on 2012-01-15
**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr *removed*
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29567 (29.5 KB)  TX bytes:29567 (29.5 KB)

wlan0     Link encap:Ethernet  HWaddr *removed* 
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b6ff:fe59:223a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:314455 (314.4 KB)  TX bytes:58630 (58.6 KB)

```
The only difference is the nmbd process waits for about a minute and a half on something.  When I remove the 'auto lo' line it works fine.  From reading about it the nmbd is linked to Samba.  Any idea how to disable this nmbd process from starting?

---

### Post by zika on 2012-01-15
The only problem with boot I have is &#8222;PMP SRST workaround&#8220; with SATA that makes my boot nearly a minute longer. But, that could be solved only with recompiling the kernel with CONFIG_SATA_PMP=n...

---

### Post by paul_in_london on 2012-01-15
> **zika said:**
> Did You try to boot with „lo“ disabled? In great percentage of cases You'll end up either (if You're lucky) in recovery mode or (in most cases) chroot-ing...
Maybe You will get through boot with only „auto lo“ disabled, but with both... 
Turn NM off:
```
echo "manual" | sudo tee -a /etc/init/network-manager.override
echo "manual" | sudo tee -a /etc/init/modem-manager.override
```
Make a proper /etc/network/interfaces
```
:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```
and /etc/resolv.conf```
:~$ cat /etc/resolv.conf
nameserver whatever_You've_set-up
```
Remove mn-applet from startup-applications and live ever after...
Once You get an(other) urge to tweak You could think of static address...

This wasn't it for me. I didn't have network-manager installed anyway and I removed modemmanager because I'm not using mobile broadband.

```
paul@precise-64:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:a4:f3:32:a3  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1985054 (1.9 MB)  TX bytes:411520 (411.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:411 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40088 (40.0 KB)  TX bytes:40088 (40.0 KB)

paul@precise-64:~$ 
```

```
paul@precise-64:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:3f:00.0
       logical name: eth0
       version: 01
       serial: 00:17:a4:f3:32:a3
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5752-v3.10 ip=192.168.1.66 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:e8400000-e840ffff
paul@precise-64:~$
```

---

### Post by paul_in_london on 2012-01-16
Ok for the last few days I've had these boot-related entries in /var/log/syslog:

```
paul@precise-64:~$ grep "dhclient: parse_option_param: Bad format a" /var/log/syslog
Jan 12 20:48:29 localhost dhclient: parse_option_param: Bad format a
Jan 13 00:31:44 localhost dhclient: parse_option_param: Bad format a
Jan 13 22:55:36 localhost dhclient: parse_option_param: Bad format a
Jan 14 12:19:38 localhost dhclient: parse_option_param: Bad format a
Jan 14 23:26:20 localhost dhclient: parse_option_param: Bad format a
Jan 15 05:12:46 localhost dhclient: parse_option_param: Bad format a
Jan 15 17:53:13 localhost dhclient: parse_option_param: Bad format a
Jan 15 21:52:41 localhost dhclient: parse_option_param: Bad format a
Jan 15 22:56:27 localhost dhclient: parse_option_param: Bad format a
Jan 15 23:06:22 localhost dhclient: parse_option_param: Bad format a
Jan 15 23:07:23 localhost dhclient: parse_option_param: Bad format a
Jan 15 23:56:07 localhost dhclient: parse_option_param: Bad format a
Jan 16 00:32:39 localhost dhclient: parse_option_param: Bad format a
Jan 16 18:49:29 localhost dhclient: parse_option_param: Bad format a
Jan 16 18:58:46 localhost dhclient: parse_option_param: Bad format a
paul@precise-64:~$
```

It's potentially a consequence of one of these updates (everything was fine before that). Details extracted from /var/log/aptitude:

```
Aptitude 0.6.4: log report
Thu, Jan 12 2012 20:17:59 +0000

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 67 packages, and remove 3 packages.
4,768 kB of disk space will be used
===============================================================================
[REMOVE, NOT USED] libebook1.2-12
[REMOVE, NOT USED] libecal1.2-10
[REMOVE, NOT USED] libedataserver1.2-15
[INSTALL, DEPENDENCIES] libebook-1.2-12
[INSTALL, DEPENDENCIES] libecal-1.2-10
[INSTALL, DEPENDENCIES] libedataserver-1.2-15
[UPGRADE] apparmor 2.7.0~beta1+bzr1774-1ubuntu3 -> 2.7.0-0ubuntu1
[UPGRADE] command-not-found 0.2.45ubuntu2 -> 0.2.45ubuntu3
[UPGRADE] command-not-found-data 0.2.45ubuntu2 -> 0.2.45ubuntu3
[UPGRADE] evince 3.2.1-1ubuntu6 -> 3.2.1-1ubuntu7
[UPGRADE] evince-common 3.2.1-1ubuntu6 -> 3.2.1-1ubuntu7
[UPGRADE] evolution-data-server 3.2.2-0ubuntu2 -> 3.2.3-0ubuntu1
[UPGRADE] evolution-data-server-common 3.2.2-0ubuntu2 -> 3.2.3-0ubuntu1
[UPGRADE] firefox-trunk 12.0~a1~hg20120111r84108-0ubuntu1~umd1 -> 12.0~a1~hg20120111r84273-0ubuntu1~umd1
[UPGRADE] firefox-trunk-globalmenu 12.0~a1~hg20120111r84108-0ubuntu1~umd1 -> 12.0~a1~hg20120111r84273-0ubuntu1~umd1
[UPGRADE] gir1.2-clutter-1.0 1.9.3+git20120103.88aaad9b-0ubuntu1~12.04~ricotz1 -> 1.9.3+git20120112.646cf236-0ubuntu1~12.04~ricotz0
[UPGRADE] gir1.2-folks-0.6 0.6.6-1ubuntu1 -> 0.6.6-1ubuntu2
[UPGRADE] gir1.2-freedesktop 1.31.6+git20120108.0a5c522a-0ubuntu1~12.04~ricotz0 -> 1.31.6+git20120111.526ba422-0ubuntu1~12.04~ricotz0
[UPGRADE] gir1.2-glib-2.0 1.31.6+git20120108.0a5c522a-0ubuntu1~12.04~ricotz0 -> 1.31.6+git20120111.526ba422-0ubuntu1~12.04~ricotz0
[UPGRADE] gir1.2-gtk-3.0 3.3.7+git20120111.9c7d795d-0ubuntu1~12.04~ricotz0 -> 3.3.7+git20120111.ff1e1e1f-0ubuntu1~12.04~ricotz0
[UPGRADE] gir1.2-networkmanager-1.0 0.9.2.0+git201112151936.6b31828-0ubuntu3 -> 0.9.2.0+git201201101813.0b30200-0ubuntu1
[UPGRADE] gir1.2-panelapplet-4.0 1:3.3.3-0ubuntu1 -> 1:3.3.3-0ubuntu2
[UPGRADE] gnome-accessibility-themes 3.3.3+git20120111.434fc3f2-0ubuntu1~12.04~ricotz0 -> 3.3.3+git20120111.a45f7683-0ubuntu1~12.04~ricotz0
[UPGRADE] gnome-control-center 1:3.2.2-0ubuntu6 -> 1:3.2.2-0ubuntu7
[UPGRADE] gnome-control-center-data 1:3.2.2-0ubuntu6 -> 1:3.2.2-0ubuntu7
[UPGRADE] gnome-disk-utility 3.0.2-2ubuntu3 -> 3.0.2-2ubuntu4
[UPGRADE] gnome-panel 1:3.3.3-0ubuntu1 -> 1:3.3.3-0ubuntu2
[UPGRADE] gnome-panel-data 1:3.3.3-0ubuntu1 -> 1:3.3.3-0ubuntu2
[UPGRADE] gnome-screensaver 3.2.0-1ubuntu3 -> 3.2.0-1ubuntu4
[UPGRADE] gnome-settings-daemon 3.2.2-0ubuntu7 -> 3.2.2-0ubuntu8
[UPGRADE] gnome-shell 3.3.3+git20120110.41f69561-0ubuntu1~12.04~ricotz1 -> 3.3.3+git20120110.41f69561-0ubuntu1~12.04~ricotz2
[UPGRADE] gnome-shell-common 3.3.3+git20120110.41f69561-0ubuntu1~12.04~ricotz1 -> 3.3.3+git20120110.41f69561-0ubuntu1~12.04~ricotz2
[UPGRADE] gnome-themes-standard 3.3.3+git20120111.434fc3f2-0ubuntu1~12.04~ricotz0 -> 3.3.3+git20120111.a45f7683-0ubuntu1~12.04~ricotz0
[UPGRADE] gobject-introspection 1.31.6+git20120108.0a5c522a-0ubuntu1~12.04~ricotz0 -> 1.31.6+git20120111.526ba422-0ubuntu1~12.04~ricotz0
[UPGRADE] ifupdown 0.7~alpha5.1ubuntu6 -> 0.7~beta2ubuntu1
[UPGRADE] libcamel-1.2-29 3.2.2-0ubuntu2 -> 3.2.3-0ubuntu1
[UPGRADE] libclutter-1.0-0 1.9.3+git20120103.88aaad9b-0ubuntu1~12.04~ricotz1 -> 1.9.3+git20120112.646cf236-0ubuntu1~12.04~ricotz0
[UPGRADE] libclutter-1.0-common 1.9.3+git20120103.88aaad9b-0ubuntu1~12.04~ricotz1 -> 1.9.3+git20120112.646cf236-0ubuntu1~12.04~ricotz0
[UPGRADE] libebackend-1.2-1 3.2.2-0ubuntu2 -> 3.2.3-0ubuntu1
[UPGRADE] libedata-book-1.2-11 3.2.2-0ubuntu2 -> 3.2.3-0ubuntu1
[UPGRADE] libedata-cal-1.2-13 3.2.2-0ubuntu2 -> 3.2.3-0ubuntu1
[UPGRADE] libedataserverui-3.0-1 3.2.2-0ubuntu2 -> 3.2.3-0ubuntu1
[UPGRADE] libevince3-3 3.2.1-1ubuntu6 -> 3.2.1-1ubuntu7
[UPGRADE] libfolks-eds25 0.6.6-1ubuntu1 -> 0.6.6-1ubuntu2
[UPGRADE] libfolks25 0.6.6-1ubuntu1 -> 0.6.6-1ubuntu2
[UPGRADE] libgail-3-0 3.3.7+git20120111.9c7d795d-0ubuntu1~12.04~ricotz0 -> 3.3.7+git20120111.ff1e1e1f-0ubuntu1~12.04~ricotz0
[UPGRADE] libgdu-gtk0 3.0.2-2ubuntu3 -> 3.0.2-2ubuntu4
[UPGRADE] libgdu0 3.0.2-2ubuntu3 -> 3.0.2-2ubuntu4
[UPGRADE] libgirepository-1.0-1 1.31.6+git20120108.0a5c522a-0ubuntu1~12.04~ricotz0 -> 1.31.6+git20120111.526ba422-0ubuntu1~12.04~ricotz0
[UPGRADE] libglib2.0-0 2.31.8-0ubuntu1 -> 2.31.8+git20120111.c3d6595f-0ubuntu1~12.04~ricotz0
[UPGRADE] libglib2.0-data 2.31.8-0ubuntu1 -> 2.31.8+git20120111.c3d6595f-0ubuntu1~12.04~ricotz0
[UPGRADE] libgnome-control-center1 1:3.2.2-0ubuntu6 -> 1:3.2.2-0ubuntu7
[UPGRADE] libgtk-3-0 3.3.7+git20120111.9c7d795d-0ubuntu1~12.04~ricotz0 -> 3.3.7+git20120111.ff1e1e1f-0ubuntu1~12.04~ricotz0
[UPGRADE] libgtk-3-bin 3.3.7+git20120111.9c7d795d-0ubuntu1~12.04~ricotz0 -> 3.3.7+git20120111.ff1e1e1f-0ubuntu1~12.04~ricotz0
[UPGRADE] libgtk-3-common 3.3.7+git20120111.9c7d795d-0ubuntu1~12.04~ricotz0 -> 3.3.7+git20120111.ff1e1e1f-0ubuntu1~12.04~ricotz0
[UPGRADE] libnautilus-extension1a 1:3.2.1-2ubuntu6 -> 1:3.2.1-2ubuntu7
[UPGRADE] libnm-glib4 0.9.2.0+git201112151936.6b31828-0ubuntu3 -> 0.9.2.0+git201201101813.0b30200-0ubuntu1
[UPGRADE] libnm-util2 0.9.2.0+git201112151936.6b31828-0ubuntu3 -> 0.9.2.0+git201201101813.0b30200-0ubuntu1
[UPGRADE] libnss3 3.13.1.with.ckbi.1.88-1ubuntu2 -> 3.13.1.with.ckbi.1.88-1ubuntu3
[UPGRADE] libnss3-1d 3.13.1.with.ckbi.1.88-1ubuntu2 -> 3.13.1.with.ckbi.1.88-1ubuntu3
[UPGRADE] libpanel-applet-4-0 1:3.3.3-0ubuntu1 -> 1:3.3.3-0ubuntu2
[UPGRADE] libssl1.0.0 1.0.0e-2ubuntu4 -> 1.0.0e-3ubuntu1
[UPGRADE] libwayland0 0.1.0~git20120105.44b529f2-0ubuntu0ricotz -> 0.1.0~git20120112.151ca457-0ubuntu0ricotz
[UPGRADE] libxml2 2.7.8.dfsg-5ubuntu1 -> 2.7.8.dfsg-5.1ubuntu1
[UPGRADE] midori 0.4.3+r4403-0~precise1 -> 0.4.3+r4421-0~precise1
[UPGRADE] nautilus 1:3.2.1-2ubuntu6 -> 1:3.2.1-2ubuntu7
[UPGRADE] nautilus-data 1:3.2.1-2ubuntu6 -> 1:3.2.1-2ubuntu7
[UPGRADE] openssl 1.0.0e-2ubuntu4 -> 1.0.0e-3ubuntu1
[UPGRADE] ubuntu-minimal 1.255 -> 1.256
[UPGRADE] ubuntu-standard 1.255 -> 1.256
===============================================================================

Log complete.
```

Boot hangs on "waiting for network configuration" for a while then it says "waiting an additional 60 seconds for network configuration". After that it says "Booting system without full network configuration". Basically it seems to spend an eternity on DHCP discovery. Once I eventually get to the desktop, networking is fine.

```
paul@precise-64:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
paul@precise-64:~$
```

I thought a possible workaround might be to comment out the **auto eth0** line and then start networking manually, but this made no difference.

I'm just about to try slim instead of lightdm in case this or a similar bug is affecting me:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/856810](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/856810)

---

### Post by clivejo on 2012-01-16
> **paul_in_london said:**
> I thought a possible workaround might be to comment out the **auto eth0** line and then start networking manually, but this made no difference.

I'm just about to try slim instead of lightdm in case this or a similar bug is affecting me:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/856810](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/856810)

Does your system still have the delay with the **auto lo** line commented out?

---

### Post by paul_in_london on 2012-01-16
> **clivejo said:**
> Does your system still have the delay with the **auto lo** line commented out?

Yes, I tried that. Made no difference. It was the original version of the file that I posted (and that's what I'm using again now).

It's not lightdm either in this case (same happens with slim).

This is happening for me in Precise on 2 different boxes. This one is 64 bit, the other is 32 bit. :confused:

---

### Post by ventrical on 2012-01-16
I'm getting 35 to 45 seconds  for  full boot to desktop on several different machines.

  I have one install that will periodically not detect the netowrk. Irt will detect the card and say it's running but the indicator is <off> and there is no  traffic.

---

### Post by ventrical on 2012-01-16
This one took 44 seconds but I subtracted 6 seconds because it took me that long to type in my password :)

---

### Post by paul_in_london on 2012-01-16
> **ventrical said:**
> This one took 44 seconds but I subtracted 6 seconds because it took me that long to type in my password :)

Hi ventrical,

It's all very weird.

I just fired up oneiric again on the same box to check and boot time is perfectly normal.

Btw, I'm not using Network Manager or anything on any of my installs.

None of my googling has borne fruit so far.

Cheers,

Paul

---

### Post by ventrical on 2012-01-16
ok .. I just updated THIS machine to the n.n.n-9 kernel and it  has nearly destroyed all my desktop settings in other users that I have created on this particular SATA 2 install (compiz settings especially). and added near 20 seconds to bootime!!

---

### Post by paul_in_london on 2012-01-16
> **ventrical said:**
> ok .. I just updated THIS machine to the n.n.n-9 kernel and it  has nearly destroyed all my desktop settings in other users that I have created on this particular SATA 2 install (compiz settings especially). and added near 20 seconds to bootime!!

Only 20 more seconds mate? You're lucky! :lolflag:

I did wonder at one point if it's kernel-related (and maybe to some extent it is), but the other day as a test I booted precise using the 3.2.0-7 kernel I think it was - and I'm pretty sure that kernel pre-dates this problem.

Btw, I'm not seeing this boot issue on my arch install either (which is currently on kernel 3.2.something-or-other.

---

### Post by ventrical on 2012-01-16
> **paul_in_london said:**
> Only 20 more seconds mate? You're lucky! :lolflag:

I did wonder at one point if it's kernel-related (and maybe to some extent it is), but the other day as a test I booted precise using the 3.2.0-7 kernel I think it was - and I'm pretty sure that kernel pre-dates this problem.

Btw, I'm not seeing this boot issue on my arch install either (which is currently on kernel 3.2.something-or-other.


 I just rolled back to 3.2.0-8 and I have all my desktops and compiz settings back !!:):)   Definitely appears to be a kernel regression.

---

### Post by paul_in_london on 2012-01-16
> **ventrical said:**
> I just rolled back to 3.2.0-8 and I have all my desktops and compiz settings back !!:):)   Definitely appears to be a kernel regression.

Glad you got your settings back. Prefer GS myself.

I wish booting 3.2.0-8 or earlier solved the boot issue though. :(

---

### Post by ventrical on 2012-01-16
> **paul_in_london said:**
> Glad you got your settings back. Prefer GS myself.

I wish booting 3.2.0-8 or earlier solved the boot issue though. :(

Nope .. not today my friend ! :)  But  I other installs on this machine with earlier kernels. mabey I can dig it out.

---

### Post by paul_in_london on 2012-01-16
> **ventrical said:**
> Nope .. not today my friend ! :)  But  I other installs on this machine with earlier kernels. mabey I can dig it out.

Thanks - I'm open to suggestions! :)

---

### Post by clivejo on 2012-01-16
Hi Paul,

Did you try installing boot chart and looking what process is causing the delay?

Mine is in the nmbd process.

---

### Post by paul_in_london on 2012-01-16
> **clivejo said:**
> Hi Paul,

Did you try installing boot chart and looking what process is causing the delay?

Mine is in the nmbd process.

Thanks. Maybe I should give bootchart a try (never used it before actually). Not sure about doing that tonight though. It's a little late (UK time). Don't think it's nmbd in my case though because I'm not using samba.

---

### Post by ventrical on 2012-01-16
It is starting to dog on some machines just after update..

---

### Post by paul_in_london on 2012-01-16
> **ventrical said:**
> It is starting to dog on some machines just after update..

But not *really* bad for you?

I had my fingers crossed a few mins ago when I booted back into precise and found that **ifupdown** was one of the available updates, but still no improvements after latest updates - another looooong reboot.

---

### Post by ventrical on 2012-01-16
> **paul_in_london said:**
> Hold down the shift key when the BIOS loads to get the GRUB menu, edit your GRUB menu entry before you boot and remove "quiet" and "splash" from the kernel line.

In my case it spends a LONG time waiting for network configuration.

I tried booting 3.2.0-7 last night and experienced the same problem.


On my 2.2GHz P4 machine my network card was intermitently on and off for past week and a half. So what I did was a shot in the dark. I chose Recovery mode from GRUB and each time I did that the network card worked OK again . The net card is not faulty because it works with other installs. It's just one install where it will just not power up.And ya know .. the funny thing is that I used to be able to set all this up manually (with Lucid,Maveric) but I just completely forgot how to do it :)

---

### Post by paul_in_london on 2012-01-16
> **ventrical said:**
> On my 2.2GHz P4 machine my network card was intermitently on and off for past week and a half. So what I did was a shot in the dark. I chose Recovery mode from GRUB and each time I did that the network card worked OK again . The net card is not faulty because it works with other installs. It's just one install where it will just not power up.And ya know .. the funny thing is that I used to be able to set all this up manually (with Lucid,Maveric) but I just completely forgot how to do it :)

Thanks again for your input mate. Do you mean booting into recovery mode and then choosing "resume normal boot" or whatever that menu option's called? Whenever I go into recovery mode for whatever reason I always reboot instead of trying to resume the boot.

From the testing I've done with other installs on the same box I've got no obvious reason to suspect there's any problem with the NIC or the router or the ethernet cables.

---

### Post by effenberg0x0 on 2012-01-16
I always suspect of network-manager and modem-manager. If you have it installed, and are willing to tweak things a little, I'd try apt-get remove'ing it, manually setting /etc/network/interfaces and /etc/resolv.conf. Worst case scenario, if there's no real improvement to boot time, you'll end up having to apt-get install network-manager.

EDIT: I know you mentioned to not be using it. Me too. But I really just feel comfortable when the thing is removed from the machine.

---

### Post by paul_in_london on 2012-01-16
Hi effenberg0x0,

I don't have network-manager or modem-manager installed (in precise or oneiric). I like to keep my installs as minimal as possible.

Need to call it a night in a minute, but will maybe install bootchart in the next day or two when I get a chance and see if that reveals anything.

Regards,

Paul

---

### Post by MAFoElffen on 2012-01-16
> **ventrical said:**
> On my 2.2GHz P4 machine my network card was intermitently on and off for past week and a half...  

the funny thing is that I used to be able to set all this up manually (with Lucid,Maveric) but I just completely forgot how to do it :)

You mean like this?
```

mafoelffen@maferr-serv-01:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# iface eth0 inet dhcp
 iface eth0 inet static
    address   192.168.2.5
    netmask   255.255.255.0
    network   192.168.2.0
    broadcast 192.168.2.255
    gateway   192.168.2.1

```It has not delay or problems with network config delays.

The problems I'm having after those updates were a delay/wait/timeout problem on mounting mdadm and hardware RAID arrays from fstab. 22 drives are on RAID. 

They worked during boot until those updates.  Now 1 array comes right up and the other one times out, but mounts no-problem right after boot.

---

### Post by paul_in_london on 2012-01-18
Just did a dummy run with bootchart in a VM @work. Never used it before. Will install it on my home PC later, but in the meantime...

After a reboot, I have this file:

```
/var/log/bootchart/precise-precise-20120118-1.tgz
```

and extracting the contents of the archive into my home directory gives me these files:

```
proc_stat.log
proc_ps.log
proc_diskstats.log
header
```

but isn't /var/log/bootchart also supposed to contain a .png file (the actual chart)?

Can someone who has it working in precise tell me what version of java I need (I assume that's the problem)?

Many thanks.

---

### Post by ventrical on 2012-01-18
> **paul_in_london said:**
> Just did a dummy run with bootchart in a VM @work. Never used it before. Will install it on my home PC later, but in the meantime...

After a reboot, I have this file:

```
/var/log/bootchart/precise-precise-20120118-1.tgz
```and extracting the contents of the archive into my home directory gives me these files:

```
proc_stat.log
proc_ps.log
proc_diskstats.log
header
```but isn't /var/log/bootchart also supposed to contain a .png file (the actual chart)?

Can someone who has it working in precise tell me what version of java I need (I assume that's the problem)?

Many thanks.


With each boot it makes two files. A .png file and a .tzg file. The .png file opens with the default image viewer which I think is Gimp?  Sometimes you just have to wait a few seconds for that file to show up..

---

### Post by cariboo on 2012-01-18
> **ventrical said:**
> With each boot it makes two files. A .png file and a .tzg file. The .png file opens with the default image viewer which I think is Gimp?  Sometimes you just have to wait a few seconds for that file to show up..

The default image viewer is eog (eye of gnome).

---

### Post by clivejo on 2012-01-18
> **paul_in_london said:**
> Just did a dummy run with bootchart in a VM @work. Never used it before. Will install it on my home PC later, but in the meantime...

After a reboot, I have this file:

```
/var/log/bootchart/precise-precise-20120118-1.tgz
```and extracting the contents of the archive into my home directory gives me these files:

```
proc_stat.log
proc_ps.log
proc_diskstats.log
header
```but isn't /var/log/bootchart also supposed to contain a .png file (the actual chart)?

Can someone who has it working in precise tell me what version of java I need (I assume that's the problem)?

Many thanks.

yes, there is supposed to be a png, with similar file-name to the tgz one.

---

### Post by paul_in_london on 2012-01-18
> **clivejo said:**
> yes, there is supposed to be a png, with similar file-name to the tgz one.

Have installed bootchart on the physical box now and I got the .png as expected (attached). Uploading it changed it to a .jpg

Can someone help me make sense of it?

Cheers.

---

### Post by cariboo on 2012-01-18
> **paul_in_london said:**
> Have installed bootchart on the physical box now and I got the .png as expected (attached). Uploading it changed it to a .jpg

Can someone help me make sense of it?

Cheers.

Could you please use one of the image hosting service to repost your bootchart, as the forum limits images to 1024X768, making the image unreadable. I'd suggest [imgur.com]("http://imgur.com/").

---

### Post by paul_in_london on 2012-01-18
> **cariboo907 said:**
> Could you please use one of the image hosting service to repost your bootchart, as the forum limits images to 1024X768, making the image unreadable. I'd suggest [imgur.com]("http://imgur.com/").

Sorry about that. imgur.com is actually blocked at the moment:

> We have blacked out Imgur today from 8am to 8pm, EST, to raise awareness about the danger that the Stop Online Piracy Act (SOPA) and the Protect IP Act (PIPA) pose to a free and vibrant Internet. It is important that our users understand the far-reaching and potentially disastrous repercussions that this legislation could have.

Please join the discussion. Take three minutes to save the web by clicking the button below and calling your senators. Tell them that you care about the freedom of the Internet.

Any other one that you'd recommend?

---

### Post by paul_in_london on 2012-01-18
Is this any good?

[http://i1052.photobucket.com/albums/s456/paul_in_london/precise-64-precise-20120118-1.png](http://i1052.photobucket.com/albums/s456/paul_in_london/precise-64-precise-20120118-1.png)

---

### Post by cariboo on 2012-01-18
> **paul_in_london said:**
> Is this any good?

[http://i1052.photobucket.com/albums/s456/paul_in_london/precise-64-precise-20120118-1.png](http://i1052.photobucket.com/albums/s456/paul_in_london/precise-64-precise-20120118-1.png)

Nope, it's even smaller than your original attachment.

---

### Post by ventrical on 2012-01-18
> **cariboo907 said:**
> The default image viewer is eog (eye of gnome).


Thanks for the correction Cariboo907

---

### Post by paul_in_london on 2012-01-18
> **cariboo907 said:**
> Nope, it's even smaller than your original attachment.

Another attempt:

[http://ubuntuone.com/6mxpExEQx8GIq8DZhmLb6k](http://ubuntuone.com/6mxpExEQx8GIq8DZhmLb6k)

(This is the original file - I haven't tampered with it in any way).

---

### Post by cariboo on 2012-01-18
> **paul_in_london said:**
> Another attempt:

[http://ubuntuone.com/6mxpExEQx8GIq8DZhmLb6k](http://ubuntuone.com/6mxpExEQx8GIq8DZhmLb6k)

(This is the original file - I haven't tampered with it in any way).

Much better, I'll have a look at it, and get back to you.

---

### Post by paul_in_london on 2012-01-18
> **cariboo907 said:**
> Much better, I'll have a look at it, and get back to you.

Thanks a lot. Sorry about the previous ones.

I can see the boot delay, but it's not very clear to me exactly where the problem lies.

---

### Post by ventrical on 2012-01-18
> **paul_in_london said:**
> Thanks a lot. Sorry about the previous ones.

I can see the boot delay, but it's not very clear to me exactly where the problem lies.


  Of course, just curious as to what type of hdd you are using . (if you haven't posted previously).

---

### Post by paul_in_london on 2012-01-18
> **ventrical said:**
> Of course, just curious as to what type of hdd you are using . (if you haven't posted previously).

```
paul@precise-64:~$ sudo lshw
precise-64
    description: Mini Tower Computer
    product: HP xw4300 Workstation (PS988AV)
    vendor: Hewlett-Packard
    serial: CZC6382QLQ
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=mini-tower family=103C_53335X sku=PS988AV uuid=D41902D8-124A-DB11-BBDA-A4F332A30017
  *-core
       description: Motherboard
       product: 0A00h
       vendor: Hewlett-Packard
       physical id: 0
       serial: CZC6382QLQ
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786D3 v01.08
          date: 03/10/2006
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: Intel(R) Pentium(R) D CPU 3.20GHz
          slot: XU1 PROCESSOR
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl vmx est cid cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
        *-cache:0
             description: L1 cache
             physical id: 7
             slot: Internal L1 Cache
             size: 28KiB
             capacity: 28KiB
             capabilities: burst internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 8
             slot: Cache L2
             size: 2MiB
             capacity: 4MiB
             capabilities: burst internal write-back data
     *-cpu:1
          description: CPU
          vendor: Intel
          physical id: 6
          bus info: cpu@1
          version: Intel(R) Pentium(R) D CPU 3.20GHz
          slot: XU1 PROCESSOR 2
          size: 3200MHz
          capacity: 3200MHz
          clock: 800MHz
          capabilities: cpufreq
     *-memory:0
          description: System Memory
          physical id: 36
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 18HTF12872AY-667B3
             vendor: JEDEC ID:2C FF FF FF FF FF FF FF
             physical id: 0
             serial: 14F44975
             slot: XMM1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous [empty]
             vendor: JEDEC ID:
             physical id: 1
             slot: XMM2
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 18HTF12872AY-667B3
             vendor: JEDEC ID:2C FF FF FF FF FF FF FF
             physical id: 2
             serial: 15F44975
             slot: XMM3
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous [empty]
             vendor: JEDEC ID:
             physical id: 3
             slot: XMM4
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 37
          slot: System board or motherboard
          capacity: 1MiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 1MiB
             width: 2 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82955X Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82955X PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:e9000000-eb1fffff ioport:e0000000(size=136314880)
           *-display
                description: VGA compatible controller
                product: NV41GL [Quadro FX 1400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:e9000000-e9ffffff memory:e0000000-e7ffffff memory:ea000000-eaffffff memory:e8000000-e801ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:e8500000-e8503fff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=4096) memory:80600000-807fffff ioport:80800000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:80200000-803fffff ioport:80400000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:2000(size=4096) memory:e8200000-e84fffff ioport:80000000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:3f:00.0
                logical name: eth0
                version: 01
                serial: 00:17:a4:f3:32:a3
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5752-v3.10 ip=192.168.1.66 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:46 memory:e8400000-e840ffff
        *-usb:0
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1000(size=32)
        *-usb:1
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1020(size=32)
        *-usb:2
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1040(size=32)
        *-usb:3
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:1060(size=32)
        *-usb:4
             description: USB controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:e8504000-e85043ff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:10a0(size=16)
           *-cdrom
                description: DVD reader
                product: COMBO SOHC-4836K
                vendor: LITE-ON
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/sr0
                version: SQK5
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: N10/ICH7 Family SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:10d0(size=8) ioport:10e8(size=4) ioport:10d8(size=8) ioport:10ec(size=4) ioport:10b0(size=16) memory:e8504400-e85047ff
           *-disk
                description: ATA Disk
                product: SAMSUNG HD160JJ/
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: ZM10
                serial: S0DFJ1ML816864
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003bcbd
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /mnt
                   version: 1.0
                   serial: df61b0c1-6cd7-470b-b5d0-62085da4bf86
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-04 22:00:55 filesystem=ext4 lastmountpoint=/ modified=2012-01-18 21:45:27 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered mounted=2012-01-18 21:45:27 state=mounted
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: c16f4cbf-43d3-45d7-b41e-a8ca3b339513
                   size: 39GiB
                   capacity: 39GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-08-28 17:45:56 filesystem=ext4 lastmountpoint=/ modified=2012-01-13 22:46:34 mount.fstype=ext4 mount.options=rw,noatime,nodiratime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-01-18 20:14:54 state=mounted
```

oneiric on /dev/sda1 - boots normally
precise on /dev/sda2 - you can see for yourself!

```
paul@precise-64:~$ ls -lad /var/run
lrwxrwxrwx 1 root root 4 Jan 18 20:14 /var/run -> /run
paul@precise-64:~$ ls -la /var/run/
total 48
drwxr-xr-x 17 root       root        620 Jan 18 23:36 .
drwxr-xr-x 23 root       root       4096 Jan 16 18:46 ..
-rw-r--r--  1 root       root          5 Jan 18 20:16 acpid.pid
srw-rw-rw-  1 root       root          0 Jan 18 20:16 acpid.socket
-rw-r--r--  1 root       root          5 Jan 18 20:16 atd.pid
drwxr-xr-x  2 root       root         60 Jan 18 20:17 console
drwxr-xr-x  2 root       root         60 Jan 18 20:17 ConsoleKit
-rw-r--r--  1 root       root          5 Jan 18 20:17 console-kit-daemon.pid
-rw-r--r--  1 root       root          5 Jan 18 20:16 crond.pid
----------  1 root       root          0 Jan 18 20:16 crond.reboot
drwxr-xr-x  2 messagebus messagebus   80 Jan 18 20:14 dbus
-rw-r--r--  1 root       root          4 Jan 18 20:15 dhclient.eth0.pid
drwxr-xr-x  2 dnsmasq    nogroup      60 Jan 18 20:16 dnsmasq
drwsrwsrwt  2 root       root         60 Jan 18 20:14 initramfs
drwx--x--x  3 root       root         60 Jan 18 20:16 lightdm
-rw-r--r--  1 root       root          5 Jan 18 20:16 lightdm.pid
drwxrwxrwt  2 root       root         80 Jan 18 21:24 lock
-rw-r--r--  1 root       root        132 Jan 18 20:14 motd
drwxr-xr-x  2 root       root         60 Jan 18 20:14 mount
drwxr-xr-x  2 root       root         80 Jan 18 20:15 network
-rw-r--r--  1 root       root          0 Jan 18 20:14 network-interface-security
drwxr-xr-x  4 root       root         80 Jan 18 20:17 pm-utils
-rw-r--r--  1 root       root          4 Jan 18 20:14 rsyslogd.pid
drwxrwxr-x  2 root       utmp         40 Jan 18 20:14 screen
drwxr-xr-x  2 root       root         40 Jan 18 20:14 sendsigs.omit.d
drwxrwxrwt  3 root       root        160 Jan 18 23:37 shm
drwxr-xr-x  7 root       root        180 Jan 18 23:28 udev
drwx------  2 root       root         40 Jan 18 20:17 udisks
-rw-r--r--  1 root       root          4 Jan 18 20:14 upstart-socket-bridge.pid
-rw-r--r--  1 root       root          4 Jan 18 20:14 upstart-udev-bridge.pid
-rw-rw-r--  1 root       utmp       2304 Jan 18 20:17 utmp
paul@precise-64:~$
```

```
paul@precise-64:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=c16f4cbf-43d3-45d7-b41e-a8ca3b339513 /               ext4    errors=remount-ro,noatime,nodiratime 0       1
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
tmpfs /tmp     tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
cache-chromium /home/paul/.cache/chromium tmpfs defaults,noauto,noatime,mode=1777 0 0
#firefox /home/paul/.mozilla/firefox/m209x9n3.default tmpfs size=128M,noauto,noatime,user,exec,uid=1000,gid=100 0 0
#firefox-trunk /home/paul/.mozilla/firefox-trunk/m209x9n3.default tmpfs size=128M,noauto,noatime,user,exec,uid=1000,gid=100 0 0
paul@precise-64:~$
```

Everything was fine until about a week ago.

---

### Post by cariboo on 2012-01-18
> **ventrical said:**
> Of course, just curious as to what type of hdd you are using . (if you haven't posted previously).

I've been running bootchart since Oct 27th, and just doing a quick check, hard drive size/interface/speed doesn't seem to have a lot to do with boot speed. I found that some of the slowest boot times, 01:14:35, had the highest data transfer rates, 88MB/s, while one of the quicker ones, 00:43:65, had a data transfer rate of 75MB/s.

---

### Post by ventrical on 2012-01-18
> **cariboo907 said:**
> I've been running bootchart since Oct 27th, and just doing a quick check, hard drive size/interface/speed doesn't seem to have a lot to do with boot speed. I found that some of the slowest boot times, 01:14:35, had the highest data transfer rates, 88MB/s, while one of the quicker ones, 00:43:65, had a data transfer rate of 75MB/s.

Yes , agreed , but I originally had a long boot with alpha Oneiric (as most of us did) and there was a fix .. there was a 120 second wait-state that could be editied out. i am wondering if that is the case here.

@paul_in_london..

  I notice the 667MHz being reported  concerning your memory. I am assuming you have an 800MHz bus for mem. I must admit this seems curious to me (from a hardware aspect)  This is the first time i have seen an odd parity  in MHz , but , then thats just me.

 Also .. THANK you !! I think you helped me more than I helped you because I now see some problems when I ran that command  <sudo lhsw>  you did, on my own machines. Thanks.

also @ Cariboo907 
I originally had a real hard time with my SATA 2 drive and (I'm not sure about Paul's system) but I could not have the IDE hdd and SATA running at the same time.
I'm not declaring that this is the problem.. just  putting it up here.

---

### Post by paul_in_london on 2012-01-18
> **ventrical said:**
> @paul_in_london..

  I notice the 667MHz being reported  concerning your memory. I am assuming you have an 800MHz bus for mem. I must admit this seems curious to me (from a hardware aspect)  This is the first time i have seen an odd parity  in MHz , but , then thats just me.

 Also .. THANK you !! I think you helped me more than I helped you because I now see some problems when I ran that command  <sudo lhsw>  you did, on my own machines. Thanks.

also @ Cariboo907 
I originally had a real hard time with my SATA 2 drive and (I'm not sure about Paul's system) but I could not have the IDE hdd and SATA running at the same time.
I'm not declaring that this is the problem.. just  putting it up here.

As the Aussies say, no wukkas! Hardware's not my strong point. I've seen exactly the same boot issue on my other precise install (32 bit) on a different box so it's pretty mystifying (again all was fine on that box as well until the software updates froma a week ago). It seems pretty unlikely that both boxes would suddenly have developed a hardware problem at the same time.

@ventrical: Just to give you a clue, a little clip for you (UK ad):

[https://www.youtube.com/watch?v=SeTyv51C8pE](https://www.youtube.com/watch?v=SeTyv51C8pE)

---

### Post by ventrical on 2012-01-18
> **paul_in_london said:**
> As the Aussies say, no wukkas! Hardware's not my strong point. I've seen exactly the same boot issue on my other precise install (32 bit) on a different box so it's pretty mystifying (again all was fine on that box as well until the software updates froma a week ago). It seems pretty unlikely that both boxes would suddenly have developed a hardware problem at the same time.

@ventrical: Just to give you a clue, a little clip for you (UK ad):

[https://www.youtube.com/watch?v=SeTyv51C8pE](https://www.youtube.com/watch?v=SeTyv51C8pE)

I'll never be the same after that :)

Ok.. I can agree ... definitely something from the updates. I just realized that this PC I am typing from  (one of my main towers ) is only running my mem @166Mhz and it's a 555MHz bus @ 333MHz reported in the BIOS .. and there is no feature in CMOS to adjust it (as I can see at the moment).


9pm here .. must be 1 in the morning there ....  don't you ever sleep..? :)

---

### Post by paul_in_london on 2012-01-18
> **ventrical said:**
> I'll never be the same after that :)

Ok.. I can agree ... definitely something from the updates. I just realized that this PC I am typing from  (one of my main towers ) is only running my mem @166Mhz and it's a 555MHz bus @ 333MHz reported in the BIOS .. and there is no feature in CMOS to adjust it (as I can see at the moment).


9pm here .. must be 1 in the morning there ....  don't you ever sleep..? :)

Quite a good clip eh? It's 2am now. Really need to get some sleep. Wish I knew what this problem was. Ok, here's a similar ad I like just before I go:

[https://www.youtube.com/watch?v=UU1RQRXGH9U](https://www.youtube.com/watch?v=UU1RQRXGH9U)

---

### Post by ventrical on 2012-01-18
I just cracked open one of my towers and noticed I had  a PC2700 CL2.5 matched with a PC2700 CL3. I took out the CL2.6 256MB DDR and here is before and after:

---

### Post by ventrical on 2012-01-18
It also blew my SATA2 drive wide open.. wow...

I am almost embarrassed to say I did not see this ..

---

### Post by mc4man on 2012-01-18
I would take a look at firestarter, maybe get rid of it & see if your boot time goes back to normal

---

### Post by paul_in_london on 2012-01-19
> **mc4man said:**
> I would take a look at firestarter, maybe get rid of it & see if your boot time goes back to normal

Thanks for the tip. I haven't reconfigured firestarter in any way recently (and it's not causing any problems for me in oneiric), but I'll try that when I get home.

Btw, I know the transition from **/var/run** to **/run** seemed to cause similar problems for some people, but I don't see why this would suddenly have become an issue on this install a week ago when it wasn't before. One of the original things I tried was recreating the sym links etc. just in case.

---

### Post by ventrical on 2012-01-19
And here is my boot time with proper 400MHz 512 memory for this machine.

---

### Post by paul_in_london on 2012-01-19
> **ventrical said:**
> And here is my boot time with proper 400MHz 512 memory for this machine.

Well you're doing a lot better than me mate! :lolflag:

---

### Post by ventrical on 2012-01-19
> **paul_in_london said:**
> Well you're doing a lot better than me mate! :lolflag:
There was a .conf file that we editied during the last beta. I recall you were here testing with us. I think it was harry33 or Mac4man that pointed it out.. or mabey effenberg - but I remember that we had to knock off this <120> second wait that was in that file during boot and I just cannot recall what it was. I am assuming , perhaps , that mabey that file might still exist is some cases ..

---

### Post by paul_in_london on 2012-01-19
> **ventrical said:**
> There was a .conf file that we editied during the last beta. I recall you were here testing with us. I think it was harry33 or Mac4man that pointed it out.. or mabey effenberg - but I remember that we had to knock of this <120> second wait that was in that file during boot and I just cannot recall what it was. I am assuming , perhaps , that mabey that file might still exist is some cases ..

That's interesting. I don't remember having to do anything like that. It would be nice to know what the conf file is/was called! :)

---

### Post by ventrical on 2012-01-19
I'm also just curious as to the performance of your hdds. Could you run Disk Utility , do a 'read benchmark only', then screenshot them and post them ?

---

### Post by ventrical on 2012-01-19
Ok.. so far I found this one ...

[http://ubuntuforums.org/showthread.php?t=1853484](http://ubuntuforums.org/showthread.php?t=1853484)

---

### Post by jasonrisenburg on 2012-01-19
[QUOTE=paul_in_london;11606582]Is anyone else seeing this?

I've found consistently (much) longer boot times with PP (64 bit) after today's updates. Finally booted up my OO install (32 bit) on the same box and found boot time to be normal so it seems to me it's something to do with today's PP updates.

I'm in Fremont,Ohio and It was normal for me. How was the internet speed doing?

---

### Post by ventrical on 2012-01-19
and yet another ... this is the one !!

[http://ubuntuforums.org/showpost.php?p=11242427&postcount=37](http://ubuntuforums.org/showpost.php?p=11242427&postcount=37)

---

### Post by ventrical on 2012-01-19
and of course .. here is the start of that whole thread started by none other than  yours truely :)

[http://ubuntuforums.org/showthread.php?t=1842022](http://ubuntuforums.org/showthread.php?t=1842022)

---

### Post by paul_in_london on 2012-01-19
> **ventrical said:**
> I'm also just curious as to the performance of your hdds. Could you run Disk Utility , do a 'read benchmark only', then screenshot them and post them ?

I'm @work right now, but will try and do that later...

---

### Post by forcecore on 2012-01-19
I can tell too that on my X201 (i5 CPU, 7200rpm HDD) boot time is very long, even login takes very long. I keep checking updates and maybe this is only temporary.

---

### Post by paul_in_london on 2012-01-19
> **jasonrisenburg said:**
> [QUOTE=paul_in_london;11606582]Is anyone else seeing this?

I've found consistently (much) longer boot times with PP (64 bit) after today's updates. Finally booted up my OO install (32 bit) on the same box and found boot time to be normal so it seems to me it's something to do with today's PP updates.

I'm in Fremont,Ohio and It was normal for me. How was the internet speed doing?

The "today" in question was 7 or 8 days ago now. I know this thread's a bit convoluted. I had no network issues before or during the updates from that day. The boot trouble all started after those particular updates (see earlier in the thread for details of the specific set of updates). It may be the fallacy of *post hoc ergo propter hoc*, it's hard to say.

When I **eventually** get to the desktop there are still no network problems (or any other problems) at all. Everything is fine other than the severely slow boot.

---

### Post by ventrical on 2012-01-19
here is the format of the new failsafe.conf

                                 # failsafe  description "Failsafe Boot Delay" author "Clint Byrum <clint@ubuntu.com>"  start on filesystem and net-device-up IFACE=lo stop on static-network-up or runlevel  console output  script     # Determine if plymouth is available     if [ -x /bin/plymouth ] && /bin/plymouth --ping ; then         PLYMOUTH=/bin/plymouth     else         PLYMOUTH=":"     fi      # The point here is to wait for 2 minutes before forcibly booting      # the system. Anything that is in an "or" condition with 'started      # failsafe' in rc-sysinit deserves consideration for mentioning in     # these messages. currently only static-network-up counts for that.      sleep 20      # Plymouth errors should not stop the script because we *must* reach     # the end of this script to avoid letting the system spin forever     # waiting on it to start.     $PLYMOUTH message --text="Waiting for network configuration..." || :     sleep 40      $PLYMOUTH message --text="Waiting up to 60 more seconds for network configuration..." || :     sleep 59     $PLYMOUTH message --text="Booting system without full network configuration..." || :      # give user 1 second to see this message since plymouth will go     # away as soon as failsafe starts.     sleep 1     exec initctl emit --no-wait failsafe-boot end script  post-start exec    logger -t 'failsafe' -p daemon.warning "Failsafe of 120 seconds reached."  

 ...so it's still 2 minutes - but I am not sure it applies to your case Paul.

---

### Post by paul_in_london on 2012-01-19
> **ventrical said:**
> here is the format of the new failsafe.conf

                                 # failsafe  description "Failsafe Boot Delay" author "Clint Byrum <clint@ubuntu.com>"  start on filesystem and net-device-up IFACE=lo stop on static-network-up or runlevel  console output  script     # Determine if plymouth is available     if [ -x /bin/plymouth ] && /bin/plymouth --ping ; then         PLYMOUTH=/bin/plymouth     else         PLYMOUTH=":"     fi      # The point here is to wait for 2 minutes before forcibly booting      # the system. Anything that is in an "or" condition with 'started      # failsafe' in rc-sysinit deserves consideration for mentioning in     # these messages. currently only static-network-up counts for that.      sleep 20      # Plymouth errors should not stop the script because we *must* reach     # the end of this script to avoid letting the system spin forever     # waiting on it to start.     $PLYMOUTH message --text="Waiting for network configuration..." || :     sleep 40      $PLYMOUTH message --text="Waiting up to 60 more seconds for network configuration..." || :     sleep 59     $PLYMOUTH message --text="Booting system without full network configuration..." || :      # give user 1 second to see this message since plymouth will go     # away as soon as failsafe starts.     sleep 1     exec initctl emit --no-wait failsafe-boot end script  post-start exec    logger -t 'failsafe' -p daemon.warning "Failsafe of 120 seconds reached."  

 ...so it's still 2 minutes - but I am not sure it applies to your case Paul.

Thanks very much ventrical. That file doesn't actually ring any bells with me at all, but I'll take it under advisement as they say! Still at work so can't look into it now unfortunately.

---

### Post by zika on 2012-01-19
```
echo manual | sudo tee -a /etc/init/failsafe.override
```

---

### Post by mc4man on 2012-01-19
> **paul_in_london said:**
>  I haven't reconfigured firestarter in any way recently (and it's not causing any problems for me in oneiric), but I'll try that when I get home.

Btw, I know the transition from **/var/run** to **/run** seemed to cause similar problems for some people, but I don't see why this would suddenly have become an issue on this install a week ago when it wasn't before. One of the original things I tried was recreating the sym links etc. just in case.
Wouldn't know anything about fs or it's config, never used, but a quick test suggests that having it installed with it's default conf will increase boot time significantly, around 3X here.

---

### Post by paul_in_london on 2012-01-19
> **mc4man said:**
> Wouldn't know anything about fs or it's config, never used, but a quick test suggests that having it installed with it's default conf will increase boot time significantly, around 3X here.

Ok, thanks again for your feedback. FS is just a front-end for iptables (like gufw). I'll test the effect of disabling it later. Don't know why it should suddenly be causing a problem though for the last week or so. I've just got it set to whitelist inbound and outbound traffic (standard protocols - http, https etc).

EDIT: AFAIK Firestarter is hardly maintained any more so maybe it would also be a good time to switch to gufw or something similar.

---

### Post by paul_in_london on 2012-01-19
> **zika said:**
> ```
echo manual | sudo tee -a /etc/init/failsafe.override
```

And thanks to you too zika for this suggestion.

---

### Post by VMC on 2012-01-19
> **paul_in_london said:**
> And thanks to you too zika for this suggestion.

Interesting. Never seen this before. Your appending to a file that I don't even have?

---

### Post by paul_in_london on 2012-01-19
> **VMC said:**
> Interesting. Never seen this before. Your appending to a file that I don't even have?

I did quickly check earlier on my precise VM and it's there (without any ill effects):

```
paul@precise:~$ ls -la /etc/init/failsafe.conf
-rw-r--r-- 1 root root 1345 Oct 27 06:08 /etc/init/failsafe.conf
```

EDIT - Contents:

```
cat /etc/init/failsafe.conf
# failsafe

description "Failsafe Boot Delay"
author "Clint Byrum <clint@ubuntu.com>"

start on filesystem and net-device-up IFACE=lo
stop on static-network-up or runlevel

console output

script
	# Determine if plymouth is available
	if [ -x /bin/plymouth ] && /bin/plymouth --ping ; then
		PLYMOUTH=/bin/plymouth
	else
		PLYMOUTH=":"
	fi

    # The point here is to wait for 2 minutes before forcibly booting 
    # the system. Anything that is in an "or" condition with 'started 
    # failsafe' in rc-sysinit deserves consideration for mentioning in
    # these messages. currently only static-network-up counts for that.

	sleep 20

    # Plymouth errors should not stop the script because we *must* reach
    # the end of this script to avoid letting the system spin forever
    # waiting on it to start.
	$PLYMOUTH message --text="Waiting for network configuration..." || :
	sleep 40

	$PLYMOUTH message --text="Waiting up to 60 more seconds for network configuration..." || :
	sleep 59
	$PLYMOUTH message --text="Booting system without full network configuration..." || :

    # give user 1 second to see this message since plymouth will go
    # away as soon as failsafe starts.
	sleep 1
    exec initctl emit --no-wait failsafe-boot
end script

post-start exec	logger -t 'failsafe' -p daemon.warning "Failsafe of 120 seconds reached."
```

---

### Post by zika on 2012-01-19
> **VMC said:**
> Interesting. Never seen this before. Your appending to a file that I don't even have?For all services having .conf files in /etc/init automatic start can be turned-off with a file name_of_the_service.override that has a line &#8222;manual&#8220; in it. Not more, not less than that...
If You do not want lightdm to start by itself, or network-manager, or...
The same as (simple) making (empty) .xbindkeys.noauto in $HOME prevents xbindkeys from auto-start..

---

### Post by paul_in_london on 2012-01-19
Well bingo! :)

I didn't really want to remove firestarter, just to stop it starting automatically at boot (temporarily as a test).

It wasn't immediately obvious how to do it, but this is what I did after a bit of searching:

```
sudo mv /etc/network/if-down.d/50firestarter /etc/network/if-down.d/50firestarter.HIDDEN
sudo mv /etc/network/if-up.d/50firestarter /etc/network/if-up.d/50firestarter.HIDDEN
```

This is the *only* thing I did and (coincidence or otherwise) the **ifupdown** package was among the ones updated right before this boot problem started.

Here are the new bootcharts.

After 1st reboot: [http://ubuntuone.com/1GqQgMssYUoXfn0gCC9D5o](http://ubuntuone.com/1GqQgMssYUoXfn0gCC9D5o)
After 2nd reboot: [http://ubuntuone.com/4vECcuZ2GFTA7FuakuU6Ad](http://ubuntuone.com/4vECcuZ2GFTA7FuakuU6Ad)

---

### Post by ventrical on 2012-01-19
Bravo !!

:)

---

### Post by paul_in_london on 2012-01-19
> **ventrical said:**
> Bravo !!

:)

Thanks! :)

Not as good as your boot times obviously, bur definitely a step forward. :lolflag:

It seems very strange that this started happening, especially when firestarter isn't a firewall *per se* - just a GUI for controlling it.

Thanks to everyone else too for all the responses by the way and not least **mc4man**!

---

### Post by mc4man on 2012-01-19
If you go back & review your orig. slow bootchart you'll notice that during the initial period of high activity firestarter* runs twice. When it stops the 2nd time then the long period of inactivity starts. When firestarter* resumes coincides with the resumption of your boot.
What's happening, if anything other then some timeout, during that long period no clue.
Seems like firestarter is  a package that needs updating...

(your current boot seems a little slow but not that bad, are you manually logging in? (I think many people use an auto login to shave some time off.
Appears it takes about 25 sec's or so after to login till done, here it's about 12 or so but I use unity only..

Edit: looking at bootcharts in the image viewer reminds me of how nonsensical the 250ms fade on overlay-scrollbar's thumb is, reopened a bug on that

---

### Post by paul_in_london on 2012-01-19
> **mc4man said:**
> If you go back & review your orig. slow bootchart you'll notice that during the initial period of high activity firestarter* runs twice. When it stops the 2nd time then the long period of inactivity starts. When firestarter* resumes coincides with the resumption of your boot.
What's happening, if anything other then some timeout, during that long period no clue.
Seems like firestarter is  a package that needs updating...

(your current boot seems a little slow but not that bad, are you manually logging in? (I think many people use an auto login to shave some time off.
Appears it takes about 25 sec's or so after to login till done, here it's about 12 or so but I use unity only..

Edit: looking at bootcharts in the image viewer reminds me of how nonsensical the 250ms fade on overlay-scrollbar's thumb is, reopened a bug on that

Thanks again for your help. Yes I think I read somewhere a while back that FS isn't really maintained any more and I can't remember the last time I noticed getting a FS update. At some point I'll probably remove it and try gufw instead. All a bit weird and maybe it was somehow related to the recent **ifupdown** update(s).

I do always log in manually actually. Old habits die hard I suppose. :) I'm using the ricotz-testing and ricotz unstable ppas (the latter, more recently, instead of xorg-edgers to get X Server 1.12) and that may partly explain the additional sluggishness after login.

---

### Post by cariboo on 2012-01-19
> **paul_in_london said:**
> Thanks again for your help. Yes I think I read somewhere a while back that FS isn't really maintained any more and I can't remember the last time I noticed getting a FS update. At some point I'll probably remove it and try gufw instead. All a bit weird and maybe it was somehow related to the recent **ifupdown** update(s).

I do always log in manually actually. Old habits die hard I suppose. :) I'm using the ricotz-testing and ricotz unstable ppas (the latter, more recently, instead of xorg-edgers to get X Server 1.12) and that may partly explain the additional sluggishness after login.

Firestarter hasn't been updated since 2005, the package maintainer does fix any small bugs that come up, but that's about it. I'd really suggest you remove it, and use gufw instead.

---

### Post by VMC on 2012-01-19
I didn't know what Firestarter was until this thread. Googling gave me some answers..."A Modern Linux Firewall". Which brings to mind that my Fedora16 takes almost twice as long as either, Precise and/or Mint12. I didn't setup any firewall, and not that in tune with Red Hat's architecture , but I think SELinux may play a part.

---

### Post by paul_in_london on 2012-01-20
> **cariboo907 said:**
> Firestarter hasn't been updated since 2005, the package maintainer does fix any small bugs that come up, but that's about it. I'd really suggest you remove it, and use gufw instead.

Thanks **cariboo907**. My thoughts have been moving in that direction. It'll be interesting to see what happens using gufw instead.

---

### Post by paul_in_london on 2012-01-20
> **VMC said:**
> I didn't know what Firestarter was until this thread. Googling gave me some answers..."A Modern Linux Firewall". Which brings to mind that my Fedora16 takes almost twice as long as either, Precise and/or Mint12. I didn't setup any firewall, and not that in tune with Red Hat's architecture , but I think SELinux may play a part.

It's basically a front-end for the **ufw** command-line equivalent (which, in turn, is simpler than manipulating **iptables** directly), but it's nice to use a GUI for certain things! :)

---

### Post by cariboo on 2012-01-20
Firestarter also has the ability to monitor the firewall, you have to run it as root though. We see many new users using this function, and getting scared because of all the hits against it.

I personally don't like that feature, as it may be one other point a cracker may use to gain entry to the system.

---

### Post by paul_in_london on 2012-01-20
> **cariboo907 said:**
> Firestarter also has the ability to monitor the firewall, you have to run it as root though. We see many new users using this function, and getting scared because of all the hits against it.

I personally don't like that feature, as it may be one other point a cracker may use to gain entry to the system.

Well having now purged firestarter and installed gufw instead I see that gufw doesn't have that feature, but that's ok. I was slightly mistaken earlier in that firestarter depends directly on iptables, whereas gufw depends on iptables via ufw. In fact ufw on its own (I've discovered) would be perfectly adequate.

When I installed gufw, ufw was set up as an upstart job:

```
initctl show-config | grep ufw
...
ufw
  start on ((starting network-interface or starting network-manager) or starting networking)
  stop on runlevel [!023456]
...
```

About 10 seconds is added to the previous boot time (where I'd disabled firestarter at boot), but I can live with that.

Here's the bootchart:

```
http://ubuntuone.com/3bb29dynmiRqoLbsd06ziB
```

and after I got to the desktop (without running gufw) I checked that ufw was still active:

```
paul@precise-64:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
1935                       ALLOW       Anywhere
25                         ALLOW       Anywhere
53                         ALLOW       Anywhere
80                         ALLOW       Anywhere
110                        ALLOW       Anywhere
443                        ALLOW       Anywhere
1935                       ALLOW       Anywhere (v6)
25                         ALLOW       Anywhere (v6)
53                         ALLOW       Anywhere (v6)
80                         ALLOW       Anywhere (v6)
110                        ALLOW       Anywhere (v6)
443                        ALLOW       Anywhere (v6)

paul@precise-64:~$
```

So thanks again to everyone and I think it would be reasonable to mark this thread as solved. :)

EDIT: **ufw** was already installed so, in retrospect, all I really needed to do (instead of installing **gufw**) would have been:

```
sudo ufw enable # by default ufw is initially disabled
#
# By default, ufw denies all incoming traffic but allows all outgoing traffic
# so just open a few ports - e.g.:
#
sudo ufw allow 25 # SMTP 
sudo ufw allow 53 # DNS 
sudo ufw allow 80 # HTTP
sudo ufw allow 110 # POP
sudo ufw allow 443 # HTTPS
```

---

### Post by Alan F on 2012-01-22
> **paul_in_london said:**
> Well bingo! :)

Here are the new bootcharts.

After 1st reboot: [http://ubuntuone.com/1GqQgMssYUoXfn0gCC9D5o](http://ubuntuone.com/1GqQgMssYUoXfn0gCC9D5o)
After 2nd reboot: [http://ubuntuone.com/4vECcuZ2GFTA7FuakuU6Ad](http://ubuntuone.com/4vECcuZ2GFTA7FuakuU6Ad)

In both of these bootcharts very little, if any, is being loaded by ureadahead. Why is this?

I have the same with an Oneiric 64 bit install that I have been unable to resolve (clearing pack files, reboot etc)

---

### Post by paul_in_london on 2012-01-22
> **Alan F said:**
> In both of these bootcharts very little, if any, is being loaded by ureadahead. Why is this?

I have the same with an Oneiric 64 bit install that I have been unable to resolve (clearing pack files, reboot etc)

Thanks for pointing that out. ureadahead never seems to have worked properly for me in any release actually, but I've never really looked into it.

---

### Post by VMC on 2012-01-22
I have experienced a much longer boot time for the past 3 ISO installs. I have in the past ignored bootlog, mainly because I didn't know what I was looking at or what I was looking for.
 Normal Ubuntu boot for my machine is 20 - 22 seconds.  Looking more closely at bootchart now it takes 58 secs! If I had a previous bootchart I could compare results.

so from the 20 second mark onward is where something is eating up my boot time. 

In observation, I see the normal 20 - 22 sec boot, then the screen goes dark for the rest of the boot.

I'll look further. In the meantime here's the chart:

edit: it appears tinypic doesn't allow resizing. I'l find another link. Anyone know what site to use for temp image. I don't need another sign-up account. So imgur is out.

edit2: It appears that xorg, gnome settings and compiz have activity up in the 55 second range. Maybe one of them is a culprit - like xorg.

edit3: Here's the ubuntuone image- Is their a way to thumnail it. Its way to big?
Edit again: neither one of the below suggestions worked. The image was huge!
Thanks cariboo for the fix.

[[IMG]http://i.imgur.com/Eathll.png[/IMG]](http://imgur.com/Eathl)

---

### Post by ventrical on 2012-01-22
> **VMC said:**
> I have experienced a much longer boot time for the past 3 ISO installs. I have in the past ignored bootlog, mainly because I didn't know what I was looking at or what I was looking for.
 Normal Ubuntu boot for my machine is 20 - 22 seconds.  Looking more closely at bootchart now it takes 58 secs! If I had a previous bootchart I could compare results.

so from the 20 second mark onward is where something is eating up my boot time. 

In observation, I see the normal 20 - 22 sec boot, then the screen goes dark for the rest of the boot.

I'll look further. In the meantime here's the chart:

[http://oi39.tinypic.com/6xzrr5.jpg](http://oi39.tinypic.com/6xzrr5.jpg)

edit: it appears tinypic doesn't allow resizing. I'l find another link. Anyone know what site to use for temp image. I don't need another sign-up account. So imgur is out.

edit2: It appears that xorg, gnome settings and compiz have activity up in the 55 second range. Maybe one of them is a culprit - like xorg.

Why can't you upload them here with <manage attatchments> tool ?

---

### Post by paul_in_london on 2012-01-22
> **VMC said:**
> I have experienced a much longer boot time for the past 3 ISO installs. I have in the past ignored bootlog, mainly because I didn't know what I was looking at or what I was looking for.
 Normal Ubuntu boot for my machine is 20 - 22 seconds.  Looking more closely at bootchart now it takes 58 secs! If I had a previous bootchart I could compare results.

so from the 20 second mark onward is where something is eating up my boot time. 

In observation, I see the normal 20 - 22 sec boot, then the screen goes dark for the rest of the boot.

I'll look further. In the meantime here's the chart:

[http://oi39.tinypic.com/6xzrr5.jpg]("http://oi39.tinypic.com/6xzrr5.jpg")

edit: it appears tinypic doesn't allow resizing. I'l find another link. Anyone know what site to use for temp image. I don't need another sign-up account. So imgur is out.

edit2: It appears that xorg, gnome settings and compiz have activity up in the 55 second range. Maybe one of them is a culprit - like xorg.

I ended up using my ubuntuone account to upload the bootcharts. Seemed to work pretty well.

---

### Post by xyzzyman on 2012-01-23
> **Alan F said:**
> In both of these bootcharts very little, if any, is being loaded by ureadahead. Why is this?

I have the same with an Oneiric 64 bit install that I have been unable to resolve (clearing pack files, reboot etc)

It's because he is using a mainline kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/). Mainline kernels doesn't have the necessary patches for ureadahead so it crashes. I've been frustrated that people seem to recommend them without ever mentioning that. They also break apparmor, and the 3.2+ don't have the ASPM fixes, along with a number of other backports and patches. They are very good when troubleshooting but you do lose alot of the Ubuntu work.

---

### Post by VMC on 2012-01-23
OK, Today's iso has boot time back to normal for me. I'll have to re-load bootlog and see what changed.

---

