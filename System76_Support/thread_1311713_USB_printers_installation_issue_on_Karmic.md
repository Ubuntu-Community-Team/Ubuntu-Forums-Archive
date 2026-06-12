---
title: "USB printers installation issue on Karmic"
date: 2009-11-02
forum: System76 Support
---

### Post by arepaking on 2009-11-02
Folks,
Have you had any issues while trying to install a USB printer on Karmic 64b? For some reasons my daru3 is not able to detect a USB printer (Samsung ML-6060) that was working fine back in Jaunty.

I also tried through CUPS but I never get the USB installation option.

Any thoughts on this?

---

### Post by thomasaaron on 2009-11-03
So, if you plug your printer into the USB port, and then go to System > Admin > Printer, the printer isn't even detected?

Does anything else work in that USB port? (I've been seeing some USB port issues that I've not quite gotten solved yet. Want to make sure that this isn't one of them.)

---

### Post by arepaking on 2009-11-03
Hi Thomas,
Thanks for your reply.

I connected the printer in every USB port on my daru3 and is not being recognized. I used a 9.04 Live CD and it works like a charm.

Something changed in the way Karmic (or the new linux kernel) handles the usb devices.

---

### Post by thomasaaron on 2009-11-03
Could you verify that a different USB device is detected in your Karmic install? Maybe a flash drive or something?

---

### Post by arepaking on 2009-11-03
> **thomasaaron said:**
> Could you verify that a different USB device is detected in your Karmic install? Maybe a flash drive or something?

It has been verifed already. The following devices worked fine:
1) USB flash drive
2) Iphone
3) External USB HD.

---

### Post by zob on 2009-11-03
I have the same problem.
Everything shows up except my brother hl-2140 printer. I also have a thread (with a posting of my lsusb).

---

### Post by Cygnia on 2009-11-03
It's just the opposite for me. In Jaunty, my HP Inkjet printer wouldn't work until I downloaded the more recent version of hplip directly from the HP website. Now under Karmic it installed automatically and prints perfectly. (All on a fresh install of Karmic on a PanP4n.)

---

### Post by zob on 2009-11-03
I think I can answer for both myself and arepaking when I say it's not a driver problem.
The printer doesn't even get recognized as connected to the USB-plug. It's as if the cable wasn't there. But I have tested the USB-connection in a windows dual-boot and it works perfectly (and I'm still not talking about drivers or printing - just hardware getting recognized as connected).

It is actually very strange.

---

### Post by ctsdownloads on 2009-11-03
> **arepaking said:**
> Folks,
Have you had any issues while trying to install a USB printer on Karmic 64b? For some reasons my daru3 is not able to detect a USB printer (Samsung ML-6060) that was working fine back in Jaunty.

I also tried through CUPS but I never get the USB installation option.

Any thoughts on this?


CUPS definitely shows this as a "mostly working" printer. Still, I bet it is just having a bad day.

So to clarify, what happens "exactly" when you goto System>Administration>Printing ?

You are not seeing the printer showing up automatically in there and you are 100% that it is turned on. Don't laugh, I did this to myself yesterday - I totally forgot to turn it on! :)

If it is not showing up there, before going further, from Applications>Accessories>Terminal , paste in lsusb .

Then copy/paste the entire results back here. All this does is as you stated, shows if the hardware is "physically there". We will get into drivers later. That command will help us determine whether Ubuntu "sees" the printer or not.

As for it being a driver issue, I would not write this off just yet. More than likely a bug, it may be possible to do some stuff manually to work around the issue.

---

### Post by zob on 2009-11-03
I hope I'm not hijacking anything here. I'm convinced that we have the same problem.

So I will give my lsusb.

```
lars@lars-desktop:~$ lsusb
Bus 001 Device 006: ID 0499:1011 Yamaha Corp. P-250
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 002: ID 0bc2:3101 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
This is the same with the printer on or off. Strangely it is the only thing that doesn't get recognized. Also it doesn't help to move the printercable to another position, fx. where something else has been recognized. And at the moment it's in the back of the computer, not in a hub (though I've tried that to).


It's not there. I does get recognized (same cable and everything) in my windows dual-boot.

Please arepaking. Tell me if you do any progress. And also tell me if you think my case is not related and I'm hijacking your thread.

Oh and System>Administration>Printing is empty. Very empty.

---

### Post by ctsdownloads on 2009-11-03
> **zob said:**
> I hope I'm not hijacking anything here. I'm convinced that we have the same problem.

So I will give my lsusb.

```
lars@lars-desktop:~$ lsusb
Bus 001 Device 006: ID 0499:1011 Yamaha Corp. P-250
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 002: ID 0bc2:3101 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
This is the same with the printer on or off. Strangely it is the only thing that doesn't get recognized. Also it doesn't help to move the printercable to another position, fx. where something else has been recognized. And at the moment it's in the back of the computer, not in a hub (though I've tried that to).


It's not there. I does get recognized (same cable and everything) in my windows dual-boot.

Please arepaking. Tell me if you do any progress. And also tell me if you think my case is not related and I'm hijacking your thread.

Oh and System>Administration>Printing is empty. Very empty.

Kind of brings us to a dead stop if you are connecting straight to the PC (not a hub) and it is not even showing up under lsusb.

I'd say run a dmesg | tail, but it seems silly if it is not being detected by lsusb.

I also read in another thread at one time, there was a conflict issue with the Parallel and USB ports. I bet this is the issue again. It was buried [in this mess]("http://ubuntuforums.org/showthread.php?t=341621") someplace.

---

### Post by ctsdownloads on 2009-11-03
Just found an awesome [non-Ubuntu specific thread]("http://sidux.com/PNphpBB2-viewtopic-t-8635.html") for dealing with broken lsusb/CUPS detection issues that might help.

```
modprobe lp
echo lp >> /etc/modules
apt-get remove --purge cupsys
apt-get install cupsys or apt-get install cupsys cupsys-driver-gutenprint  hplip
```

---

### Post by zob on 2009-11-04
Thanks a lot ctsdownloads. I hope you will follow up again.

With respect to your last post. Doesn't do anything for me, and lp is already in my /etc/modules and is listed at lsmod, so it is loaded.

dmesg however returned an interesting result. First dmesg | tail before turning printer on.
```
lars@lars-desktop:~$ dmesg | tail
[   11.203629] type=1505 audit(1257341850.845:21): operation="profile_replace" pid=919 name=/usr/sbin/tcpdump
[   15.542120] usplash:375 freeing invalid memtype ffffffffe0000000-fffffffff0000000
[   17.909874] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   17.909895] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   17.909931] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   21.432527] eth0: no IPv6 routers present
[   40.820100] kjournald starting.  Commit interval 5 seconds
[   40.820137] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   40.889906] EXT3 FS on sdd4, internal journal
[   40.889921] EXT3-fs: mounted filesystem with writeback data mode.

```

Now I turn the printer on:
```
lars@lars-desktop:~$ dmesg | tail
[   17.909931] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   21.432527] eth0: no IPv6 routers present
[   40.820100] kjournald starting.  Commit interval 5 seconds
[   40.820137] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   40.889906] EXT3 FS on sdd4, internal journal
[   40.889921] EXT3-fs: mounted filesystem with writeback data mode.
[  711.292551] usb 2-3: new full speed USB device using ohci_hcd and address 2
[  711.528665] usb 2-3: configuration #1 chosen from 1 choice
[  711.612618] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0033
[  711.612639] usbcore: registered new interface driver usblp

```

Turn printer of:
```
lars@lars-desktop:~$ dmesg | tail
[   40.820100] kjournald starting.  Commit interval 5 seconds
[   40.820137] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   40.889906] EXT3 FS on sdd4, internal journal
[   40.889921] EXT3-fs: mounted filesystem with writeback data mode.
[  711.292551] usb 2-3: new full speed USB device using ohci_hcd and address 2
[  711.528665] usb 2-3: configuration #1 chosen from 1 choice
[  711.612618] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0033
[  711.612639] usbcore: registered new interface driver usblp
[  788.067558] usb 2-3: USB disconnect, address 2
[  788.067750] usblp0: removed

```

Turn on printer 2. time.
```
lars@lars-desktop:~$ dmesg | tail
[   40.889921] EXT3-fs: mounted filesystem with writeback data mode.
[  711.292551] usb 2-3: new full speed USB device using ohci_hcd and address 2
[  711.528665] usb 2-3: configuration #1 chosen from 1 choice
[  711.612618] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0033
[  711.612639] usbcore: registered new interface driver usblp
[  788.067558] usb 2-3: USB disconnect, address 2
[  788.067750] usblp0: removed
[  839.642521] usb 2-3: new full speed USB device using ohci_hcd and address 3
[  839.878191] usb 2-3: configuration #1 chosen from 1 choice
[  839.889194] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0033

```

Clearly something is going on in the dmesg.
Sadly lsusb still shows no trace of my printer.
```
lars@lars-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0499:1011 Yamaha Corp. P-250
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 002: ID 0bc2:3101 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


I don't know. What's this line from the first time printer is turned on?
```
[  711.612639] usbcore: registered new interface driver usblp
```

What is usblp, is that the module lp? Oh it's in my lsmod along with lp:
```
lars@lars-desktop:~$ lsmod |grep lp
usblp                  15136  0 
lp                     11908  0 
parport                40528  3 ppdev,lp,parport_pc

```

Hmmm. ctsdownloads? Anyone?

---

### Post by ctsdownloads on 2009-11-04
Do not recall seeing the answer to whether or not you are using a hub or not?

---

### Post by thomasaaron on 2009-11-04
Well, HAL is definitely recognizing your printer, per...
```

[  711.612618] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0033
[  711.612639] usbcore: registered new interface driver usblp
```

Now, if you go to System > Admin > Printers and click 'New' does CUPS see it?
I asked that earlier, and you answered. But your answer seemed a bit ambiguous to me.

(I'm not too concerned with lsusb just yet.)

---

### Post by zob on 2009-11-04
ctsdownloads, Right now I'm not in a hub.
I have also tried connecting thru a hub.
No difference in lsusb.


thomasaaron, I can't press new. It's greyed out though my printer is on and connected.

---

### Post by ctsdownloads on 2009-11-04
> **zob said:**
> ctsdownloads, Right now I'm not in a hub.
I have also tried connecting thru a hub.
No difference in lsusb.


thomasaaron, I can't press new. It's greyed out though my printer is on and connected.

Well that is weird. Right above the new button, try 

```
Server>New>Printer
```

 from the pull down menu instead.

---

### Post by zob on 2009-11-04
That's greyed out too.

---

### Post by atentik on 2009-11-04
Great to know I am not the only[one ]("http://ubuntuforums.org/showthread.php?t=1311632") experiencing this trouble. In fact, when I did 
> lp
lp: Error - scheduler not responding!

What is going on with Karmic? Non comparable to Windows 7. Trouble free.

---

### Post by zob on 2009-11-04
9.04 was troublefree for me to. Havn't tried that thing, what was it...? windows?

---

### Post by HotShotDJ on 2009-11-04
> **atentik said:**
> What is going on with Karmic? Non comparable to Windows 7. Trouble free.Your joking, right?
[http://www.pcworld.com/article/174342/windows_7_upgrade_woes_mount_endless_reboots_and_product_key_problems.html](http://www.pcworld.com/article/174342/windows_7_upgrade_woes_mount_endless_reboots_and_product_key_problems.html)  -- how about THIS forum that currently has 5927 threads with Windows 7 related issues?

And this is after millions of dollars and years of development by both Microsoft and hardware vendors for what amounts to a service pack for Vista.  It is hardly trouble free.  We've got some serious [Stockholm Syndrome]("http://www.mental-health-matters.com/index.php?option=com_content&view=article&id=167") going on with some people's perception of Microsoft products.

---

### Post by atentik on 2009-11-04
> **HotShotDJ said:**
> Your joking, right?
[http://www.pcworld.com/article/174342/windows_7_upgrade_woes_mount_endless_reboots_and_product_key_problems.html](http://www.pcworld.com/article/174342/windows_7_upgrade_woes_mount_endless_reboots_and_product_key_problems.html)  -- how about THIS forum that currently has 5927 threads with Windows 7 related issues?

And this is after millions of dollars and years of development by both Microsoft and hardware vendors for what amounts to a service pack for Vista.  It is hardly trouble free.  We've got some serious [Stockholm Syndrome]("http://www.mental-health-matters.com/index.php?option=com_content&view=article&id=167") going on with some people's perception of Microsoft products.

Nope. I have had and used Windows 7 for 3 months plus without any problems. At least with Windows, you know you'd get help when you ask....

---

### Post by zob on 2009-11-04
Hey guys. Don't make this a windows is better than ubuntu thread it's very uninteresting.

Please help out with this strange bug. Well I found this. So it is or has been a known bug it seems.
[https://bugs.launchpad.net/ubuntu/karmic/+source/udev/+bug/420015?comments=all](https://bugs.launchpad.net/ubuntu/karmic/+source/udev/+bug/420015?comments=all)

Someone suggests that this would fix the problem
```
sudo aa-enforce cupsd
```

It still doesn't let me see my printer via lsusb, but it does change things in dmesg |tail
```
[ 2850.049704] type=1505 audit(1257360769.685:22): operation="profile_replace" pid=6172 name=/usr/lib/cups/backend/cups-pdf
[ 2850.049942] type=1505 audit(1257360769.685:23): operation="profile_replace" pid=6172 name=/usr/sbin/cupsd
[ 2869.722555] usb 2-3: new full speed USB device using ohci_hcd and address 3
[ 2869.961662] usb 2-3: configuration #1 chosen from 1 choice
[ 2869.976057] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0033

```

I posted earlier dmesg earlier in this thread for comparison. But the new thing is that now it actually starts to mention cups.

---

### Post by atentik on 2009-11-04
> **zob said:**
> Hey guys. Don't make this a windows is better than ubuntu thread it's very uninteresting.

Please help out with this strange bug. Well I found this. So it is or has been a known bug it seems.
[https://bugs.launchpad.net/ubuntu/karmic/+source/udev/+bug/420015?comments=all](https://bugs.launchpad.net/ubuntu/karmic/+source/udev/+bug/420015?comments=all)

Someone suggests that this would fix the problem
```
sudo aa-enforce cupsd
```

It still doesn't let me see my printer via lsusb, but it does change things in dmesg |tail
```
[ 2850.049704] type=1505 audit(1257360769.685:22): operation="profile_replace" pid=6172 name=/usr/lib/cups/backend/cups-pdf
[ 2850.049942] type=1505 audit(1257360769.685:23): operation="profile_replace" pid=6172 name=/usr/sbin/cupsd
[ 2869.722555] usb 2-3: new full speed USB device using ohci_hcd and address 3
[ 2869.961662] usb 2-3: configuration #1 chosen from 1 choice
[ 2869.976057] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0033

```

I posted earlier dmesg earlier in this thread for comparison. But the new thing is that now it actually starts to mention cups.

Thanks. I was able to run the command and be able to now see my printer by 
> lsusb
Bus 002 Device 006: ID 03f0:1d17 Hewlett-Packard LaserJet 1320
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
.
But when I go to System->Administration->Printing, I still get the same error message:
> **CUPS server error**
There was an error during the CUPS operation: 'client-error-bad-request'.

---

### Post by zob on 2009-11-04
Sorry to say. I don't know where to go from here. Looks like a bug.
Might have something to do with apparmor protecting CUPS, but damn it's difficult.

---

### Post by HotShotDJ on 2009-11-04
> **zob said:**
> Hey guys. Don't make this a windows is better than ubuntu thread it's very uninteresting.Oh, I agree with you... a Windows vs. Linux flame-fest is completely uninteresting.  At the same time, the whole "Why can't Linux make bug free software like Microsoft does" canard needs to be challenged where ever it rears its ugly head.

But beyond that, I certainly think we should return to our regularly scheduled program already in progress. ;)  I wish I could help with the USB thing, but I cannot replicate it on my system.  The auto-detection of both my USB printer and network printer worked as expected on my PanP5 with a fresh install of Karmic.  But that information is not particularly helpful to those experiencing problems.

---

### Post by ctsdownloads on 2009-11-04
> **zob said:**
> Sorry to say. I don't know where to go from here. Looks like a bug.
Might have something to do with apparmor protecting CUPS, but damn it's difficult.

If it was me and I was unable to get the printer working with 9.10, yet it works great in 9.04. then thinking "printer server" is where I would go.

Then again, I am tripping over my extra computers in my home office. All you really need is something running 9.04 or earlier, then share the printer. But that is just me. 

The beauty of a printer server is it removes the 9.10 USB problem pretty easily and as CUPS does have the driver for the printer, this might be the best solution available. ;)

---

### Post by zob on 2009-11-04
Well I wish I had one ctsdownloads.
For now I posted my version of the bug here [https://bugs.launchpad.net/ubuntu/karmic/+source/udev/+bug/420015?comments=all](https://bugs.launchpad.net/ubuntu/karmic/+source/udev/+bug/420015?comments=all), I hope anyone in the same situation will help solve this issue which looks strange to me.

---

### Post by thomasaaron on 2009-11-05
Try going to Software Sources, clicking the Updates tab and selecting backports.

Then check for updates on your system and run them. Then reboot.

Did that help?

If not, try booting from a live CD and trying your printer from there (9.10, that is). If that works better, you might consider doing a clean install (particularly if you did an online upgrade to start with).

---

### Post by zob on 2009-11-05
Well well. You're right thomasaaron. Running from the LiveCD I installed from actually makes it work instantly. My printer just shows up and is recognized as a HL-2140, which is correct. Now I guess that is kind of bad news, 'cause next is the fresh install.

For the moment I installed the proposed updates, I don't know about the backports. Not very stable are they?

---

### Post by zob on 2009-11-05
SOLVED.

Thanks thomasaaron. That LiveCD test led me on track. And now it's solved. To get a faster boot with a dual-core machine I made a change in /etc/init.d/rc where i changed concurrency=none to concurrency=shell.
Setting it back to concurrency=none solved this problem and another problem I had with Grub.
Thanks to everyone involved. And to the other guys who had the same problem. Did you do something like this? Then the solution is to set it back to default.
Maybe other "speed up your boot" tricks can have the same effect, so think... Did you do something to speed up your boot?

Now I'm a simple hijacker of this thread, hence I can't mark it as solved, but I hoped we solved the original posters problem too.

---

### Post by yahs on 2009-11-07
Just like to add my experience of Karmic installation and usb printing as I think it is relevant to the original posting.

I have now done 4 fresh installs of Karmic Desktop to different partitions and disks, ( Pentium Dual-core PC) all with the printer attached by usb.

Unlike Jaunty, Karmic does not recognise my Samsung scx4100 mfp straight away. If I select System, Admin, Printer then Karmic will recogonise the printer and offer the scx4200 as the driver using SpliX

This works for printing but not for scanning, so I download the unified driver from Samsung (ver 3.00.37).

When the Samsung GUI installer runs, you are offered the option of adding users to the group lp and _disabling parallel printing_.

The printer is configured to use /dev/mfp4 and a test page can be printed using CUPS v 1.1.x.

After the reboot, in the Samsung unified driver configurator and in System, Admin, Printers there are now 2 printers showing.

SCX-4100-Series on usb://Samsung/SCX-4100%20Series

scx4100(default) on mfp:/dev/mfp4

Both work but as I only need 1, I delete SCX-4100-Series.

In Jaunty the printer SCX-4100-Series on usb://Samsung/SCX-4100%20Series is found immediately after the installation finishes and although you can use the printer you cannot (or at least I can't) use the scanner unless you download and install the unified driver from Samsung.

With regards to some of the posts, I was wondering if the disabling of the parallel port is an issue that some users are experiencing.

Karmic works well for me and the printer and scanner work perfectly.

---

### Post by Trog on 2009-11-07
> **zob said:**
> 

Sadly lsusb still shows no trace of my printer.
```
lars@lars-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0499:1011 Yamaha Corp. P-250
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 002: ID 0bc2:3101 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```



Try using sudo lsusb. 
Incidentally, this is the first release where I haven't had to use the wrong driver to get my ip5200 working on USB.

---

### Post by fivenote on 2009-11-09
I can't get karmic to detect my canon bj-200 connected via usb.

This worked in jaunty, but not in karmic. I have both upgraded and freshly installed machines with the same results.

Unlike an earlier post that mentioned a solution, I did not edit  "concurrency" in /etc/init.d/rc. It is set to the default "concurrency=none".

Although the printer as not detected as under jaunty, I connected it and installed the driver using System->Admin->Printing and specifying the uri /dev/usb/lp0. However, when I print something, it goes to the queue and is stuck with the "Processing" status.

The printer does not show in "lsusb" and there are cups-related segfault messages in dmesg when I try to print. I found some launchpad bug reports from just before karmic released, but they seem to claim the problem is solved.

Any ideas or news on this issue?

---

### Post by thomasaaron on 2009-11-09
fivenote, which System76 model do you have?

---

### Post by ctsdownloads on 2009-11-09
> **fivenote said:**
> I can't get karmic to detect my canon bj-200 connected via usb.

This worked in jaunty, but not in karmic. I have both upgraded and freshly installed machines with the same results.

Unlike an earlier post that mentioned a solution, I did not edit  "concurrency" in /etc/init.d/rc. It is set to the default "concurrency=none".

Although the printer as not detected as under jaunty, I connected it and installed the driver using System->Admin->Printing and specifying the uri /dev/usb/lp0. However, when I print something, it goes to the queue and is stuck with the "Processing" status.

The printer does not show in "lsusb" and there are cups-related segfault messages in dmesg when I try to print. I found some launchpad bug reports from just before karmic released, but they seem to claim the problem is solved.

Any ideas or news on this issue?

Not saying this will help. I realize that even lsusb is showing nothing, but I found it might relate at some level as they do not mention looking into lshw or lsusb. [http://ubuntuforums.org/showthread.php?t=34583](http://ubuntuforums.org/showthread.php?t=34583)

So even though it is not being "seen" with lsusb, I'd take this old thread for a drive regardless. Half of the issues I solve are with totally unrelated, "wrong" ideas that just work sometimes. ;)

---

### Post by wgodoy80 on 2009-11-14
ISSUE: Printer not recognized when plugged in USB port, although drivers were correctly installed.  
Printer: BROTHER MFC-290c
System: Ubuntu 9.10 Karmic Koala , amd64

SOLVED:    first installed all Linux drivers (amd64) as recommended by Brother for printer and scanner ([http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html))  follow their steps carefully.  
Then: Disconnect printer from USB port and turn it off, restart your computer, log in and wait until everything loads, plug USB (make sure it's plugged correctly), turn on your printer after plugging USB, wait for system to recognize it automatically.....  printer and scanner work!!!  

'lsusb' output: 
wxxxx@my-laptop:~$ lsusb
Bus 003 Device 003: ID 04f9:01fd Brother Industries, Ltd 
Bus 003 Device 002: ID 04d9:048e Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

make sure you have all drivers installed typing:  ' dpkg -l | grep (make) '

wxxxxx@my-laptop:~$ dpkg -l | grep Brother
ii  brother-cups-wrapper-common                1.0.0-10-0ubuntu5                          Common files for Brother cups wrapper packag
ii  brscan-skey                                0.2.1-3                                    Brother Linux scanner S-KEY tool
ii  brscan3                                    0.2.7-1                                    Brother Scanner Driver
ii  mfc290ccupswrapper                         1.1.2-2                                    Brother CUPS Inkjet Printer Definitions
ii  mfc290clpr                                 1.1.2-2                                    Brother lpr Inkjet Printer Definitions

Hope it helps!

---

### Post by arepaking on 2010-03-13
Hi Everyone,
I still having issue when it comes to print to my Samsumg ML-6060 printer.

This is what I have by running lsusb:

[HTML]Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04a9:2225 Canon, Inc. CanoScan LiDE 70
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hu[/HTML]


And this is what I get when running: sudo lsusb
[HTML]Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04a9:2225 Canon, Inc. CanoScan LiDE 70
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 04e8:3008 Samsung Electronics Co., Ltd ML-6060 laser printer[/HTML]

As you can see, by using SUDO I can see that my printer is detected... any ideas???

---

