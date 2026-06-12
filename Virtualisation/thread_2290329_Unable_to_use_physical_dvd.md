---
title: "Unable to use physical dvd"
date: 2015-08-11
forum: Virtualisation
---

### Post by sublimestylelb on 2015-08-11
Hello, I'm trying to use a physical dvd for a new virtual machine on my ubuntu server.
Virtual Machine Manager say "could not find media /dev/sr0".
I am able to mount/umount the dvd via command line.
I don't know what to do.




[IMG]http://s9.postimg.org/fc3z35xsv/Capture_d_cran_2015_08_11_10_54_32.png[/IMG]





Thank You!

---

### Post by TheFu on 2015-08-12
Did you passthru the DVD device to the GuestOS?

VMs only see virtual hardware unless you go to great lengths to passthru the hardware.  If you just want to read the contents of a DVD, copy it off to an file.iso and use that instead.

---

