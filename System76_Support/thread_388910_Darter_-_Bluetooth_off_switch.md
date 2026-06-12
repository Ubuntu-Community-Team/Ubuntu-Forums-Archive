---
title: "Darter - Bluetooth off switch?"
date: 2007-03-20
forum: System76 Support
---

### Post by cowbean on 2007-03-20
The hardware wifi switch (next to the blank screen switch in the upper left corner of the keyboard) seems to control both wifi and bluetooth.  Is there a way to turn either one on and off independently?  I've tried iwconfig eth2 power off, as well as hciconfig down, but neither of these seem to do the trick -- the wifi light still blinks intermittently, which I take to mean the radio is still on, and after issuing hciconfig down i can still immediately connect via bluetooth.

I'm mostly trying to maximize battery, any help would be greatly appreciated.

---

### Post by crichell on 2007-03-20
That's a good question.  The hardware switch does turn off both but I know one customer was turning off Bluetooth and leaving wireless on.  I'll check with him and post back.

Cheers, Carl

---

### Post by cowbean on 2007-03-28
Hi Carl -- Any luck with this?

---

### Post by crichell on 2007-03-28
Yes - the wireless/Bluetooth switch is an all or nothing deal.  I heard otherwise but haven't been able to replicate.  This command will turn off the radio:

```
sudo /usr/sbin/hciconfig hci0 down
```

Interestingly the blue light may stay on but the radio is off.

---

### Post by madcitybrit on 2007-03-28
The Bluetooth light on my Darter doesn't come on (even when Bluetooth is on and I'm actively using it). Wireless light seems to work. 

I've been successfully using Bluetooth however with my Sony Ericsson phone, and 'switch it on' via the Applications>Accessories menu (Bluetooth File Sharing option). Unless I do this my phone won't find my laptop, so I'm assuming Bluetooth is switched off by default (but I'm still using WI-FI), at least in Gnome anyway. With Bluetooth on an icon appears in my application panel, and by right-clicking this icon I can choose 'quit' to switch it off.

So long story short, for me and my new Darter with the default Gnome, Bluetooth seems to be off by default regardless of the physical wireless switch on the laptop (so software controlled). Does this help?

---

### Post by madcitybrit on 2007-04-11
An update to my last post. Bluetooth File Sharing was installed by default when I first received my Darter. I have since re-installed Ubuntu and initially Bluetooth wasn't working, whereby I found that the Bluetooth File Sharing prog wasn't listed under my Applications>Accessories menu. Seems this isn't installed by the default Ubuntu install, system update, or System76 Driver installation (as part of the System Recovery Process).

For future reference... 

To install Bluetooth File Sharing go to Synaptic Package Manager (under System>Administration) and select gnome-bluetooth, then click Apply. Once installed you'll be able to switch Bluetooth on and off with System>Administration>Bluetooth File Sharing. When switching it on an icon will appear in the top panel by the date and time to show that Bluetooth is on and waiting for devices. Right click and select quit to switch Bluetooth off.

---

