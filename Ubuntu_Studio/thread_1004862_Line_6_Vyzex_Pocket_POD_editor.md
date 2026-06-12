---
title: "Line 6 Vyzex Pocket POD editor"
date: 2008-12-07
forum: Ubuntu Studio
---

### Post by kemra on 2008-12-07
Hi Guys, this is my first post after a while of hanging out here ):P

I recently switched to Linux from Windows (as well do at some point) and have been getting things steadily up and running.

I am having problems running the Vyzex software used to interact with the Line6 Pocket POD. Or it would be more correct to say that when the Vyzex editor is loading it cannot detect the Pocket POD even though it is connected via USB.

I have tried selecting different midi ports within Vyzex but it still cannot find the POD. Now I have tried following the instructions found here: [http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/) but due to my newness to Linux I'm not sure I have followed it correctly as it has made no discernible difference to my situation. 

If anyone has any ideas I'd be very grateful, thanks in advance!

---

### Post by AutoStatic on 2009-01-11
Hello kemra,

Start winecfg (Wine Config) and select the tab Audio. Make sure ALSA is ticked and that your Line6 device appears under MIDI IN Devices and MIDI OUT Devices. If so, you can start the Vyzex Pocket Pod editor and you're good to go.

---

### Post by Jeztastic on 2009-05-30
This works great for me, thanks!

---

### Post by abit2thewhat on 2009-06-10
:guitar:[SIZE=5]Hey thank you for the great info.I guess the software is in the pod itself,but now they have and extra dvd that is in the extra pack.Love to justbe able to get that but don't need the whole pack.peace, Dennis[/SIZE]

---

### Post by coverup on 2009-07-23
Hey, I'd like to revive this thread because at some point my Pocket POD has stopped working under Linux... I had it working with Intrepid 64-bit, but something has changed in between then and now (Jaunty 64).  It's not a wine issue, but rather a plain ol' USB issue.  Here's my dmesg output when I plug it in:

[ 6707.712059] usb 2-4: device descriptor read/64, error -62
[ 6708.001031] usb 2-4: device descriptor read/64, error -62
[ 6708.280025] usb 2-4: new full speed USB device using ohci_hcd and address 9
[ 6708.460101] usb 2-4: device descriptor read/64, error -62
[ 6708.748216] usb 2-4: device descriptor read/64, error -62
[ 6709.029523] usb 2-4: new full speed USB device using ohci_hcd and address 10
[ 6709.436014] usb 2-4: device not accepting address 10, error -62
[ 6709.597517] usb 2-4: new full speed USB device using ohci_hcd and address 11
[ 6710.005516] usb 2-4: device not accepting address 11, error -62
[ 6710.005533] hub 2-0:1.0: unable to enumerate USB device on port 4

It doesn't work on 32-bit either, which is my Ubuntu Studio install.  Where do you start troubleshooting stuff like this?  I've tried it on various ports, other USB midi devices work super-well.

Is anyone still able to use theirs with Linux?  I'm going to stop by a friend's house with a Windows machine and give it a shot there to make sure it's not defective hardware on the POD's end, but I'd really appreciate any tips or hints on where to go from here.  The thing's almost useless for recording if you can't customize the settings.

---

### Post by coverup on 2009-07-23
Another way to phrase this question - some people have had success in the past troubleshooting this with removing the ehci-hcd module via

rmmod ehci-hcd

or

modprobe -r ehci-hcd

But now I notice that these modules don't exist anymore in Ubuntu... what kernel module is coming in and managing this stuff now if ehci isn't??

---

### Post by sgx on 2009-07-23
> **coverup said:**
> Another way to phrase this question - some people have had success in the past troubleshooting this with removing the ehci-hcd module via

rmmod ehci-hcd

or

modprobe -r ehci-hcd

But now I notice that these modules don't exist anymore in Ubuntu... what kernel module is coming in and managing this stuff now if ehci isn't??

You might try google: exact phrase:

instead of ehci

and go from there. Cheers

---

