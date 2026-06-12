---
title: "GlobalSat"
date: 2009-04-06
forum: Wine
---

### Post by GPSLogger on 2009-04-06
I've got a GlobalSat Data Logger (DG-100).  I have managed to get the PC Utility software working under Wine.  Using Wintricks I installed all of the relevent fonts and the .net framework (MS .NET 1.1 & MS .NET 2.0)

I'm new to Ubuntu and from searching on the net I realised that I had to make a link from my Data Logger to COM1.  So to find the USB location I typed the following into terminal:

```
dmesg | grep USB
```

The response (cut down) I receive is:

```
usb 2-1: pl2303 converter now attached to ttyUSB0
usbcore: registered new interface driver pl2303
/build/buildd/linux-2.6.24/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver
```

So, to link COM1 to ttyUSB0 I typed in:

```
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1
```

I checked the directory ~/.wine/dosdevices/ to be sure the link info was in there - it was.  So I opened the GlobalSat Data Logger PC Utility under Wine.  COM1 wasn't available in the COM Port drop down menu, so I tried typing in how it appears on my Windows PC "COM1:" but still no joy; I was still receiving the error "ComPort ERROR!!".  Are there other parts of winetricks I should install?  I have tried various COM port numbers and restarted etc but I still can't communicate with my logger.  Can anyone spot what I'm doing wrong?

---

