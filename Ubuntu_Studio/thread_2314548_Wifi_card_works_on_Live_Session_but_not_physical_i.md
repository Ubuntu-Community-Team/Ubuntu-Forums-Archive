---
title: "Wifi card works on Live Session but not physical installation"
date: 2016-02-22
forum: Ubuntu Studio
---

### Post by nigel12 on 2016-02-22
So I used pendrivelinux.com's Universal USB Installer to install Ubuntu Studio 14.04.4 x64 onto a 4gb flash drive. Worked perfectly, of course, so I booted a live session to ensure everything would work as expected.

Initially my Wifi PCI Express card (TP-LINK AC1300 Model Archer T6E) was disabled, so I enabled it in Settings Manager->Additional Drivers.

It recognized it as "Broadcom Corporation: Unknown".

After changing it from "Do not use the device" to "Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)" it took a few seconds and the card was working perfectly.

So I think, "great! Time to actually install now." But once I booted the OS from the hard drive the device was disabled again, so I tried to enable it in the exact same fashion as before, but instead the "Do not use the device" box was quickly rechecked and under "Broadcom Corporation: Unknown" it now says "the device is not working".

I'm sending this from a live session right now on the same computer, so the card definitely works. Maybe during installation a newer driver was downloaded that doesn't support my card?

Any help or ideas for fixing this issue are greatly appreciated.

Thanks.

Some extra info:

From the live session:
```
ubuntu-studio@ubuntu-studio:~$ sudo lshw -numeric -C network
PCI (sysfs)  

  *-network               
       description: Wireless interface
       product: BCM4360 802.11ac Wireless Network Adapter [14E4:43A0]
       vendor: Broadcom Corporation [14E4]
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 03
       serial: f4:f2:6d:ec:10:a6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.0.10 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:fb5f8000-fb5fffff memory:fb200000-fb3fffff
```
```
ubuntu-studio@ubuntu-studio:~$ lspci -nn | grep -i network
07:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
```

Going to boot off the hdd now and see if anything is different, will update post if so.

So everything was the same, aside from things that would be assigned once in use.

After failing with ndiswrapper (kept getting "modprobe: FATAL: Module ndiswrapper not found"), even though the driver installed properly and associated itself with the hardware, I decided to try a regular 14.04.4 amd64 install.

The exact same problem arose even down to ndiswrapper, however I received different and less errors while installing ndiswrapper-dkms this time. On Ubuntu studio, it would throw errors related to the low latency kernel.

Since this is an issue with Ubuntu and not strictly Ubuntu Studio, hopefully an admin can move this thread to the proper category.

---

### Post by goofprog on 2016-02-22
Maybe just copy the driver from /lib/firmware to your install.

---

### Post by nigel12 on 2016-02-22
> **goofprog said:**
> Maybe just copy the driver from /lib/firmware to your install.
Thanks for your response, I will try this and post back with the results.

No luck. Exact same results, the files don't even seem to be any different.

I may have copied the wrong files, but I copied the ones that sounded right:
```
/lib/firmware/bcrm/bcm43xx-0.fw
/lib/firmware/bcrm/bcm43xx_hdr-0.fw
/lib/firmware/bcrm/bcm4329-fullmac-4.bin
/lib/firmware/bcrm/brcmfmac4329-sdio.bin
/lib/firmware/bcrm/brcmfmac4330-sdio.bin
/lib/firmware/bcrm/brcmfmac4334-sdio.bin
/lib/firmware/bcrm/brcmfmac4335-sdio.bin
/lib/firmware/bcrm/brcmfmac4339-sdio.bin
/lib/firmware/bcrm/brcmfmac4354-sdio.bin
/lib/firmware/bcrm/brcmfmac4356-pcie.bin
/lib/firmware/bcrm/brcmfmac43143.bin
/lib/firmware/bcrm/brcmfmac43143-sdio.bin
/lib/firmware/bcrm/brcmfmac43236b.bin
/lib/firmware/bcrm/brcmfmac43241b0-sdio.bin
/lib/firmware/bcrm/brcmfmac43241b4-sdio.bin
/lib/firmware/bcrm/brcmfmac43242a.bin
/lib/firmware/bcrm/brcmfmac43362-sdio.bin
/lib/firmware/bcrm/brcmfmac43569.bin
/lib/firmware/bcrm/brcmfmac43570-pcie.bin
/lib/firmware/bcrm/brcmfmac43602-pcie.ap.bin
/lib/firmware/bcrm/brcmfmac43602-pcie.bin
```

I'm going to see if the problem persists in 15.10.

Different issues, but still not working in 15.10 either.

---

### Post by Nosphky on 2016-02-23
I had a similar problem with wifi and Broadcom drivers.  The effective answer was supplied by hadaka in post #3 to the following thread :

[http://ubuntuforums.org/showthread.php?t=2253877](http://ubuntuforums.org/showthread.php?t=2253877)

You will see that I had a few goes at the problem but finally did a good install using just the info in post #3

hth

---

### Post by nigel12 on 2016-02-23
> **Nosphky said:**
> I had a similar problem with wifi and Broadcom drivers.  The effective answer was supplied by hadaka in post #3 to the following thread :

[http://ubuntuforums.org/showthread.php?t=2253877](http://ubuntuforums.org/showthread.php?t=2253877)

You will see that I had a few goes at the problem but finally did a good install using just the info in post #3

hth

Wow, I feel really dumb. So I got it working perfectly, but I feel embarrassed to explain how...

So I tried your advice from post #3, when I tried to remove bcmwl-kernel-source, it told me it wasn't installed. After installing it, the card immediately started working.

Thank you so much for your reply, I never would have realized this without your help.

Now I am successfully running Ubuntu Studio 15.10 amd64 with my wireless card functioning perfectly.

---

### Post by Nosphky on 2016-02-23
No need to worry about feeling dumb.  We all go there from time to time.
Glad it's all working now.

---

