---
title: "Video capture via USB?"
date: 2008-07-03
forum: Ubuntu Studio
---

### Post by daxdog on 2008-07-03
I've got an Honestech My Vidbox video capture device.  It came with some Windows software called "VHS to DVD Deluxe".  Is there Linux software to support it?  I tried loading dvgrab and it did not recognize the video input device.

The bottom of the device reads "Trade Name: VIDBOX" and "Model Number: HT VIDBOX NW02".

Any help would be appreciated.

---

### Post by Creative2 on 2008-07-04
NB I DON'T KNOW if you camera is compatible with raw1394 module but generally, this is for firewire but it should work even with usb devices :

lsmod | grep 1394 

if raw1394 is not present you have to load it. 

[here]("http://fuocotools.byethost13.com/index.php?topic=103.0") there is a translation of this italian wiki

[http://wiki.ubuntu-it.org/Hardware/Video/TelecameraDv?highlight=(telecamera](http://wiki.ubuntu-it.org/Hardware/Video/TelecameraDv?highlight=(telecamera))

---

### Post by flipg40 on 2008-12-19
Has anyone got "my vidbox" working in Intrepid? Kino is not seeing it I followed a how to located [here]("http://fuocotools.byethost13.com/index.php?topic=103.0").

Kino does not error out so I am afraid that ubuntu is not seeing the hardware. Any help would be awesome!

---

### Post by kayosiii on 2008-12-23
Kino doesn't really work with anything other than minidv firewire cameras last time I checked.

If your device is supported it will be because it has a video4linux driver so I would suggest searching the interweb for video4linux and your device name.

---

### Post by IcKY99 on 2009-01-05
> **daxdog said:**
> I've got an Honestech My Vidbox video capture device.  It came with some Windows software called "VHS to DVD Deluxe".  Is there Linux software to support it?  I tried loading dvgrab and it did not recognize the video input device.

The bottom of the device reads "Trade Name: VIDBOX" and "Model Number: HT VIDBOX NW02".

Any help would be appreciated.

same problem, still no help? is there any alternatives that support the honestech capture box?

---

### Post by flipg40 on 2009-11-13
This is the only thing tying me to a windows environment. Can anyone give me any guidance on resolving this issue?

---

### Post by spegru on 2009-11-13
not exactly but I am looking into it right now!

By the way if you have one of these USB things, what happens if you type lsusb into a terminal?
It should giv a list of your USB devices so what dies it give for the the video thing?

---

### Post by flipg40 on 2009-11-13
It gives this:

Bus 001 Device 023: ID eb1a:5006 eMPIA Technology, Inc.

I've unplugged the device and the above goes away. So this has to be it. I've been looking into it but can't seem to find anything that is helpful.

Thanks!

---

### Post by spegru on 2009-11-13
Certainly must be the one then.
I found this article see if it helps.......
[http://www.starcube.co.uk/2009/10/ubuntu-howto-capture-from-the-dazzle/](http://www.starcube.co.uk/2009/10/ubuntu-howto-capture-from-the-dazzle/)

I've not got one of these so I cant test.
I did try to install wxcam but the link seems broken and it's not in the repo
However even if it doesnt work for you, you could try VLC, or Kaffiene, or Cheese or various others.
The trick will be to see if you can get the system to recognise the dazzle as a video input device like a camera

---

### Post by flipg40 on 2009-11-13
Thank you... the only thing is this is not a Dazzle. It is a Honestech My VID Box (HT VIDBOX NW03).

I'll try the Dazzle info... thanks again.

---

### Post by spegru on 2009-11-13
well I hope the principle is the same
Let us know how you get on.........

---

### Post by shadetree1 on 2010-03-08
> **flipg40 said:**
> Thank you... the only thing is this is not a Dazzle. It is a Honestech My VID Box (HT VIDBOX NW03).

I'll try the Dazzle info... thanks again.

Just wondering if you or anyone figured this out?

I have a USB ADS VideoXpress.

---

### Post by wkulecz on 2010-03-09
Check out the MythTV project supported hardware, if it doesn't work there your odds are slim of it being usable in Linux without specific manufacturer support.  As far as I can tell, Hauppauge is about the only maker with even lip service support for Linux for some of their devices.

--wally.

---

### Post by shadetree1 on 2010-03-09
> **wkulecz said:**
> Check out the MythTV project supported hardware, if it doesn't work there your odds are slim of it being usable in Linux without specific manufacturer support. As far as I can tell, Hauppauge is about the only maker with even lip service support for Linux for some of their devices.
 
--wally.
 
OK,  Thanks for the goto :)
 
shadetree

---

### Post by wkulecz on 2010-03-11
Here is the best liste of supported video capture devices I've yet found:

[http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices)

--wally.

---

### Post by ibeofa on 2010-03-13
PLS can  anyone help am new here and i just bought a new  light wave cam but my cheese webcam booth can not find cam i have inatalled all the gstreamer but yet still not working pls i would apprecite if someone help me

---

