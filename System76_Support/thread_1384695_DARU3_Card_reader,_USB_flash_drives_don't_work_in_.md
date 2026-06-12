---
title: "DARU3 Card reader, USB flash drives don't work in Mint 8 (Karmic)"
date: 2010-01-18
forum: System76 Support
---

### Post by Murrquan on 2010-01-18
Okay, this one's weird ...

I'm using a DARU3 Darter Ultra. I *was* using Mint 7 (based on Jaunty), and it worked fine.

I've tried out both Mint 8 and Karmic now. On the LiveCDs, they recognize my SD card reader and USB flash drive; these things automatically mount as soon as I plug them in. Once the distro's installed to my hard drive, however, neither work. (The sound also cuts out after a little while, and I have no idea why.)

What information is needed to troubleshoot this, and/or what can I do to solve it?

---

### Post by Murrquan on 2010-01-18
BUMPing this with the note that I've installed Karmic itself now and they still don't work.

---

### Post by thomasaaron on 2010-01-19
Good. We're not set up to test with and trouble-shoot Mint. While I realize it is virtually the same as Ubuntu, the System76 Driver won't work on it without a through hacking -- which is a service we do not currently provide.

Please install and run the System76 Driver (Install tab and Install button). Reboot afterwards.

Once that's done, try a different SD card and a different USB flash drive.

If they still don't work, remove them. Then, please open a terminal and run this command...

tail -f /var/log/syslog

Insert the USB flash drive and record the output from the terminal.
Then remove the flash drive.

Insert the SD card and record the output from the terminal.

Let me know the output for each.

---

