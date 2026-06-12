---
title: "asrock q1900-itx booting with vga but not without"
date: 2015-02-11
forum: Server Platforms
---

### Post by Frozen Forest on 2015-02-11
I recently installed Ubuntu server 14.04.1 64bit on a system with Asrock q1900-itx (latest BIOS), the installation went fine but a odd problem has occurred. When booting and not having keyboard or monitor (VGA) connected does the boot stall, the system is up but not getting any IP address through DHCP and clicking the tower button turns it off eminently. When booting again, this time with VGA connected, does the system start without issue.

What might be causing this?
How do I debug it? Connecting a monitor make it work as normal!
Which log might have the answer?
Might it be a configuration in BIOS?

---

### Post by volkswagner on 2015-02-11
[This thread]("http://ubuntuforums.org/showthread.php?t=2263100") has some Grub suggestions.

Unfortunately they didn't help the other poster, but I thought it may be a good idea to link the threads.
There's also a link to a ~$12 fake video device.

Yes you'll want to make sure the BIOS is set to ignore keyboard and other errors.

---

### Post by cariboo on 2015-02-11
> **volkswagner said:**
> Yes you'll want to make sure the BIOS is set to ignore keyboard and other errors.

+1 that's usually the problem.

---

