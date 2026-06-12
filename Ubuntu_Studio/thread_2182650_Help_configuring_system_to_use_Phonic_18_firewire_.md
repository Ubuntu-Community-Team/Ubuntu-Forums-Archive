---
title: "Help configuring system to use Phonic 18 firewire mixer"
date: 2013-10-21
forum: Ubuntu Studio
---

### Post by astembridge on 2013-10-21
I have the Phonic MKII 18 firewire mixer hooked up and when I issue ffado-test ListDevices, I see the device: 


[FONT=courier new]sudo ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x0001080000016941  0x00000108  0x00000000   Linux Firewire - 
   1       0x0014960006000000  0x00001496  0x00060000   Phonic - HB18 FW MKII 
no message buffer overruns

[/FONT]
So it seems my Phonic mixer is seen.   I tried launching JACK, but I'm not seeing the Phonic in the Connect screen (or anywhere else in JACK Audio Connection Kit). 

What do I need to look at next in order to use this device in Ardour?

---

### Post by jejeman on 2013-10-22
Give
```
cat ~/.jackdrc
```
If shows nothing tell us how is the JACK set up.

---

### Post by astembridge on 2013-10-22
> **jejeman said:**
> Give
```
cat ~/.jackdrc
```
If shows nothing tell us how is the JACK set up.

Off to work, will post contents of ~/.jackdrc tonight. 

I'm brand new to linux audio and JACK.  Can you elaborate on the second half of your question?   How would I provide this info?

---

### Post by jejeman on 2013-10-22
You can just take a screenshot of JACK settings window in Qjackctl.
Like this
[http://qjackctl.sourceforge.net/image/qjackctlSetupForm1.png](http://qjackctl.sourceforge.net/image/qjackctlSetupForm1.png)

---

