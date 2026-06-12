---
title: "Zoom H4 doesn't show up in JACK"
date: 2009-12-22
forum: Ubuntu Studio
---

### Post by elsrkite on 2009-12-22
I'm trying to use my Zoom H4 as a USB audio interface to record into Ardour and do live signal processing. The H4 works with Audacity, so it doesn't seem to be a hardware problem. But it doesn't appear in JACK at all.

I'm using Ubuntu Studio 9.04, and QjackCtl.


Please tell me if there's other info I should put up here. Thanks for any help or ideas!

---

### Post by gorgon on 2009-12-23
Hi,

just to be sure, does it not show up when you (in qjackctl) enter setup and look at the 'interface' drop down menu?

---

### Post by AutoStatic on 2009-12-23
Hello elsrkite, what's the output of **lsusb** and **aplay -l** with the H4 plugged in?

---

### Post by elsrkite on 2009-12-23
> **gorgon said:**
> Hi,

just to be sure, does it not show up when you (in qjackctl) enter setup and look at the 'interface' drop down menu?

I'm not finding the Interface menu. Maybe it has different names in the versions we're using?

> **AutoStatic said:**
> Hello elsrkite, what's the output of **lsusb** and **aplay -l** with the H4 plugged in?

Shows up in both.

lsusb:
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 008: ID 1686:0045 ZOOM Corporation H4 Digital Recorder
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

(anyone know what a "Stroage Device is"? lol)

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: H4 [H4], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by AutoStatic on 2009-12-23
In QjackCtl you should press the 'Setup' button on the right side. This opens the Setup window, see the attachment.
In the Interface drop down menu you should be able to select hw:1 or USB Audio. That's your H4. You could also add an entry yourself which should read: *hw:H4*

---

### Post by elsrkite on 2009-12-23
Oh, gotcha. Don't know how I missed that.

I left the interface as it was and just changed the input device. It's working now, though it still doesn't show up in the connections window. Thanks for your help!

---

### Post by AutoStatic on 2009-12-23
You're welcome.
Maybe you could post a screenshot of the Settings and Connections windows with the H4 plugged in an JACK running?

---

### Post by KoRnholio on 2010-02-17
It shows up as 'System' in the qjackctl connections window.  I know, I was expecting something more descriptive too.

After figuring out how to get this to work, I was so overjoyed that I finally set up my blog to tell people how I got a working Zoom H4 interface.

[http://tristanhaywardcrockett.com/?p=4](http://tristanhaywardcrockett.com/?p=4)

---

### Post by AutoStatic on 2010-02-18
Good to read that you got it working too!
And nice blog entry, I'm not with you though on the part about things being wrong with Linux audio production ;)

---

### Post by xianbei on 2011-01-07
Jack > Settings

Interface = default
Input device = hw:H4
Output devce = hw:1

at least, that worked for me.

---

