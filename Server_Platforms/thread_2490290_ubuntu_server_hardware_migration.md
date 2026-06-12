---
title: "ubuntu server hardware migration"
date: 2023-08-29
forum: Server Platforms
---

### Post by josh60 on 2023-08-29
[COLOR=#232629][FONT=-apple-system]I am trying to move my server ssd to a new computer and all I get is a blinking cursor. I have tried holding down ****, shift e, doing ctrl alt f1-f8, tried esc and but nothing happens.[/FONT][/COLOR]

---

### Post by TheFu on 2023-08-29
When you boot into a "try ubuntu" environment and connect the older SSD, does the OS see it at all?  Does the BIOS see it?  Sometimes, newer hardware needs updated firmware from the SSD to be compatible.  Be 100% certain you have a complete, know-you-can-restore, backup of any data on the disk you don't want to loose BEFORE any firmware update.

BTW, for troubleshooting things that worked and not don't work, it is helpful so compare the old hardware and the new hardware. So, what's different?  Almost certainly there is a different disk controller. What else?  Was there any proprietary GPU drivers or RAID in the old system that you forgot to remove?

---

