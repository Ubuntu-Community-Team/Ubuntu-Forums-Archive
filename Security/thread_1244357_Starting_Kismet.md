---
title: "Starting Kismet"
date: 2009-08-19
forum: Security
---

### Post by phillip4672 on 2009-08-19
Hi,

I'm trying to get Kismet working from the command line. I'm not very experienced with the command line so this is proving to be quite trying.

I have a Dell Mini Inspiron 1010. I installed Kismet from the command line, which seems to have worked but I seem to have run into a couple of problems at this point.

1) I don't know how to change the source= line in the kismet.conf file.

2) I have a Broadcom wireless card and from what I've seen on various web pages this could be a problem.

I've tried using backtrack 3 but this doesn't support many of the features of my laptop. I tried this using a bootable USB drive. I tried the USB drive on my desktop but after initially encouraging graphics and scrolling scripts the screen just went dead!

I've got a Belkin USB wireless adapter as well but with problem (1) above I haven't got very far with it!

Can anyone help??

Kind regards,

Phillip

---

### Post by cariboo on 2009-08-19
According to the Kismet readme, it should be located in either /usr/share/kismet or /usr/share/doc/kismet, your broadcom chipset is not supported. What chipset does your belkin usb adapter use?

---

### Post by punia1979 on 2009-08-20
ye I have pretty much the same problem... have difficulties 2configure kismet on 9.04... getting this message:

root@a5920g:/home/robert# kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.

I have found kismet conf in: /etc/kismet

anyone have a quick tutorial how to configure it?

---

### Post by phillip4672 on 2009-08-20
cariboo907: the USB wireless adapter is a Belkin F5D7050. A quick web search told me that the chipset is Ralink RT2500. If I do a lspci with the adapter connected, however, I don't get a listing for it. Is there an analogue for usb devices?
 
I also found the config file under /etc/kismet/ but the readme is difficult to follow. I'm not sure how to set up the values it asks for. What's the difference between "source" and "ncsource". Do you use the same names as returned by wiconfig?
 
I'm going to try this using an ethernet connection to my wireless router and see what happens. So far I've been getting the same error message as the one posted by punia1979.
 
Thanks for the posts!
 
Phillip

---

### Post by cariboo on 2009-08-20
@phillip4672

The usb equivalent to lspci is lsusb, although it won't give you as much info as lspci. The best way to find the info is to run:

```
sudo lshw -C network
```

I'm in the midst of doing an upgrade on this computer I'm using, it's an old PII 400Mhz, so it might take a while. Once it's done, I'll install a wireless usb device and give kismet a try.

---

