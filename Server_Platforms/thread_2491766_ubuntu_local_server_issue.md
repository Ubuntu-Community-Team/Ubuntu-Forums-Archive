---
title: "ubuntu local server issue"
date: 2023-10-19
forum: Server Platforms
---

### Post by gfxnick on 2023-10-19
hi i have been stuck on a problem for the past few days I am using 22.04.3 LTS and i am using usb tethering but an issue has arose i have installed casaos and get everything working on the host device with is my phone but when i go to try open casaos on another device i get a connect time out  i have opened port 22 and port 80 and gone through countless of the other solutions on multiple forums and none have succeeded Any help is appreciated.

---

### Post by TheFu on 2023-10-19
> Official Support

    Debian 12 (&#9989; Tested, Recommended)
    Ubuntu Server 20.04 (&#9989; Tested)
    Raspberry Pi OS (&#9989; Tested)
...
CasaOS is currently under active development. Support is limited before CasaOS reaches v1.0.

Ref: [https://github.com/IceWhaleTech/CasaOS](https://github.com/IceWhaleTech/CasaOS)

Trying to run on an untested OS is a mistake.

It looks interesting, though I can't easily see the features - they just say "Cloud Server".

---

### Post by MAFoElffen on 2023-10-19
I don't understand the problem. Is this an Ubuntu Sever networking problem where you are running having a problem tethering the network connection through your phone and having problems connecting to ii from another device through that network right? And the intermediary service just happens to be as a CasaOS personal cloud?

So is this a networking problem?

Or a CasaOS service problem?

I think you have a bunch of wrenches thrown into that making it harder than it should be...

If a networking problem... Diagnose it out... When diagnosing a USB tethering problem, do these (as just the start of the hunt)
```

sudo dmesg | grep -A100 -e 'usb [0-2]\-[0-9]: New USB device found' 
sudo lshw -C Networking

```
In the output of lshw, it's going to look different, like this example. I'll highlight the things that make it stand out as "different" if you are doing USB tethering.
```

  *-network
       description: Ethernet interface
       physical id: 2
       logical name: [COLOR=#ff0000]enp0s20f0u1[/COLOR]
       serial: 3e:2a:f0:fa:ff:0d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=[COLOR=#ff0000]rndis_host[/COLOR] driverversion=22-Aug-2005 firmware=[COLOR=#ff0000]RNDIS[/COLOR] device link=yes multicast=yes
           [COLOR=#ff0000]configuration[/COLOR]: broadcast=yes driver=[COLOR=#ff0000]iwlwifi[/COLOR] driverversion=4.15.0-22-generic firmware=34.0.1 [COLOR=#ff0000]ip=192.168.1.8[/COLOR] latency=0 link=yes multicast=yes wireless=IEEE 802.11
           resources: irq:138 memory:dd200000-dd201fff
      *-network
           description: Ethernet interface
           physical id: 2
           logical name: enp0s20f0u1
           serial: 3e:2a:f0:fa:ff:0d
           capabilities: [COLOR=#ff0000]ethernet physical[/COLOR]
           configuration: broadcast=yes driver=[COLOR=#ff0000]rndis_host[/COLOR] driverversion=22-Aug-2005 firmware=[COLOR=#ff0000]RNDIS[/COLOR] device link=yes multicast=yes

```

Notice the thing that jumps out and grabs you it that it has a "*-network" sub-column section... where it is using rndis_host as a driver, which is a driver for USB Ethernet networking...

With Ubuntu server, you will use information from this output to create your netplan yaml file, before your can generate and apply it...

Then what are your USB settings on your phone? 

With DHCP = yes in netplan, are your assigned an IP address from the phone?
```

ip addr show

```

It you have networking worked out and working, and you are rather asking about why a device is timing out connecting to the Personal Cloud service of CasaOS, then I do not know. I have no experience on it. This is the first time I have ever heard of it.

---

### Post by TheFu on 2023-10-19
Sometimes a cheap, old, wifi router makes sense.  Especially to avoid USB tethering for network junk on a LAN.

---

