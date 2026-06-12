---
title: "Alpha 3 ISO Testing"
date: 2012-07-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by balloons on 2012-07-24
Alpha 3 iso's are here! Grab your favorite iso and jump in.

[http://iso.qa.ubuntu.com/qatracker/milestones/226/builds](http://iso.qa.ubuntu.com/qatracker/milestones/226/builds)

If you need help, here is the wiki link describing how to iso test. If you get stuck, send a message back here and we can help :-)
[https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

Interesting things in this release are the new software-properties manager, as well as the final 3.5 kernel. Previous issues with hardware, suspend/resume and graphics should all be watched out for with the new kernel. Additionally, the ubiquitly installer is starting to land new code as the new features to support dropping the alternate isos are landed, and should be tested.

As always, be on the look out for bugs people have reported earlier. This list is a good place to have a quick glance:

[http://iso.qa.ubuntu.com/qatracker/reports/defects](http://iso.qa.ubuntu.com/qatracker/reports/defects)

Finally, this link gives the tech overview for alpha 3. It's still a WIP, but lists some of the changes found in these isos.

[https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha3](https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha3)

---

### Post by xebian on 2012-07-24
Kubuntu with KDE 4.8.90 ?  4.8.95 has already been outdated by 4.8.97 - Jul 11 released.  IMHO, it's pointless testing with outdated framework.

---

### Post by ronacc on 2012-07-24
> **guitara said:**
> Alpha 3 iso's are here! Grab your favorite iso and jump in.



where ?  see SS

---

### Post by mc4man on 2012-07-24
> **ronacc said:**
> where ?  see SS
from 1st link in post one, pick the one you want, click on green icon, brings you to this page in screen, ect.

---

### Post by ronacc on 2012-07-24
thanks

---

### Post by balloons on 2012-07-24
> **ronacc said:**
> thanks

Ronacc, yes.. There won't be a link on releases until it's actually released. From now until Thursday (when the release is planned) we as a community test the images to make sure they are stable and work for installation. If we find bugs, we fix them or note them in the release notes if we can't fix them (yet). Make sense?

---

### Post by ventrical on 2012-07-24
So far ... awesome. Ubiquity does this little adjustment thing now on my  system  with ATi Radeon graphics adapter. It will focus in , adjust, offset , then center itself and focus again. Actually it is very kewl and 'punchy' :)

---

### Post by ventrical on 2012-07-24
Flawless install!:)

```
ventrical@ventrical-P4M266A-8237:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)
ventrical@ventrical-P4M266A-8237:~$ 

```

---

### Post by arpanaut on 2012-07-24
Well, Glory BE...

For the first time since Nov. last year the daily-live iso has installed completely 
without having to remove the ubiquity-slideshow-ubuntu from the live session.

Yahoooooo!  I'm back in business with iso testing. 
I was pretty burned out having ubiquity crash out EVERY time.
On top of that, Apport has been quiet at least for now. (20 min. or so)

Good job on fixing Ubiquity!

Color me: :mrgreen:

---

### Post by ronacc on 2012-07-24
no joy , amd64 desktop installed but kernel panicked  when I attempted to update the repos to complete language installation .

---

### Post by fjgaude on 2012-07-24
No issues with my main box amd64-bit install on an SSD partition, with Intel graphics.

---

### Post by effenberg0x0 on 2012-07-25
> **fjgaude said:**
> No issues with my main box amd64-bit install on an SSD partition, with Intel graphics.

Same hardware as fjgaude's but branded ASUS. Nothing out of the ordinary. Same old problems with display backlight, which I'm already working on a fix. 

Power consumption is increased for 3 kernels already, giving me 2 hours less (normal is 8hrs). But there's a chance this is also part of the ACPI problems that cause the brightness issue. 

Same Unity/Nautilus issues mentioned in recent threads. Still seeing network (cifs/nfs) problems when working with large lan files or lan shares with too many files/dirs for a long time (a couple hours). 

Apport crashing apport. 

The SysIO thing is still here (I have no idea what it is and haven't had the time to look for it as I said I would - sorry - life is tough):
```

[    5.874509] it87: Found IT8721F chip at 0x290, revision 1
[    5.874546] ACPI Warning: 0x0000000000000295-0x0000000000000296 SystemIO conflicts with Region \_SB_.PCI0.SBRG.SIOR.ECRE 1 (20120320/utaddress-251)
[    5.923675] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver


```
colord-sane/libdbus is back, we jumped one release (at least for me):
```
[   10.753484] colord-sane[1459]: segfault at 5a ip 00007fe61c25d8d5 sp 00007fff3c6eb470 error 4 in libdbus-1.so.3.5.8[7fe61c236000+42000]
```

This is new:```

[   18.727266] mount: sending ioctl 5310 to a partition!

```
Regards,
Effenberg

---

### Post by dino99 on 2012-07-25
> **effenberg0x0 said:**
> 

```

[    5.874509] it87: Found IT8721F chip at 0x290, revision 1
[    5.874546] ACPI Warning: 0x0000000000000295-0x0000000000000296 SystemIO conflicts with Region \_SB_.PCI0.SBRG.SIOR.ECRE 1 (20120320/utaddress-251)
[    5.923675] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver


```


Looks like this report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027370](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027370)

---

### Post by effenberg0x0 on 2012-07-25
> **dino99 said:**
> Looks like this report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027370](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027370)

Hi Dino, thanks. Saw your data there, I'll +1. Have you noticed exactly in which of the latest updates this thing started? It would be nice to diff the last version before that to our current.

Regards,
Effenberg

---

### Post by dino99 on 2012-07-25
> **effenberg0x0 said:**
> Hi Dino, thanks. Saw your data there, I'll +1. Have you noticed exactly in which of the latest updates this thing started? It would be nice to diff the last version before that to our current.

Regards,
Effenberg

All depends on the hardware used :confused:
On my side , with some old mobo & cards, acpi has been an issue since kernel 3 serie has started (at least).
And when i've seen the 3.5+ kernel changelogs, adding & tweaking the acpi/lapic fonctions/features, i got less trouble related to acpi. Hopes 3.6 will fix it completly :P

note:
I've posted on bugzilla (copy/paste on launchpad) with some details.

---

### Post by balloons on 2012-07-25
> **dino99 said:**
> All depends on the hardware used :confused:
On my side , with some old mobo & cards, acpi has been an issue since kernel 3 serie has started (at least).
And when i've seen the 3.5+ kernel changelogs, adding & tweaking the acpi/lapic fonctions/features, i got less trouble related to acpi. Hopes 3.6 will fix it completly :P

note:
I've posted on bugzilla (copy/paste on launchpad) with some details.

Yea.. 3.5 seems like a stepping stone -- lots of things feel halfway..

---

### Post by effenberg0x0 on 2012-07-25
> **guitara said:**
> Yea.. 3.5 seems like a stepping stone -- lots of things feel halfway..

There can only be [[COLOR="Red"]_**one reason**_[/COLOR]]("http://www.eweek.com/c/a/Linux-and-Open-Source/Microsoft-Ranks-17-on-List-of-Top-Linux-Kernel-Contributors-847629/") :P

---

### Post by ronacc on 2012-07-25
I disagree with the thought expressed in that reference , I have no illusion that M$ it thinking "if you can't beat em join em " it is much more likely " if you can't beat em eat em " . they are looking to taint the kernel beyond all hopes of redemption . All contributions to the kernel from M$ should be rejected with extreme prejudice and any that are already there should be intermediately ripped out even if it sets us back years . The long term survival of linux is at stakes .

---

### Post by cariboo on 2012-07-25
> **ronacc said:**
> I disagree with the thought expressed in that reference , I have no illusion that M$ it thinking "if you can't beat em join em " it is much more likely " if you can't beat em eat em " . they are looking to taint the kernel beyond all hopes of redemption . All contributions to the kernel from M$ should be rejected with extreme prejudice and any that are already there should be intermediately ripped out even if it sets us back years . The long term survival of linux is at stakes .

This is just plain silly Linus has the final say as to what goes into the kernel and what doesn't. Unless of course you're saying that MS paid him off.

Now lets get back on topic.

---

### Post by ronacc on 2012-07-25
> **cariboo907 said:**
> This is just plain silly Linus has the final say as to what goes into the kernel and what doesn't. Unless of course you're saying that MS paid him off.

Now lets get back on topic.

It is not always necessary to bribe or intimidate someone , a gift can work quite well , ask the trojans .

---

### Post by ronacc on 2012-07-26
a3 amd64 desktop installed ok but kernel panicked as soon as I tried to update the language packs , was able to reboot and not log into the gui ctrl>alt>F1 at login screen and update from console and install a few things . updated ok yesterday from synaptic . this AM ( thur july 26 ) kernel panicked even from console and when it does it puts naks all over the partition so that on next reboot I have to run FSCK to fix it , this is getting very old .Its beginning to look like I may have to wait for 1304 to get a working install :mad:

---

### Post by effenberg0x0 on 2012-07-26
Ronacc, I'm on AMD 64-bit too. I did not get a kernel panic, but X crashed when I was installing pt-BR language (in that window that warns about incomplete language support). However, I could switch to a VT, kill X and restart lightdm.This is not new: For a month or so, every time I try to get the language support it crashes this exact same way.

Regards,
Effenberg

---

### Post by dino99 on 2012-07-26
believe that glib2 has something to do with that language trouble (at least on my end)

ricotz/testing is building a new version with:

Revert unintential IAPI break for g_key_file_load_from_data()
+
+    The old (length) annotation actually wasn't being read.  Changing
+    it to an array was telling g-i that it was an array of utf8, which
+    is clearly not true.
+
+    We *could* add (element-type guint8), but that would change it to a
+    byte array, as opposed to the original utf8 version.
+
+    Just removing the annotation should bring us back to where we
+    were, which was fine.
+
+    [https://bugzilla.gnome.org/show_bug.cgi?id=680310](https://bugzilla.gnome.org/show_bug.cgi?id=680310)

Be more careful when using xlocale
+
+    Bug 680074 shows that we may end up in situations where only
+    some of the xlocale functions we need are available. Rather than
+    trying to find the minimal set of required functions for each
+    use, define a global USE_XLOCALE and only use any xlocale functions
+    if we have a full set.
+

---

### Post by ronacc on 2012-07-26
> **effenberg0x0 said:**
> Ronacc, I'm on AMD 64-bit too. I did not get a kernel panic, but X crashed when I was installing pt-BR language (in that window that warns about incomplete language support). However, I could switch to a VT, kill X and restart lightdm.This is not new: For a month or so, every time I try to get the language support it crashes this exact same way.

Regards,
Effenberg

it is possible that x crashing is what precipitated the kernel panic  in the case that I posted about , I was doing the same thing you were , responding to the warning about language support . but in my case the end result was a completely frozen system and a naked up hd partition . I could fill up several pages with other things that will cause a kernel panic so to keep it brief I'll just say trying to do anything at all will panic it . It is noticeably worse in a gui than a console and worse in unity than GS I can't get any usefull information because logging is cut foo at the instant of the panic .

---

### Post by balloons on 2012-07-26
> **ronacc said:**
> it is possible that x crashing is what precipitated the kernel panic  in the case that I posted about , I was doing the same thing you were , responding to the warning about language support . but in my case the end result was a completely frozen system and a naked up hd partition . I could fill up several pages with other things that will cause a kernel panic so to keep it brief I'll just say trying to do anything at all will panic it . It is noticeably worse in a gui than a console and worse in unity than GS I can't get any usefull information because logging is cut foo at the instant of the panic .

How are you installing? Choosing a different language perhaps? I'm wondering if we could somehow recreate in a VM, or similar hardware or do you not think so?

---

### Post by ronacc on 2012-07-26
> **guitara said:**
> How are you installing? Choosing a different language perhaps? I'm wondering if we could somehow recreate in a VM, or similar hardware or do you not think so?

installed from dvd ( startup disk creator wouldn't make a bootable stick ) simple install the defaults are right for me language , keyboard etc , installed to a partition on one of my hd's  changed the location of the grub install , it chose the wrong drive but that is not relevant as it boots ok I just can't do much without it kernel panicing . installed latest mainline kernel per request from Christopher M. Penalver , fighting to get it to boot right now . if you want to try a VM my hardware is gigabyte motherboard ga-m55plus-s3g , AMD64x2 4600+ , Nvidia 7600gs , 4 gig ddr2 , 2 ide drives , 4 sata drives , 1 ide dvd drive .

what ever it is there is no chance at all of it being a hardware problem , quantal with the 3.4.0-5 kernel works flawlessly as do 2 sabayon installs ( 8 and 9 ) 2 debian installs ( squeeze and sid ) , 1 suse install ( I forget which # ) .

note acts the same with both noveau and nvidia-current .

---

### Post by effenberg0x0 on 2012-07-26
> **ronacc said:**
> it is possible that x crashing is what precipitated the kernel panic  in the case that I posted about , I was doing the same thing you were , responding to the warning about language support . but in my case the end result was a completely frozen system and a naked up hd partition . 

I think I would normally disregard this option. In theory, we *should* be able to crash any userland application and the kernel *should* stay solid. I don't know of a connection between the two things. 
(But that's my opinion anyway - I am not involved in Kernel or Ubuntu development)

Question: Does your machine also crash like that when not inside X? I mean, say you start Ubuntu, immediately switch to a VT, stop lightdm, kill remaining X if any, maybe even unload nvidia/nvidia-current, nouveau module(s), then create some console activity? Like:
Ctrl+Alt+F6
sudo service lightdm stop
sudo kill -s KILL $(grep /usr/bin/X)
for module in $(lsmod | grep -i 'nvidia\|nvidia-current\|nouveau'| awk 'BEGIN {FS=" "} {print $1}'); do sudo modprobe -r $module; done

Then run console stuff, to try to create some activity, top, mtr, fsck, glxinfo (from mesa-utils pkg) whatever, maybe load stuff simultaneously in other tty, etc. 

If we can start to exclude stuff: X, VGA/LAN/WLAN modules as potential causes, maybe you can find the culprit.   

Regards,
Effenberg

**EDIT:** Since we share similar hardware (similar CPU, same Arch, same VGA Vendor) maybe I could spot something different in our kernel messages. If you want to, mail me your /var/log/kern.log on (my forum handle)@ubuntu.com or post it here and I'll have a look/diff it from mine.

---

### Post by ronacc on 2012-07-26
it sometimes crashes even when not in X . It seems more stable that way but still panics sometimes , you need to be doing something most of the time for it to panic but it is totally inconsistant in a console with lightdm stopped sometimes forinstance running sudo apt-get update it may sometimes complete and sometimes panic halfway through , same thing with lightdm when running synaptic or just opening a browser , FF chrome or Opera but sometimes not , whatever is causing it it happens so fast it leaves no tracks . I just booted into it and logged into G-S but did nothing just let it sit for 2 hrs and no panic just sitting there . But on the other hand it has panicked just starting the desktop sometimes . I've rebooted so many times I'm afraid I'm going to wear out grub :lolflag:

---

### Post by effenberg0x0 on 2012-07-26
> **ronacc said:**
> it sometimes crashes even when not in X . It seems more stable that way but still panics sometimes , you need to be doing something most of the time for it to panic but it is totally inconsistant in a console with lightdm stopped sometimes forinstance running sudo apt-get update it may sometimes complete and sometimes panic halfway through , same thing with lightdm when running synaptic or just opening a browser , FF chrome or Opera but sometimes not , whatever is causing it it happens so fast it leaves no tracks . I just booted into it and logged into G-S but did nothing just let it sit for 2 hrs and no panic just sitting there . But on the other hand it has panicked just starting the desktop sometimes . I've rebooted so many times I'm afraid I'm going to wear out grub :lolflag:

What if it's the NIC module? We know some realtek modules were unstable a while ago, broadcom was never reliable, etc. You could try to unload whatever your module is (see below), to see if you feel the PC more stable. That would be a solid guess IMO.

[23:45:22] ahsl@AL-DESK01:[~]: lspci -vvvv | grep -i eth -A 10
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 51
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at fafff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at faff8000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
 [23:45:30] ahsl@AL-DESK01:[~]: sudo modprobe -r r8169
 [23:45:32] ahsl@AL-DESK01:[~]: 

Regards,
Effenberg

EDIT: You can even test it inside X, no prob, only your wired, wireless, whichever you disable, will drop until you reload the module.

---

### Post by ronacc on 2012-07-26
I'll give that a try tomorrow , I think my nic is a realtek 8185 , I've never had a problem with it before and 3.4.0-5 doesn't but at this point I'll try anything .

---

### Post by ronacc on 2012-07-27
here is a link to the specs for my motherboard , [ http://www.gigabyte.eu/products/product-page.aspx?pid=2283#sp ]( http://www.gigabyte.eu/products/product-page.aspx?pid=2283#sp ) .

 my wireless is a realtek 8185 so I plugged in wired connection . killed lightdm and checked with top and saw no x running and tried to update and got a kernel panic halfway through , rebooted and let it go to desktop and it updated fine but on reboot after the update it blackscreens  instantly from grub ( this is on my A3 install ) but my updated precise install now runs stably with 3.5.0-6 so atleast thats progress .

I'm going to try a daily install and see what happens .

---

### Post by effenberg0x0 on 2012-07-27
> **ronacc said:**
> here is a link to the specs for my motherboard , [ http://www.gigabyte.eu/products/product-page.aspx?pid=2283#sp ]( http://www.gigabyte.eu/products/product-page.aspx?pid=2283#sp ) .

 my wireless is a realtek 8185 so I plugged in wired connection . killed lightdm and checked with top and saw no x running and tried to update and got a kernel panic halfway through , rebooted and let it go to desktop and it updated fine but on reboot after the update it blackscreens  instantly from grub ( this is on my A3 install ) but my updated precise install now runs stably with 3.5.0-6 so atleast thats progress .

I'm going to try a daily install and see what happens .

Hopefully they fixed whatever was causing this on 3.5.0-6, this one is being hard to solve. 

I forgot to ask you before: Are BIOS settings at more or less default values? Is it overclocked (FSB/Multipliers CPU, RAM Freq./Timings, etc)? I have seen a motherboard with a similar chipset that would only work reliably with default frequencies/timings and with scaling support disabled (like SpeedStep, Cool'n'Quiet, PowerNow, etc on the BIOS) in a specific kernel series. That one was hard to catch back then. Maybe that's also something you could have a look at. 

Regards,
Effenberg

---

### Post by ronacc on 2012-07-27
no overclock but I'll have to check the scaling I don't remember wheather I set that or not , for that mater I flashed the bios a couple of years ago and don't think I've messed with any settings since then except to rearrange the boot priority on occasion . I just shut that box down for the night , I'll check the scaling tomorrow when I boot it .

---

### Post by ronacc on 2012-07-28
yesterdays daily failed to install , todays daily installed and is working perfectly so something resolved what ever has been giving me grief about 3.5  .

---

