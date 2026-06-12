---
title: "Power Management for Laptop"
date: 2016-01-10
forum: Server Platforms
---

### Post by robo731 on 2016-01-10
I'm running Ubuntu Server 14.04 on a Dell Inspiron 15r 5521. I use the server primarily for downloading and storing media. I read through this [thread]("http://ubuntuforums.org/showthread.php?t=2309326&page=1"), but I have some ideas that go a bit beyond the scope of that thread. I plan to do the following:


[LIST]
[*]Turn off Wifi 
[*]Turn off sound 
[*][Enable Intel i915 RC6]("https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks") 
[*]Turn off webcam 
[*]Turn off touch (it's a touch screen laptop) 
[*][Spin down HDD after certain idle time]("http://www.howtoeverything.net/linux/hardware/permanently-configure-hard-drives-spin-down-after-given-idle-time") 
[*]Turn off unused bus terminals (USB, etc...) 
[*]Reduce CPU 
[*]Set screen timeout very low 
[/LIST]

I have some questions about these ideas though. I'm pretty sure things like turning off wifi and spinning down the HDD will be worth it, but I'm not so sure about these other ideas.

I have set wlan0 to not be automatically upped in etc/network/interfaces, but is the wifi still being powered? If so, can I shut it down completely somehow?

I know I can down-clock my CPU, but will this reduce performance when downloading or streaming to a different device on my network? Are there any other adjustments I should make in terms of the CPU?

Is there a considerable difference when the screen timesout compared to if I disabled graphics altogether?

Also, I have only found information on how to implement the ideas with links from the above list. Any links or directions on how to implement the above would be greatly appreciated.

---

### Post by MAFoElffen on 2016-01-12
I just happened to be a poster in that thread... The big difference is the hardware between the two. A Dell PowerEdge 2900 fully-loaded is pulling 1860W max. Your Dell Inspiron 15r 5521 laptop is pulling 65W. You don't have a WOL NIC... but as a laptop you have plenty of power saving features built in. In fact, most, in not all of everything you mentioned might all be in the BIOS(?). Since server is text on VGA, if you turn the backlighting down you should be fine. Server screen blanks if left sitting. Default is 10 minutes. You could change that to less time with setterm.

Wifi, hdd sleep, trackpad, webcam, sound mute, are all BIOS or Fn hotkey. Touch screen might be BIOS, but also a driver would not be load loaded for it in server. (No X) Reduced CPU power is a feature of some BIOS'es... and most likely of those on laptops, but some BIOS versions do not have that feature. 

For turning usb ports off-- Find the port address of a known device "connected" to that port in the branch of the tree view of list usb:
```

lsusb -t

```
To turn it off Bus 1, port 2 dev 3, simply echo address:
```

echo '1-2.3' > /sys/bus/usb/drivers/usb/unbind

```
Use lsusb to see that that port is gone from lsusb output or not with the address you used ... You may have to play with that to figure out from your output, what your port ID address is. It varies as per system. (see [sysfs]("https://www.kernel.org/doc/Documentation/sysfs-rules.txt"))

To enable it, echo same address to &#8220;bind&#8221;:
```

echo '1-2.3' > /sys/bus/usb/drivers/usb/bind

```
(Kernel Documentation: [sysfs-rules]("https://www.kernel.org/doc/Documentation/sysfs-rules.txt"))

What you might want to do is use lsusb to id all the ports on your laptop, then create a bash script containing those port addresses... Otherwise, the bios feature for usb is enable/disable for all usb ports.

---

### Post by robo731 on 2016-01-12
Unfortunately the InsydeH20 BIOS is virtually useless.

I was able to use setterm, thanks for that.

It seems that the function keys do not work on Ubuntu Server.

I'm going to run powertop and see which of these ideas are actually worth implementing. If I can save a decent amount of power I will definitely implement them, but if I can only save a couple watts, it's probably just not worth it.

---

### Post by robo731 on 2016-01-12
Powertop says that "The battery reports a discharge rate of ~10 W," At the time, the p2p1 network interface was about ~2.5 W and the wlan0 interface was about ~2.5 W and something, I wasn't sure what it was comprised ~3 W. I was able to disable the wlan0 using the function key, but the battery discharge rate is virtually the same (~9 W) and the p2p1 interface has shot up to ~8 W. This seems strange it's almost like the minimum the laptop can draw is ~10 W and the power increased for the p2p1 interface to compensate for the lack of power to the other components. What's going on here?

---

### Post by MAFoElffen on 2016-01-12
Remember the thread you mentioned in your first post and WOL?

Here is what Realtek says about the Realtek RTL8105E 5521 Network controller (in your laptop):
> 
Advanced Configuration Power management Interface (ACPI)&#8212;power management for modern operating systems that are capable of Operating System-directed Power Management (OSPM)&#8212;is supported to achieve the most efficient power management possible. PCI MSI (Message Signaled Interrupt) and MSI-X are also supported.

In addition to the ACPI feature, remote wake-up (including AMD Magic Packet and Microsoft Wake-up frame) is supported in both ACPI and APM (Advanced Power Management) environments. To support WOL from a deep power down state (e.g., D3cold, i.e., main power is off and only auxiliary exists), the auxiliary power source must be able to provide the needed power for the RTL8105E.

Feature:
 - Wake-on-LAN and remote wake-up support

So it might be possible to do WOL on that also... Dell does not mention it, but Realtek says it does.

---

### Post by robo731 on 2016-01-13
Oh, so are you saying that ~10 W is the amount required for WOL, and that's why it won't go any lower than that? Also, this laptop is not capable of WOL from a complete shutdown, only from sleep (suspend).

---

