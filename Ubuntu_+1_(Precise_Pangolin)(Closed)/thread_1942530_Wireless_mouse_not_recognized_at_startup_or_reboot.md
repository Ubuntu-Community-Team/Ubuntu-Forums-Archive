---
title: "Wireless mouse not recognized at startup or reboot..."
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-03-17
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/958174](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/958174)

Me and my bugs. I've confirmed it. Whenever I boot up or restart Unity, I have to unplug my USB mouse, then plug it back in before it's recognized. My mouse: Logitech, Anywhere MX.

If anyone else has been affected by this bug, be sure to go to launchpad and add yourself to the list.

---

### Post by lucazade on 2012-03-17
I get the same issue since oneiric with a Logitech Performance MX mouse.
So to me this is an old issue, still not solved..

---

### Post by neu5eeCh on 2012-03-17
> **lucazade said:**
> I get the same issue since oneiric with a Logitech Performance MX mouse.
So to me this is an old issue, still not solved..

Never had this issue with oneiric (Xubuntu or Unity) or any other distro for that matter?

---

### Post by lucazade on 2012-03-17
> **VTPoet said:**
> Never had this issue with oneiric (Xubuntu or Unity) or any other distro for that matter?

lucky you, you get this only with latest kernel in precise.. for me is an old issue.
have you tried to look into "dmesg" when mouse is not responding? There will probably be some errors logged.
With another logitech mouse I own this issue is anyway not reproducible.

---

### Post by neu5eeCh on 2012-03-17
> **lucazade said:**
> lucky you, you get this only with latest kernel in precise..

Yeah... OK, but no. **For the record:** My point is that everything was fine until yesterday's update. It's not clear that the kernel is at fault. 

But anyway, I'll live. The workaround is easy.

---

### Post by neu5eeCh on 2012-03-20
Here's a new twist, and I'd be interested in seeing if anyone else can reproduce this.

I notice that I lose my wireless mouse connection when I use the "Scale" feature provided by Ubuntu Tweak/Compiz. In other words, I've assigned Scale to the top left corner. As soon as I mouse to the corner and the windows scale, I lose my wireless mouse. I've added this to my initial bug report:

[https://bugs.launchpad.net/ubuntu/+bug/958174](https://bugs.launchpad.net/ubuntu/+bug/958174)

---

### Post by SemiExpert on 2012-04-12
There seems to be a definite bug here, effecting both varieties of the Darkfield technology Logitech mouse - Performance MX and Anywhere MX.  It's a shame, as other Logitech models work just fine, including models with the nano receiver. Weird. The Anywhere MX works fairly well with Ubuntu 12.04 as far as button functionality, but isn't always recognized after a reboot.  The fault is intermittant, so it's recognized after booting up about half the time.   The odd thing is that Log Out, Lock Screen, Suspend and even a Restart won't neccessarily allow the mouse to be recognized.  You have to pull and replace the USB nano receiver.

---

### Post by jadtech on 2012-04-12
i had no trouble with my wireless mouse working the other day whenI install 12.04 beta nothing else worked but the mouse was fully fuctional and I am fairly sure if  it had booted with and menus  or gui's of any kind other then then back ground  I could have clicked on it if there was  some way to get to  restart I am sure it would have worked as well keyboard on the other hand no way nothing on that workd after the point of the password ..

---

### Post by jadtech on 2012-04-12
i guess linux really is a cooperative effort if someone of you type in commands for me I will do the clicking .

---

### Post by treesurf on 2012-04-12
> **SemiExpert said:**
> There seems to be a definite bug here, effecting both varieties of the Darkfield technology Logitech mouse - Performance MX and Anywhere MX.  It's a shame, as other Logitech models work just fine, including models with the nano receiver. Weird. The Anywhere MX works fairly well with Ubuntu 12.04 as far as button functionality, but isn't always recognized after a reboot.  The fault is intermittant, so it's recognized after booting up about half the time.   The odd thing is that Log Out, Lock Screen, Suspend and even a Restart won't neccessarily allow the mouse to be recognized.  You have to pull and replace the USB nano receiver.

I agree this sounds like a problem with the Darkfield tech.  My wireless Logitech mouse that doesn't have the Darkfield tech works just fine.

---

### Post by lucazade on 2012-04-13
> **treesurf said:**
> I agree this sounds like a problem with the Darkfield tech.  My wireless Logitech mouse that doesn't have the Darkfield tech works just fine.

exactly.. confirmed bug again.

---

### Post by neu5eeCh on 2012-04-13
I called up logitech and they're replacing my Anywhere mouse. I never had problems with it until I used it on Ubuntu 12.04.

Even though I think I know the answer, I'm going to ask anyway: Is it at all possible that "Ubuntu" could have _fried_ the transmitter?

---

### Post by NHclimber on 2012-04-13
> **VTPoet said:**
> Even though I think I know the answer, I'm going to ask anyway: Is it at all possible that "Ubuntu" could have _fried_ the transmitter?

Yep.  Last year, I nuked a BT dongle while working on BT authentication for legacy devices -- which also fried the attached HID keyboard :(

---

### Post by neu5eeCh on 2012-04-13
> **NHclimber said:**
> Yep.  Last year, I nuked a BT dongle while working on BT authentication for legacy devices -- which also fried the attached HID keyboard :(

So is it possible that "Ubuntu" (or the Kernel) is frying all these mice using the Darkfield technology? I find it curious that others are having this problem, but worse that the mice also suddenly don't work on OS or MAC? Is there a correlation?

---

### Post by cariboo on 2012-04-13
Does the mouse show up in dmesg? I don't have a Logitech mouse, but when I use the following command:

```
dmesg | grep Microsoft
```

I get the following output:

> cariboo@alexis:~$ dmesg | grep Microsoft
[    1.533834] input: Microsoft Microsoft Wireless Optical Mouse\xffffffc2\xffffffae\xffffffae 1.0A as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input2

---

### Post by NHclimber on 2012-04-13
> **VTPoet said:**
> So is it possible that "Ubuntu" (or the Kernel) is frying all these mice using the Darkfield technology? I find it curious that others are having this problem, but worse that the mice also suddenly don't work on OS or MAC? Is there a correlation?

"Frying" is not very likely -- More likely is that the mouse has been unpaired from the unifying receiver. I know it's a drag but you should see if you can pair the mouse+receiver in Windows (as far as I'm aware Logitech hasn't ported that app to linux although there's a link to a user-contributed pairing tool here *which I've never used* _[http://forums.logitech.com/t5/Mice-and-Pointing-Devices/Linux-Unifying-Support/td-p/548124](http://forums.logitech.com/t5/Mice-and-Pointing-Devices/Linux-Unifying-Support/td-p/548124)_).

BTW, the driver for the logitech unifying receiver (hid_logitech_dj) was contributed by Logitech.

---

### Post by NHclimber on 2012-04-13
BTW, you guys with logitech unifying receiver wireless keyboards:  I'd appreciate if you could waste a bunch of your time ;) and try to install from the alternate iso. It will appear to hang after 'Install Ubuntu' but in actuality only the keyboard is unresponsive *because the logitech hid driver is not included in the kernel modules* -- hahaha...

When you do repro that, would you please 'me too' this bug [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/975198](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/975198) ?  Also wouldn't hurt to report the iso failure:
amd64 here [http://iso.qa.ubuntu.com/qatracker/milestones/204/builds/15293/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/204/builds/15293/testcases)
i386 here [http://iso.qa.ubuntu.com/qatracker/milestones/204/builds/15295/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/204/builds/15295/testcases)

---

### Post by neu5eeCh on 2012-04-13
> **NHclimber said:**
> "Frying" is not very likely -- More likely is that the mouse has been unpaired from the unifying receiver. I know it's a drag but you should see if you can pair the mouse+receiver in Windows .

Thanks, I tried that with a tech support technician at Logitech. The "pairing" software didn't work which led the tech to conclude that either the transmitter was bad or the receiver (in either unit).

Logitech is sending me a new mouse, as we speak. If the latest Ubuntu/Linux was somehow to blame, I don't want to fry 49 dollars worth of mouse. If the same mouse stops working for other users on 12.04 _**and**_ Windows, then I'm really going to start worrying. So far, though, that doesn't appear to be  the case. Evidence points to the problem being isolated to my mouse.

---

### Post by SemiExpert on 2012-04-13
When I let GNU Grub time out, the mouse isn't recognized, but when I choose from the list or simply just hit ENTER, the mouse is recognized?  I've gone through eight reboots, and 3 out of the 4 times I let Grub time out, the mouse wasn't recognized, all 4 times I selected the highlighted entry, the mouse was recognized, and the only thing that ruins the theory was the one time when the mouse was recognized after Grub timesout.  Could this issue stem from GNU Grub?  Coincidence?  I'll start a running tally of reboots to see if there is a correlation.

---

### Post by misterblobby on 2012-04-14
I have a Logitech M305 wireless mouse, but have never had a problem. I'm currently using 12.04 with all updates installed.

The touchpad used to drop out quite regularly ion 11.10, but never the mouse.

What does all that mean? I don't know, but someone might.

---

### Post by SemiExpert on 2012-04-14
> **misterblobby said:**
> I have a Logitech M305 wireless mouse, but have never had a problem. I'm currently using 12.04 with all updates installed.

The touchpad used to drop out quite regularly ion 11.10, but never the mouse.

What does all that mean? I don't know, but someone might.

 The issue in question only appears to apply to Logitech Darkfield technology mice - the Anywhere MX and Performance MX.  Having continued my experiment with Grub, I haven't had a single instance where the mouse wasn't recognized as long as I didn't let Grub time out.

---

### Post by lucazade on 2012-04-14
> **SemiExpert said:**
> The issue in question only appears to apply to Logitech Darkfield technology mice - the Anywhere MX and Performance MX.  Having continued my experiment with Grub, I haven't had a single instance where the mouse wasn't recognized as long as I didn't let Grub time out.

I have a hidden grub, without time out, and at every reboot mouse is not recognized.
I've to unplug and plug again the MX recevicer.

when it doesn't work there is only a entry in dmesg about the logitech mouse:

```
[   18.968583] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2/input2

```
instead removing and inserting again I get two entries:

```
[  106.130243] logitech-djreceiver 0003:046D:C52B.0006: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2/input2
[  106.139727] logitech-djdevice 0003:046D:C52B.0007: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:1d.0-2:1
```

---

### Post by NHclimber on 2012-04-14
> **SemiExpert said:**
> .... Having continued my experiment with Grub, I haven't had a single instance where the mouse wasn't recognized as long as I didn't let Grub time out.

@SemiExpert,
Does your keyboard use the same wireless receiver (is your keyboard even wireless)?  I could see early HID traffic prior to kernel load putting the receiver into a known state and that having an impact on whether the mouse is probed properly.  Does keyboard activity prior to grub have the same effect?

@Lucazade,
Is your mouse ever recognized at boot? If you do use the keyboard prior to kernel load, is the mouse recognized?

Can someone put 'sudo lsusb -v output' for both working and non-working conditions? Don't paste, just attach.

---

### Post by neu5eeCh on 2012-04-14
You folks should be copying some of these posts to the bug report. From what I can tell (so far) the devs at Ubuntu could give a rat's butt about this problem; but they might take it a little more seriously if information like this narrows down the cause (and is shown to be a more widespread problem than it currently appears at the bug report).

---

### Post by lucazade on 2012-04-15
@NHclimber

lsusb output attached.
I'll post them also in the bug report... btw the mouse is recognized at boot rarely, I usually have to plug the receiver again.

---

### Post by NHclimber on 2012-04-16
[I]**Please don't do this unless you're 100% comfortable messing with your boot parameters and know how to repair a broken ram image from an alternate boot.**
[/I]
It might help to see kernel logs with debug HID output to narrow down the problem. This will turn on debug output for the hid subsystem.
```
echo "options hid debug=1" | sudo tee /etc/modprobe.d/hid.conf
sudo update-initramfs -u
```Then reboot.

Please note that HID reports will output to the syslog and this could flood your logs if left on.  After rebooting, turn off the debug HID output with:
```
echo "0" | sudo tee /sys/module/hid/parameters/debug

```Use these to reset back to how it was (debug HID output disabled) upon the next reboot:
```
sudo rm /etc/modprobe.d/hid.conf
sudo update-initramfs -u

```Then attach or paste** *ONLY***  the fragment of syslog that begins
```
/build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: Logitech-DJ:logi_dj_init
```A working probe of devices paired to the receiver looks like this (for keyboard and mouse)
```
Apr 16 12:17:51 thor kernel: [   18.383757] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: Logitech-DJ:logi_dj_init
Apr 16 12:17:51 thor kernel: [   18.383772] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_probe called for ifnum 0
Apr 16 12:17:51 thor kernel: [   18.383774] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_probe: ignoring ifnum 0
Apr 16 12:17:51 thor kernel: [   18.383784] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_probe called for ifnum 1
Apr 16 12:17:51 thor kernel: [   18.383786] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_probe: ignoring ifnum 1
Apr 16 12:17:51 thor kernel: [   18.383793] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_probe called for ifnum 2
Apr 16 12:17:51 thor kernel: [   18.386301] /build/buildd/linux-3.2.0/drivers/hid/usbhid/hid-core.c: submitting ctrl urb: Get_Report wValue=0x0110 wIndex=0x0002 wLength=7
Apr 16 12:17:51 thor kernel: [   18.386983] /build/buildd/linux-3.2.0/drivers/hid/usbhid/hid-core.c: submitting ctrl urb: Get_Report wValue=0x0111 wIndex=0x0002 wLength=20
Apr 16 12:17:51 thor kernel: [   18.387980] /build/buildd/linux-3.2.0/drivers/hid/usbhid/hid-core.c: submitting ctrl urb: Get_Report wValue=0x0120 wIndex=0x0002 wLength=15
Apr 16 12:17:51 thor kernel: [   18.388983] /build/buildd/linux-3.2.0/drivers/hid/usbhid/hid-core.c: submitting ctrl urb: Get_Report wValue=0x0121 wIndex=0x0002 wLength=32
Apr 16 12:17:51 thor kernel: [   18.390191] logitech-djreceiver 0003:046D:C52B.0004: hiddev0,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-2/input2
Apr 16 12:17:51 thor kernel: [   18.392987] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_raw_event, size:15
Apr 16 12:17:51 thor kernel: [   18.393056] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: delayedwork_callback
Apr 16 12:17:51 thor kernel: [   18.393150] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_ll_parse
Apr 16 12:17:51 thor kernel: [   18.393152] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_ll_parse: sending a kbd descriptor, reports_supported: 1a
Apr 16 12:17:51 thor kernel: [   18.393321] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_ll_parse: sending a multimedia report descriptor: 1a
Apr 16 12:17:51 thor kernel: [   18.393400] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_ll_parse: sending a power keys report descriptor: 1a
Apr 16 12:17:51 thor kernel: [   18.393488] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_ll_start
Apr 16 12:17:51 thor kernel: [   18.393643] input: Logitech Unifying Device. Wireless PID:2010 as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.2/0003:046D:C52B.0004/input/input4
Apr 16 12:17:51 thor kernel: [   18.393651] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_ll_open:usb-0000:00:1d.2-2:1
Apr 16 12:17:51 thor kernel: [   18.393792] logitech-djdevice 0003:046D:C52B.0007: input,hidraw4: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:2010] on usb-0000:00:1d.2-2:1
Apr 16 12:17:51 thor kernel: [   18.394983] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_raw_event, size:15
Apr 16 12:17:51 thor kernel: [   18.395000] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: delayedwork_callback
Apr 16 12:17:51 thor kernel: [   18.395066] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_ll_parse
Apr 16 12:17:51 thor kernel: [   18.395069] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_ll_parse: sending a mouse descriptor, reports_supported: 4
Apr 16 12:17:51 thor kernel: [   18.395243] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_ll_start
Apr 16 12:17:51 thor kernel: [   18.395311] input: Logitech Unifying Device. Wireless PID:101b as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.2/0003:046D:C52B.0004/input/input5
Apr 16 12:17:51 thor kernel: [   18.395445] logitech-djdevice 0003:046D:C52B.0008: input,hidraw5: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101b] on usb-0000:00:1d.2-2:2
Apr 16 12:17:51 thor kernel: [   18.396987] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_raw_event, size:15
Apr 16 12:17:51 thor kernel: [   18.397007] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: delayedwork_callback
Apr 16 12:17:51 thor kernel: [   18.397011] /build/buildd/linux-3.2.0/drivers/hid/hid-logitech-dj.c: logi_dj_recv_add_djhid_device: device list is empty

```

---

### Post by SemiExpert on 2012-04-25
The saga continues and periodically my mouse isn't recognized even if I have selected manually from the Grub menu.  I've even had to unplug and replug twice in one instance.  I'm wondering if this is really a Grub issue, a generic Kernel issue or an Ubuntu 12.04 specific issue?

---

