---
title: "panp4i usb issues"
date: 2008-12-17
forum: System76 Support
---

### Post by adingo on 2008-12-17
I have a panp4i running Intrepid.  Earlier this week the mouse I had plugged into the usb drive stopped working.  I assumed the mouse was bad as it didn't work in any ports.  I've now tried another mouse, which also won't register.  My ipod will be recognized (and mounted) about half the time.  A flash drive will always be recognized (and mounted).  All the devices show power if they work or not (light on the optical mouse, charge icon on the ipod, etc).  I restarted on a 8.10 live cd in case an update last week had done something, but I get the same results there.

I've checked for devices using lsusb, and if they're not working the won't be mentioned there.  dmsg gives me things like:
[  837.653090] hub 8-0:1.0: unable to enumerate USB device on port 2
[  839.608088] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[  841.528285] hub 8-0:1.0: connect-debounce failed, port 2 disabled
 or less often
[  935.614445] usb 5-2: new low speed USB device using uhci_hcd and address 3
[  935.736050] usb 5-2: device descriptor read/64, error -71
[  935.964069] usb 5-2: device descriptor read/64, error -71
[  936.124110] hub 5-0:1.0: unable to enumerate USB device on port 2

Any help?

-Eddie

---

### Post by thomasaaron on 2008-12-18
Well, that's a tad confusing. If you can reliably replicate the problem from a live CD, that would pretty much confirm a hardware problem.

However, some devices being recognized all the time, others being recognized occasionally, and yet others not being recognized at all, doesn't make a lot of sense.

This guy had a similar problem a while back, and it turned out to be a kernel bug...
[http://ubuntuforums.org/archive/index.php/t-257512.html](http://ubuntuforums.org/archive/index.php/t-257512.html)

You might want to try his work-around and see if it works. If it does, it's probably a bug. If not, your hardware might be failing.

Also, how many USB devices do you have plugged in at once? And what are they? It could be that you're overwhelming the system somehow. Do a fresh reboot with no USB devices plugged in and then test them one at a time in each port.

---

### Post by adingo on 2008-12-18
The bug fix didn't help any.  (I didn't think it would, this hardware was all working w/ 8.10 up until the weekend.  And there's no change w/ the live CD from when intrepid was issued a couple months back, which also worked before).

I have tried restarting before, I redid everything and tried to take some notes as I went.  Looking at the top of the laptop I will call the port on the left to the back LB, left to the front LF, and on the right R

Plugged in my ipod nano to LB.  identified and mounted.  then LF did the same.  lsusb shows ipod.  dmesg gives:

[  894.109205] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[  894.109731] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  894.868268] hub 8-0:1.0: connect-debounce failed, port 3 disabled

Plugging ipod into R gives no id on lsusb and no mount.  (Ipod does power up to show it's charging).  dmesg:

[ 1197.012079] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[ 1198.936152] hub 8-0:1.0: connect-debounce failed, port 2 disabled

Moving to imation 1 gb usb flash drive.  LB mounts and IDs on lsusb.  dmesg:

[ 1270.403251]  sdb: sdb1
[ 1270.404386] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 1270.404593] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 1270.420062] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[ 1272.342214] hub 8-0:1.0: connect-debounce failed, port 2 disabled

If i move to LF it mounts correctly.  dmesg:

[ 1355.455345]  sdb: sdb1
[ 1355.456707] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 1355.457267] sd 11:0:0:0: Attached scsi generic sg2 type 0
[ 1356.628224] hub 8-0:1.0: connect-debounce failed, port 3 disabled

Moving it to R i get no mount indication, nothing on lsusb, dmesg:

[ 1429.037830] usb 8-2: USB disconnect, address 11
[ 1430.960287] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[ 1432.881124] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[ 1434.800150] hub 8-0:1.0: connect-debounce failed, port 1 disabled

I unmounted both the ipod and the usb drive between moving them, btw.

Moving onto a dell optical mouse in LB.  The light in the bottom comes on, but the mouse doesn't move cursor.  Nothing on lsusb.  dmesg:

[ 1576.424155] usb 5-1: new low speed USB device using uhci_hcd and address 27
[ 1576.544214] usb 5-1: device descriptor read/64, error -71
[ 1576.768209] usb 5-1: device descriptor read/64, error -71
[ 1576.984144] usb 5-1: new low speed USB device using uhci_hcd and address 28
[ 1577.105082] usb 5-1: device descriptor read/64, error -71
[ 1577.328276] usb 5-1: device descriptor read/64, error -71
[ 1577.544098] usb 5-1: new low speed USB device using uhci_hcd and address 29
[ 1577.956140] usb 5-1: device not accepting address 29, error -71
[ 1578.068280] usb 5-1: new low speed USB device using uhci_hcd and address 30
[ 1578.484067] usb 5-1: device not accepting address 30, error -71
[ 1578.484111] hub 5-0:1.0: unable to enumerate USB device on port 1
[ 1580.408095] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[ 1582.328137] hub 8-0:1.0: connect-debounce failed, port 3 disabled

Moving LF

[ 1666.395808] usb 5-1: new low speed USB device using uhci_hcd and address 37
[ 1666.809249] usb 5-1: device not accepting address 37, error -71
[ 1666.864311] hub 5-0:1.0: unable to enumerate USB device on port 1
[ 1668.785275] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[ 1670.704275] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[ 1670.944270] usb 5-1: new low speed USB device using uhci_hcd and address 39
[ 1671.064287] usb 5-1: device descriptor read/64, error -71
[ 1671.288154] usb 5-1: device descriptor read/64, error -71
[ 1672.172274] usb 5-1: new low speed USB device using uhci_hcd and address 40
[ 1672.964270] usb 5-1: device descriptor read/64, error -71
[ 1673.188271] usb 5-1: device descriptor read/64, error -71
[ 1673.404282] usb 5-1: new low speed USB device using uhci_hcd and address 41
[ 1673.820265] usb 5-1: device not accepting address 41, error -71
[ 1676.436267] usb 5-1: new low speed USB device using uhci_hcd and address 42
[ 1676.848256] usb 5-1: device not accepting address 42, error -71
[ 1676.848763] hub 5-0:1.0: unable to enumerate USB device on port 1
[ 1678.773166] hub 8-0:1.0: connect-debounce failed, port 2 disabled
[ 1680.692111] hub 8-0:1.0: connect-debounce failed, port 3 disabled

and R

[ 1732.792313] hub 5-0:1.0: unable to enumerate USB device on port 2
[ 1734.712275] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[ 1734.896095] hub 5-0:1.0: unable to enumerate USB device on port 2
[ 1736.816312] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[ 1737.056280] usb 5-2: new low speed USB device using uhci_hcd and address 62
[ 1737.176312] usb 5-2: device descriptor read/64, error -71
[ 1737.400187] usb 5-2: device descriptor read/64, error -71
[ 1737.616292] usb 5-2: new low speed USB device using uhci_hcd and address 63
[ 1737.736281] usb 5-2: device descriptor read/64, error -71
[ 1737.904313] hub 5-0:1.0: unable to enumerate USB device on port 2
[ 1739.824137] hub 8-0:1.0: connect-debounce failed, port 3 disabled
[ 1741.872305] hub 8-0:1.0: connect-debounce failed, port 2 disabled

I tried a different usb mouse  yesterday and got the same sort of results.

Anything else I should try?

---

### Post by adingo on 2008-12-18
so for the heck of it i booted into an older kernel from grub...  and the mouse works here

 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux

that doesn't make sense to me since it wasn't working for the intrepid live cd.  i know for a fact that kernel used to work.  how can it not now?  but the hardy kernel does???

---

### Post by adingo on 2008-12-18
and now it's working in the current intrepid kernel (2.6.27-9-generic) without me changing anything.  so it's official, i'm completely confused.

---

### Post by djhyland on 2008-12-18
> **thomasaaron said:**
> Well, that's a tad confusing. If you can reliably replicate the problem from a live CD, that would pretty much confirm a hardware problem.

I'm pretty sure that it's a hardware problem.  I have the same model of computer, and I'm getting similar error messages.  I have four operating systems installed on my Pangolin, and I've had USB problems on all of them.  I first got the "connect-debounce" messages with Ubuntu 8.10 running a 2.6.27 kernel a week or so ago, and I also get them running Fedora 10 running a 2.6.27 kernel the same night.  I then tried Gentoo running a 2.6.25 kernel, and that worked fine.  At the end of the night, I turned off my computer, and everything worked normally when I restarted it in the morning.

I was hoping that this problem was just a fluke, but it came back today, and this time while running my Gentoo 2.6.25 install.  Ubuntu and Fedora with the 2.6.27 kernel had the same problems.  Out of curiousity, I booted into OpenSolaris 2008.11, and while I didn't get the "connect-debounce" error messages, my USB devices didn't work under that, either.  I shut my computer down and left it off for a while, and everything works again after turning it back on (at least under Fedora, I haven't tried the other OSes yet, but I assume they'd work as well).

Anyway, hopefully this will help diagnose the problem.  Thanks!

---

### Post by thomasaaron on 2008-12-19
If you guys will shoot me an email, I'll send you instructions for resetting the CMOS. That might clear it up.

---

