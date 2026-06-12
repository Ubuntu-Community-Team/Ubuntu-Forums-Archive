---
title: "Pan P7 wireless &quot;device not ready&quot; after last 10.04 update"
date: 2011-06-14
forum: System76 Support
---

### Post by isaacullah on 2011-06-14
Hi all,

  After I ran the latest auto updates for Ubuntu 10.04 this morning, I no longer can activate my wireless. Under the network icon in the dock, it says "Device Not Ready" under "Wireless Networks". Using the Fn F11 key does nothing, and "Enable Wireless" is checked, but there is zero connectivity. I mean, it doesn't even see ANY networks, although there are plenty available (confirmed with my other PC). The ethernet port works fine, however. It's just the wireless. 

Here is the output of :~$ sudo lshw -C network

 ```
 *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:9a:7d:d6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f0300000-f0301fff
```
As you can see, it shows my wireless device as disabled, and there doesn't seem to be a way for me to enable it! Quite frustrating!

Searching on google found a few posts on the ubuntu forums in regards to this error. Most had to do with not having the correct drivers and/or device firmware installed (and most were on Dell's). I don't think that's what's going on here, though (and, yes, I've already tried re-running the sys76 driver just for good measure).

One other thing to note is that I think the update I just did may have installed a new kernel (it asked me to reboot after the update was finished), but I was busy "multitasking", so I didn't really pay attention to what was included in the update (I think I remember Flash, but that that's about it). 

Those are the only clues I've got right now. Can one of you guys help me out? This is a PanP7 that I got about 6 or 7 months ago, and I'm still using 10.04. ANY help will be greatly appreciated!

---

### Post by peterrix on 2011-06-14
Same here I let Update Manager install what looked like a Kernal Update and after re-boot my wireless network reports Device Not Ready. Had to dig up the old Ethernet Cable to get on!

Help

---

### Post by peterrix on 2011-06-14
As I said earlier, I had the same problem with 10.4 after this mornings update.

I decided to try installing 10.10 which has fixed the issue. It tok quite a long time to do the updrade, over 2 hours but I guess it was worth it.

---

### Post by isaacullah on 2011-06-14
Hmmmm... Definitely seems like it was the kernel update that did it then. It seems I have three options: (1) Go back to the last kernel (not sure how to do this, but can look it up). (2) Upgrade to 10.10 (but I kinda wanted to stick with the LTS to avoid having to upgrade so many damn times). or (3) Try to figure out what, exactly, happened during the kernel upgrade, and try to figure out some solution to it, specifically (I will need LOT'S of help for that). I suppose there is a fourth option too: Do nothing, live without wireless until the next kernel update and see if that fixes it.

Any suggestions from the Sys76 support staff?

---

### Post by isaacullah on 2011-06-14
Well, I decided to revert back to the previous kernel, and lo and behold! The wireless works again. Reverting was easy, I simply opened StartUp-Manager (System > Administration > StartUp-Manager). Under the "Boot Options" tab, in the pull-down menu for "Select Default Operating System" I chose the previous kernel (Linux 2.6.32-32 generic) instead of the newly installed one (Linux 2.6.32-33 generic). Then after closing StartUp-Manager and rebooting, I'm now in the older kernel, and my wireless works again. Let's see what happens after the NEXT kernel update (to 2.6.32-34, I'm assuming)!

Hope this helps someone!

---

