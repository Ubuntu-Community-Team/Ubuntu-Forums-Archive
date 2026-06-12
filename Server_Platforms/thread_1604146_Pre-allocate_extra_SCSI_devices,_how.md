---
title: "Pre-allocate extra SCSI devices, how?"
date: 2010-10-23
forum: Server Platforms
---

### Post by pneumatic on 2010-10-23
So I have a Supermicro 36 bay server and I would like to start small and add drives as my needs increase.  The only issue is this:

[http://tldp.org/HOWTO/archived/SCSI-Programming-HOWTO/SCSI-Programming-HOWTO-4.html](http://tldp.org/HOWTO/archived/SCSI-Programming-HOWTO/SCSI-Programming-HOWTO-4.html)

> When adding more devices to the scsi bus keep in mind there are limited spare entries for new devices. The memory has been allocated at boot time and has room for 2 more devices.

I need room for an extra 20 devices.  How do I configure this?

---

### Post by psusi on 2010-10-23
That information is wrong/outdated.  Ignore.

---

### Post by pneumatic on 2010-10-23
I'm having an issue whereby hotplugged drives are not detected.  I found some documentation on rescanning the SCSI bus so I will try that.  I'm just not certain why device autodetection just stops.  Everything works after a reboot so I know that they are working.

I'll try the rescan and see what happens.

---

