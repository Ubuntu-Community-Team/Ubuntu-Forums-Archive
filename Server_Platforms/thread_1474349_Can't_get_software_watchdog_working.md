---
title: "Can't get software watchdog working"
date: 2010-05-06
forum: Server Platforms
---

### Post by Robvdl on 2010-05-06
I need to use the software watchdog in the kernel, "softdog" for a project we are working on.  Here is what I have done so far:

 * I have modprobed softdog (also added it to /etc/modules)
 * I have commented out softdog in the blacklist (/etc/modprobe.d/blacklist-watchdog.conf)
 * The /dev/watchdog device is there, created at boot time and appears to never get kicked because the last modified/accessed datetime stamps are not changing (this is what I am expecting).

I am currently not running the watchdog daemon (on purpose), which runs a number of checks then kicks the dog, /dev/watchdog at intervals.

I would expect the computer to reboot after some time, but it isn't.  What am I doing wrong?  I expect the computer to eventually reboot unless the watchdog is kicked at intervals... this is what I want it to do.

(Oh, and another thing I even tried is compiling a kernel with the softdog compiled in rather than as a kernel module, but even this does not work, so I am completely lost now)

---

### Post by windependence on 2010-05-06
Why would you want the reboot? The only time a Linux machine needs rebooted is when there is a kernel update. I'm confused about what you are trying to accomplish. Can you explain?

-Tim

---

### Post by Robvdl on 2010-05-11
This is a requirement for work.  Basically we have a Vodafone 3G modem, and sometimes these modems go in a frozen state they won't get out of, and since they have no reset line the PC needs to be rebooted to get the modems going again.  At least this is what they told me at work.

They had an older embedded system with the same modem, running open embedded.  They used a hardware watchdog which they created themselves and connects to the parallel port.  They created their own watchdog daemon that did a number of tests such as check if the ppp and vpn are up, if everything is ok, the watchdog is kicked which keeps the PC running.  Any problems such as the modem in a frozen state and the watchdog is not kicked which results in the machine rebooting.

This is being replaced with a zotac mini itx machine running Ubuntu.  Now the problem is that newer machines do not have a parallel port anymore, so a software watchdog will need to be used instead.  Without the watchdog daemon running, the software watchdog won't get kicked and should eventually restart the PC, but it doesn't.

---

### Post by barillari on 2010-07-07
To force the software watchdog to reboot, you have to open the /dev/watchdog device and fail to write to it for the timeout period. This triggered it for me:

(as root)
# python
> d= open('/dev/watchdog','w')
> d.write('j')
> d.flush()
[wait 60 seconds]

---

