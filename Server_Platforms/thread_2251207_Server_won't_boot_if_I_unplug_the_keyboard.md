---
title: "Server won't boot if I unplug the keyboard"
date: 2014-11-02
forum: Server Platforms
---

### Post by Maheriano on 2014-11-02
I have an Acer AC100 home server and I've been using it for about 3 years now without any issues. It has Ubuntu 14.04 installed on it which I just reinstalled a couple of months ago. For some reason yesterday I shut it down, started it up again and it doesn't show the GRUB menu, it just beeps like crazy after POST. It beeps really loud and fast forever, it won't stop until I turn the system off again.

I have figured out that I can boot into a Live USB without any problem, I can run Boot Repair, then reboot into the BIOS and choose an option titled Ubuntu from the boot menu. Then the system works fine as often as I want to reboot it, no problems. If I unplug the keyboard, it does the same beeping at boot and I have to run Boot Repair again in order to fix it again. Even if I plug the keyboard back in, it won't boot again until I run Boot Repair. And that Ubuntu option disappears from the BIOS boot menu until I've run Boot Repair again. I can't figure this out, I'm going to try reinstalling 14.04 again now.

---

### Post by tgalati4 on 2014-11-03
It could be a PSU problem.  Check the 5VDC and 12VDC with a voltmeter.  Why did you reinstall 14.04 a couple of months ago?  14.04 is pretty stable.  What were your initial symptoms that made you reinstall the first time?

It could also be a disk problem.  What is the SMART status of the disk:

```
sudo smartctl -a /dev/sda
```

---

### Post by Jonathan L on 2014-11-03
Hi Maheriano

It's just a guess as I don't know anything specific about this model of server:  Many systems have a BIOS option to ignore/complain about missing keyboards, often with beep codes to indicate the problem.  If it has a battery for configuration memory, perhaps that's run out (quite possible after three years) and it got its BIOS configuration in a mess.  So I'd check and perhaps replace the battery, and check the BIOS configuration screens.

Hope that's of some use.

Kind regards,
Jonathan.

---

### Post by Maheriano on 2014-11-04
> **tgalati4 said:**
> It could be a PSU problem.  Check the 5VDC and 12VDC with a voltmeter.  Why did you reinstall 14.04 a couple of months ago?  14.04 is pretty stable.  What were your initial symptoms that made you reinstall the first time?

It could also be a disk problem.  What is the SMART status of the disk:

```
sudo smartctl -a /dev/sda
```
I did an update to the machine about a year ago and for some reason after that it wouldn't boot into the new kernel, it just kept dropping to busybox. I had to manually select the old kernel from the Grub menu any time I wanted to reboot so I had to reinstall in order to move the server off site to an unmanaged location. That way I could reboot whenever I wanted without having to manually interact with it.

```
user@xxxxx-server:~$ sudo smartctl -a /dev/sda
[sudo] password for user: 
sudo: smartctl: command not found

```

> **Jonathan L said:**
> Hi Maheriano

It's just a guess as I don't know anything specific about this model of server:  Many systems have a BIOS option to ignore/complain about missing keyboards, often with beep codes to indicate the problem.  If it has a battery for configuration memory, perhaps that's run out (quite possible after three years) and it got its BIOS configuration in a mess.  So I'd check and perhaps replace the battery, and check the BIOS configuration screens.

Hope that's of some use.

Kind regards,
Jonathan.
I've checked the BIOS all the way through, there is a warning for an opened chassis but I turned that off. I don't see any other warnings anywhere.

---

