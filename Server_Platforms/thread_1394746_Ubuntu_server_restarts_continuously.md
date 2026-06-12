---
title: "Ubuntu server restarts continuously"
date: 2010-01-31
forum: Server Platforms
---

### Post by DrIdiot on 2010-01-31
We're running an Ubuntu server (the version we installed was Jaunty).  Recently, I updated the kernel to the latest version and also installed Ruby and the Passenger module for Apache.  The server was fine for a few days.  However, today, it's been restarting randomly (usually a minute after I can log in).  I tried booting with recover mode so I could view the logs for a longer period of time, but that caused it to restart before even allowing me to log in.  Now, all boot modes will just cause the server to restart right after the GRUB messages appear.

Our server setup complicates things.  We have a RAID-1 mirroring for the /boot partition and a RAID-5 (software) for the / partition.

How can I troubleshoot this?  Does anyone have any idea what the issue is?  Is there any way I can back up the data we have?

Thanks.

---

### Post by DrIdiot on 2010-01-31
Okay, for some reason it's the operating system is booting now.  However, it still randomly restarts (crashes?)

I can't find anything similar to:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
that deals with non-X related issues (since the server is not running X it can't be causing the problems)

I did a memory test and it came back fine.

Any thoughts?

---

