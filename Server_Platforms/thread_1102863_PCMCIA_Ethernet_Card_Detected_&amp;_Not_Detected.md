---
title: "PCMCIA Ethernet Card Detected &amp; Not Detected"
date: 2009-03-22
forum: Server Platforms
---

### Post by airbad on 2009-03-22
Hi all,

Yeah, wierd title, wierd issue.  I can't find anything similar using the search function, or on the web in general (via Google).  I tried setting up Ubuntu Server on an old Dell Inspiron 7500 laptop yesterday, using a PCMCIA 10/100 card ("MRI Ethernet PCMCIA") for network access.

The card was detected fine during the installation, and the installer quite happily retrieved an IP over DHCP, but when booting into the new system, it doesn't seem to have been detected, and it certainly doesn't have access to the network.  ifconfig just reports the loopback interface, but /etc/interfaces/network *does* mention the eth0 device.  I'm guessing that the installer wrote the interfaces file, but that something isn't being loaded when the machine boots.  I tried running lspci, in case that covered PCMCIA devices, but there's no mention of it there.  What's interesting is that the card's lights have come on and blink occassionally, suggesting that it's communicating with the network in some way, and certainly drawing power.

Any ideas?

Cheers,

AirBad

---

### Post by windependence on 2009-03-22
Try to start the interface:

```
sudo ifconfig eth0 up
```

Also, you have to use ifconfig -a to show all interfaces, even the ones that are not up.

-Tim

---

### Post by airbad on 2009-03-22
Just tried running lshw, and there's no mention of any network devices - but the card's lights switch on and off during the hardware detection phase of the boot sequence, which indicates its being recognised in some capacity.

"sudo ifconfig eth0 up" fails with the message "ERROR while getting interface flags: No such device".  I still can't figure out why the installer used it without any problems, but it now refuses to work.

AirBad

---

### Post by airbad on 2009-03-22
OK, this is a little strange.  I popped in a USB WLAN dongle that I know works with Ubuntu, and used it to install the pcmciautils package using apt-get and, after a restart, the PCMCIA ethernet card seems to work without any problems :S.  Is it possible the pcmciautils package came with some extra drivers or something?  Or could the WLAN dongle have had an effect?

AirBad

---

