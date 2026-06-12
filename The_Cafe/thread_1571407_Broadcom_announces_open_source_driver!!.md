---
title: "Broadcom announces open source driver!!"
date: 2010-09-09
forum: The Cafe
---

### Post by the.dark.lord on 2010-09-09
Just saw this:  [http://thread.gmane.org/gmane.linux.kernel.wireless.general/55418](http://thread.gmane.org/gmane.linux.kernel.wireless.general/55418)

Thought I'd share.

Finally! :)

---

### Post by MasterNetra on 2010-09-09
About time.

---

### Post by blur xc on 2010-09-09
Now if intel would just follow suit w/ their gma950 and gma500 video chips, I'd be in netbook heaven...

BM

---

### Post by blueturtl on 2010-09-09
Great. One day when my grandkids ask why I don't have a single Broadcomm device in the house, I will reply: "You know, there was a time when Broadcomm didn't support Linux." "Really?" the kids will chime with their eyes gleaming. "Tell us more grandpa!" "Well it's a funny story actually, though it does involve a rather unfortunate dismantling of grandma's old HP notebook you see..." "Anyway that's when I replaced all the Broadcomms with Atheros and Intel" #-o

Broadcomm has nothing to lose and everything to gain, glad that they finally see the light.

---

### Post by Dr. C on 2010-09-09
This is excellent news. Only yesterday one would look at a laptop or a netbook at a store and under Windows 7 do the following: ```
Start > Control Panel > Administrative Tools > Computer Management > Device Manager
``` and look for Broadcom chips. If one found any the laptop or netbook was then eliminated from consideration.

---

### Post by kaldor on 2010-09-09
Holy crap. Does this mean I do not need to worry about wireless compatability nearly as much in the future? I'll eventually need a new laptop, and this would help a load.

---

### Post by Brent0 on 2010-09-09
> **blueturtl said:**
> Great. One day when my grandkids ask why I don't have a single Broadcomm device in the house, I will reply: "You know, there was a time when Broadcomm didn't support Linux." "Really?" the kids will chime with their eyes gleaming. "Tell us more grandpa!" "Well it's a funny story actually, though it does involve a rather unfortunate dismantling of grandma's old HP notebook you see..." "Anyway that's when I replaced all the Broadcomms with Atheros and Intel" #-o

Broadcomm has nothing to lose and everything to gain, glad that they finally see the light.

:lolflag:

---

### Post by Dustin2128 on 2010-09-09
excellent.

---

### Post by Ric_NYC on 2010-09-09
Thank you, Broadcom!
:popcorn:

---

### Post by drawkcab on 2010-09-09
Great.  Now I just need to send these drivers to myself back in 2005.

---

### Post by Rusna on 2010-09-10
This is so great news! I've eee 1215N with BCM4313 chip in it and now I'm more than excited about the future :)

---

### Post by undecim on 2010-09-10
> **kaldor said:**
> Holy crap. Does this mean I do not need to worry about wireless compatability nearly as much in the future? I'll eventually need a new laptop, and this would help a load.

This means that Linux can now include broadcom drivers with the livecd or default install. You can get broadcom support OUT OF THE BOX now, if this gets included with maverick (is it too late in the development cycle for that now?)

---

### Post by ukripper on 2010-09-10
Finally, after countless hacks I won't need my mods anymore.

---

### Post by jshepherd on 2010-09-10
Good, makes laptop/netbook purchases easier.:)

---

### Post by spoons on 2010-09-10
So does pretty much every network card now work on Ubuntu?

---

### Post by Ewingo401 on 2010-09-10
Maybe I'm just really lucky but...

```
sudo apt-get install b43-fwcutter
```

has always worked for me.

---

### Post by phrostbyte on 2010-09-10
Major kudos to Broadcom! :guitar:

---

### Post by oscarthegrouch on 2010-09-10
Hey everyone I'm new to the forum, as well as linux. I'm trying to install ubuntu 10.4 netbook remix onto a hp mini 1000 Vivienne Tamme Edition. Does anyone know if this may possibly support the Broadcom wireless card BCM4312? Below I've printed the results of sudo lshw - class network:

*-network
  description: Network controller
  product: BCM4312 802.11b/g
  vendor: Broadcom Corporation
  physical id: 0
  bus info: pci@0000:01:00.0
  version: 01
  width: 64 bits
  clock: 33MHZ
  capabilities: pm msi pciexpress bus-bridge latency=0
  configuration: driver=b43-pci-bridge latency=0
  resources: irq:16 memory:feafc000-feafc000-feafffff
*-generic
  descripton: Ethernet interface
  product: Illegal Vendor ID
  vendor: Illegal Vendor ID
  physical id: 0
  bus info: pci@0000:02:00.0
  logical name: eth0
  version: ff
  serial: 00:24:81:46:ef:62
  capacity: 100MB/s
  width: 32 bits
  clock: 66MHz
  capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
  configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.26 firmware=N/A latency=255 link=no maxlatency=255 mingnt=255 multicast=yes port=twisted pair
  resources: irq:26 memory:febfc000-febfffff ioport:ec00(size=256)
*-network DISABLED 
  description: Wireless interface
  physical id: 1
  logical name: wlan0
  serial: 00:24:2b:b4:c6:a9
  capabilities: ethernet physical wireless
  configuration: broadcast=yes driver=b43 driverversion=2.6.33-02063304-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

If its not possible to use this driver could someone point me in the right direction?

Thanks

---

### Post by MasterNetra on 2010-09-10
> **Ewingo401 said:**
> Maybe I'm just really lucky but...

```
sudo apt-get install b43-fwcutter
```

has always worked for me.

Little hard to do if the only means of access you have is wireless.

> **oscarthegrouch said:**
> Hey everyone I'm new to the forum, as well as linux. I'm trying to install ubuntu 10.4 netbook remix onto a hp mini 1000 Vivienne Tamme Edition. Does anyone know if this may possibly support the Broadcom wireless card BCM4312? Below I've printed the results of sudo lshw - class network:

*snip*

If its not possible to use this driver could someone point me in the right direction?

Thanks

If you can connect to the internet somehow (ethernet or with a USB wireless adapter) just load up the hardware manager while connected, let it update its indexes, exit then reload it you should have a choice between a B43 or STA for a driver, select one, let it install and you should be good to go(though you may need to wait a few moments for it to take effect).

Canonical doesn't preload Ubuntu with all of the files to run the b43 driver as some of them are not open-source.

---

### Post by oscarthegrouch on 2010-09-10
Thanks I'll give that a shot. I have the driver downloaded on a windows machine and plan to transfer via usb. I'll see what I can do. I also have a port for a hard line but thats not working either for some reason.

Thanks

---

### Post by oscarthegrouch on 2010-09-10
I took the file broadcom-wl-4.150.10.5.tar.bz2 and placed it under documents on the netbook. I then opened a terminal and navigated to the dir that contained the tar.bz2 file and the extracted contents. From that dir I ran the command: sudo apt-get install b43-fwcutter.

This was the results:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package b43-fwcutter

Thanks,

---

### Post by MasterNetra on 2010-09-10
> **oscarthegrouch said:**
> I took the file broadcom-wl-4.150.10.5.tar.bz2 and placed it under documents on the netbook. I then opened a terminal and navigated to the dir that contained the tar.bz2 file and the extracted contents. From that dir I ran the command: sudo apt-get install b43-fwcutter.

This was the results:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package b43-fwcutter

Thanks,

Thats because apt-get doesn't look at its host computer for files it looks at CD/DVD's and online repositories that are listed in software sources.

---

### Post by oscarthegrouch on 2010-09-10
Ok, Thanks MasterNetra is it possible to install the driver/firmware from a usb drive?

---

### Post by MasterNetra on 2010-09-10
> **oscarthegrouch said:**
> Ok, Thanks MasterNetra is it possible to install the driver/firmware from a usb drive?

Check this out: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9821161](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9821161)
(Post 7)

---

### Post by oscarthegrouch on 2010-09-10
Thanks so much for pointing me in the right direction :D

---

### Post by MasterNetra on 2010-09-10
> **oscarthegrouch said:**
> Thanks so much for pointing me in the right direction :D

No problem, I have a broadcom too, of course I also have a USB Wireless Adapter that works well with Ubuntu too that I plug in, nab the drivers I need and unplug.

---

### Post by Khakilang on 2010-09-11
Thats great news. I hope other vendors will see the light and follow suit.

---

