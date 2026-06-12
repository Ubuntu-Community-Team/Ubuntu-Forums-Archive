---
title: "How do I get wake on lan to work?"
date: 2009-04-18
forum: Server Platforms
---

### Post by c3lica on 2009-04-18
I have a ASUS P5QL PRO mobo and can not seem to get wake on lan working. There does not seem to be any way to enable wake on lan via bios so it must be on all the time. when I called asus they said it would have to do with setting up the os correctly but the guy i talked to didn't know anything about linux.

I did this 
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
and it did not work. 

Any idea on what I should do?

EDIT: I am running ubuntu server 8.10

EDIT #2:
I installed acpi-support ```
sudo apt-get install acpi-support
```

Then did step one here.
[http://linux-tipps.blogspot.com/2008/11/fixing-wake-on-lan-in-ubuntu-810.html](http://linux-tipps.blogspot.com/2008/11/fixing-wake-on-lan-in-ubuntu-810.html)

That seems to work well.

---

### Post by FarehamWeather on 2009-04-19
I have done it and it works, ubunu server did not need configuring just the bios settings.

make sure use the the ip and mac address of the machine, try different software.

---

### Post by Iowan on 2009-04-19
I found a help page for [etherwake]("http://manpages.ubuntu.com/manpages/hardy/man8/etherwake.8.html"), but it seems to be the other side of the coin.

---

### Post by theDaveTheRave on 2009-04-22
> **FarehamWeather said:**
> I have done it and it works, ubunu server did not need configuring just the bios settings.

make sure use the the ip and mac address of the machine, try different software.

A little more instruction would be really great?

do you have a link to a how to?

How do you wake the Server from another pc? how to do it from windows or another Linux would be helpfull....

I know that this may sound like a bunch of rather silly questions, so appologies for that.

Thanks.

C3lica, you got this working....

did you just do the steps in the initial howto and then the first step in your second link?

Again sorry if I'm being dense.....


David

---

