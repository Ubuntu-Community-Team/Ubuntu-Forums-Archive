---
title: "ffado-mixer problems"
date: 2011-09-10
forum: Ubuntu Studio
---

### Post by kamlapati on 2011-09-10
I ran Ubuntu Studio audio recording for several years using with 9.04. Now that that is no longer support, I upgraded to Natty. I am still running with the generic kernel. I thought I could do some debugging before installing the low-latency kernel.

I have a Focusrite Saffire PRO 26 i/o and a SIIG Firewire PCI Express adapter in my laptop.

Here's my problem. When I start ffado-mixer I get this:

```
15:09:24 logginghandler: Could not communicate with the FFADO DBus service...
```

Seems like the PC sees the Firewire card OK. 

lspci:

```
04:00.0 PCI bridge: Texas Instruments XIO2213A/B/XIO2221 PCI Express to PCI Bridge (rev 01)
05:00.0 FireWire (IEEE 1394): Texas Instruments XIO2213A/B/XIO2221 IEEE-1394b OHCI Controller (rev 01)
```

And this:

```
>ffado-test Discover
Cannot create thread 1 Operation not permitted
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

ERROR: messagebuffer not initialized: 09222956077: Fatal (devicemanager.cpp)[ 191] initialize: No firewire adapters (ports) found.
Could not initialize device manager
```

And this:

```
>lsmod | grep 'firewire\|1394':
firewire_ohci          31504  0
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

```

Any help would be appreciated! Why won't ffado-mixer start? Why won't it recognize my audio interface?

---

