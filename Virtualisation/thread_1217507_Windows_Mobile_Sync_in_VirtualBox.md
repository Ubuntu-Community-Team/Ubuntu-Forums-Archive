---
title: "Windows Mobile Sync in VirtualBox"
date: 2009-07-19
forum: Virtualisation
---

### Post by MaindotC on 2009-07-19
I installed Vista Ultimate in Virtualbox.  My [HTC S710](http://www.htc.com/www/Product.aspx?id=568) came with driver software that I loaded into VirtualBox and it seemed to install properly.  However, I have received two different errors in two different installations.  The first time, after downloading all updates and rebooting a few times, and installing the driver software, it said "This Device Cannot Start (Code 10)".  I hadn't even connected my HTC at the time.  I connected it, enabled it in the usb settings of VBox and Windows Mobile Centre would not connect to the device.  I tried things like powering it on and off.

I installed Vista a second time and this time I downloaded updates, rebooted, and installed the driver software.  This time, near the end of the installation it said "Could not load driver software" and here is the output from the error reporting:
> 
Description
Windows was able to successfully install device driver software, but the driver software encountered a problem when it tried to run. The problem code is 10.

Problem signature
Problem Event Name:	PnPDeviceProblemCode
Architecture:	x86
Hardware Id:	USB\VID_0BB4&PID_0B51&REV_0000
Setup class GUID:	{4d36e972-e325-11ce-bfc1-08002be10318}
PnP problem code:	0000000A
Driver name:	usb8023x.sys
Driver version:	6.0.6001.18000
Driver date:	01-21-2008
OS Version:	6.0.6001.2.1.0.256.1
Locale ID:	1033

Extra information about the problem
Bucket ID:	188684911


If you check my signature, I have a mobo that's like 5 years old so I was wondering if perhaps my usb controller could be an issue.  I performed a non-virtualized installation of Vista on my laptop (Lenovo T60) and it worked fine - synched all my files and I loaded podcasts from Audible onto my phone.

---

### Post by 0bso on 2009-07-20
If you haven't tried it, uncheck "USB advanced network" (or uncheck "enable faster data connection" in WM6.5) in the usb settings menu on the phone. Then restart the phone and your vm and try again.

That's what I had to do to get activesync on a XP VM to connect to my HTC 8925. Not exactly the same setup as yours but worth trying.

---

### Post by Bonzai11 on 2009-07-20
I got windows mobile sync to work with windows 7 and vista in vmware, but I have no experience with virtualbox.

---

### Post by MaindotC on 2009-09-11
The problem was that I had to disable the rndis_host driver in the host o/s b/c it was interfering w/ VBox trying to use it.  Once I blacklisted the driver, then modprobe'd and re-inserted the HTC it worked perfectly.  Synched all my files and podcasts.

---

### Post by luis.nando on 2009-12-29
I don't know if this can help you, but you can sync your WM6.1 with ubuntu using SynCE. It works properly with my Motorola Q11, and I can say that it was easy to configure.

---

