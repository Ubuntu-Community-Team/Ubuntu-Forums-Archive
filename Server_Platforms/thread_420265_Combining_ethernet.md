---
title: "Combining ethernet"
date: 2007-04-23
forum: Server Platforms
---

### Post by grogoreo on 2007-04-23
Hi

Has anyone managed to combine more than one Ethernet into one device with, for example, two Gb sockets making a 2Gb stream?

Firehose ([http://heroinewarrior.com/firehose.php3](http://heroinewarrior.com/firehose.php3)) does this but it is separate from the rest of the system. Would it be feasible "implement a TCP layer over multiple devices" with something like this?

Thanks,
Greg

---

### Post by prodsacnetworking on 2007-04-23
[http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)

It's called Trunking or Bonding.
After, you have to trunk on your switch too.

---

### Post by grogoreo on 2007-04-24
That's great, thanks for the link prodsacnetworking

---

