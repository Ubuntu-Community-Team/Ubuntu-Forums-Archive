---
title: "USB flash drive VERY slow"
date: 2012-01-23
forum: Virtualisation
---

### Post by Rebelli0us on 2012-01-23
Host   -- 64-bit Ubuntu 10.10 
Guests -- Win2000 and Win7 

Reading photos from USB flash drives is **very **slow. I'm surprised because both these OSes boot and run faster as VMs. Any solution?

---

### Post by snowpine on 2012-01-23
A few of obvious questions out of the way:

1. Have you installed VirtualBox Guest Additions on both guests?

2. Have you benchmarked the read/write speed of the flash drive in both the guests AND the host to measure the actual difference due to VirtualBox?

3. Have you tried a Linux guest to determine whether it's a VirtualBox problem or a Windows problem?

---

### Post by ajgreeny on 2012-01-23
Just out of interest, have you added the kernel ppa to your sources and are you using a newer that normal kernel.

I ask because I tried that in 10.04 and with the 2.6.38 kernel that was available that way the usb speeds reduced fro around 15 -20MB/sec to only a few KB/sec, totally unacceptable.  I soon got rid of that as an idea and stuck with the normal kernels.

---

### Post by Rebelli0us on 2012-01-23
> **snowpine said:**
> A few of obvious questions out of the way:

1. Have you installed VirtualBox Guest Additions on both guests?

2. Have you benchmarked the read/write speed of the flash drive in both the guests AND the host to measure the actual difference due to VirtualBox?

3. Have you tried a Linux guest to determine whether it's a VirtualBox problem or a Windows problem?


1 -- yes
2 -- Didn't benchmark but host speed feels just fine, guests are painfully slow.
3 -- Yes. It's not a Windows problem.

---

### Post by Rebelli0us on 2012-01-23
> **ajgreeny said:**
> Just out of interest, have you added the kernel ppa to your sources and are you using a newer that normal kernel.

I ask because I tried that in 10.04 and with the 2.6.38 kernel that was available that way the usb speeds reduced fro around 15 -20MB/sec to only a few KB/sec, totally unacceptable.  I soon got rid of that as an idea and stuck with the normal kernels.

I'm using vanilla kernel, whatever version the Update Manager installs in 10.10

So you've had that too, not everybody does but I've seen many reports of problems with USB speed.

---

### Post by snowpine on 2012-01-23
I found dozens of threads over on VirtualBox forums when I googled:

```
site:forums.virtualbox.org "slow usb"
```

It appears to be a FAQ over there, good luck! :)

---

### Post by bluexrider on 2012-02-11
> **snowpine said:**
> I found dozens of threads over on VirtualBox forums when I googled:

```
site:forums.virtualbox.org "slow usb"
```It appears to be a FAQ over there, good luck! :)
Yes, but mostly from 2009 and 2010 not as many in 2011. It may be getting better

---

### Post by japzone on 2012-02-11
Did you install the Extension Pack to enable USB 2.0 support?

[**https://www.virtualbox.org/wiki/Downloads**]("https://www.virtualbox.org/wiki/Downloads")

PS: How's the Thinkpad?

---

### Post by Rebelli0us on 2012-02-13
> **japzone said:**
> Did you install the Extension Pack to enable USB 2.0 support?

[**https://www.virtualbox.org/wiki/Downloads**]("https://www.virtualbox.org/wiki/Downloads")

PS: How's the Thinkpad?

Yes extension pack & guest additions installed. Thinkpad is in my suitcase permanently since I only use it when I travel. Maybe it's time for an iPad.

---

### Post by japzone on 2012-02-13
> **Rebelli0us said:**
> Yes extension pack & guest additions installed. Thinkpad is in my suitcase permanently since I only use it when I travel. Maybe it's time for an iPad.

Hmm. Try Uninstalling/Reinstalling GE and then if that doesn't help try Uninstalling/Reinstalling VirtualBox.

PS: Have you tried the Tips I posted in your Thinkpad Topic?

---

### Post by Rebelli0us on 2012-02-14
> **japzone said:**
> Hmm. Try Uninstalling/Reinstalling GE and then if that doesn't help try Uninstalling/Reinstalling VirtualBox.

PS: Have you tried the Tips I posted in your Thinkpad Topic?

What is GE? I followed the install instructions on Oracle's website, i.e. through Update Manager, they don't say how to remove. I'm inclined to not try and fix it and let Oracle do it instead.

Thank you, I've bookmarked the Thinkpad thread. I think I'd tried all the startup options at the time, then I gave up and used Win2k. But I may try Lubuntu agaIn when I get a chance. I have an even older Toshiba laptop 486, maybe I should learn to use ebay ;)

---

