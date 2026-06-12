---
title: "HP Proliant MicroServer N36L"
date: 2011-06-18
forum: Server Platforms
---

### Post by pmamatsis on 2011-06-18
Hi to all,
   in a couple of weeks i will be buying the HP microserver and
   the OS i will be installing is the Ubuntu Server version.
   Does anybody has anything that would like to point out at me ?
   I mean to say will i have any "issues" with non compatible
   piece of hardware ?

Best regards and
thank you all in advance.

---

### Post by pinus on 2011-06-19
I have one running here with Ubuntu 11.04 server, console graphics only.
Wake-On-Lan works, consumes about 0.5 watt waiting. With one disk it reduces its power consumption to about 28W after some time, drive idle but still spinning. The proprietary graphics driver didn't change the power consumption for me. Yust in case you read some articles about it. Booting from an USB stick works. Suspend doesn't work for me! RAM upgrade to 4GB was a bit tricky because you have to unplug several cables and get them into the small case again. It has an internal plug for an USB stick which holds my system. I dropped a 4GB file onto the NFS4 share and nautilus showed about 80MB/s transfer rate.

I would definitely buy it again.

---

### Post by pmamatsis on 2011-06-19
Thank you so much for your prompt response, one thing i have not told you is that i am going to use it for home server and because i need the 250GB of hard disk i am also thinking to install the system in a USB thumb drive and connect it to the internal USB port.

Best regards.

---

### Post by atca on 2011-06-19
> **pinus said:**
> I have one running here with Ubuntu 11.04 server, console graphics only.
Wake-On-Lan works, consumes about 0.5 watt waiting. With one disk it reduces its power consumption to about 28W after some time, drive idle but still spinning. The proprietary graphics driver didn't change the power consumption for me. Yust in case you read some articles about it. Booting from an USB stick works. Suspend doesn't work for me! RAM upgrade to 4GB was a bit tricky because you have to unplug several cables and get them into the small case again. It has an internal plug for an USB stick which holds my system. I dropped a 4GB file onto the NFS4 share and nautilus showed about 80MB/s transfer rate.

I would definitely buy it again.

how did you get WOL to work, I've had no luck at all under Ubuntu, see [here ]("http://confoundedtech.blogspot.com/2011/06/enable-wol-on-ubuntu-hp-microserver.html")

---

### Post by Benoe on 2011-07-07
> **atca said:**
> how did you get WOL to work, I've had no luck at all under Ubuntu, see [here ]("http://confoundedtech.blogspot.com/2011/06/enable-wol-on-ubuntu-hp-microserver.html")

I have working WOL on a HP Microserver bought yesterday. It wakes the server from switched off as well as hibernated state (yes, there is no suspend on this server :( )

Btw do you know any method to shorten the boot time? OS boot time is fine, I want to shorten the time the BIOS takes showing messages like "Press F10 to setup" and such

---

### Post by atca on 2011-07-15
> **Benoe said:**
> I have working WOL on a HP Microserver bought yesterday. It wakes the server from switched off as well as hibernated state (yes, there is no suspend on this server :( )

Btw do you know any method to shorten the boot time? OS boot time is fine, I want to shorten the time the BIOS takes showing messages like "Press F10 to setup" and such

How?

Did you have to do anything?
What kernel and version of Ubuntu are you running?

---

### Post by Benoe on 2011-07-16
> **atca said:**
> How?

Did you have to do anything?
What kernel and version of Ubuntu are you running?

Nothing special, just what you also write on your page.

---

### Post by atca on 2011-07-16
Odd I still have no luck :(

---

### Post by pmamatsis on 2011-07-28
Hi "atca",
   i am an owner of an HP Microserver myself and i don't believe that there is any way to shorten the boot time of the hardware unless you de-activate some of the features of the BIOS. Hm.....i am still a bit of newbie myself with this server but i believe that if, for example, there is a way to "cut-off" the network boot etc. etc. the boot time will be shorter. When i am a bit of a senior with the server myself i will come back. :)

Best regards,
Panos.

---

### Post by Benoe on 2011-07-28
> **pmamatsis said:**
> Hi "atca",
   i am an owner of an HP Microserver myself and i don't believe that there is any way to shorten the boot time of the hardware unless you de-activate some of the features of the BIOS. Hm.....i am still a bit of newbie myself with this server but i believe that if, for example, there is a way to "cut-off" the network boot etc. etc. the boot time will be shorter. When i am a bit of a senior with the server myself i will come back. :)

Best regards,
Panos.

Hi

It was me who wanted to find a shorter bot time, but it doesn't matter :)

I already removed network boot and raid setup delay, but there is still some time taken by "press F10" message, which I cannot remove.

Hopefully someone will modify this function in the bios as they did with sata mode for ODD and eSata (enabling AHCI for these ports)
Or find a way to enable S3 suspend...

---

### Post by cbuxton1984 on 2011-08-01
I have one of these, think they're a great system to run as a home server.

I initially ran it with Windows 2008 but have recently moved over to Ubuntu Server 11.04 because I can do the same plus some on Ubuntu as Windows.

One thing to note, the hardware RAID isn't really a true hardware RAID. It's a PDC software RAID controlled by the motherboard so it shouldn't impact your CPU. Only supports RAID 0 or 1 so I'd suggest using the Ubuntu software RAID 5 which works great.

WOL works great, powers up from any state so long as the power cord is plugged into the back. Also if you have a power cut or pull the power cord the server knows there is a problem, ones the power is restored it automatically powers the system back on.

If you use all the 4 bays you can buy a 4 or 6 disk bay to go into the 5.25inch CD-ROM slot. It takes 4 or 6 2.5inch drives for a little extra expansion.

Would recommend a remote management card, a little costly but they are great. We use them all the time at work and I wish I'd got one before now for the server.

---

