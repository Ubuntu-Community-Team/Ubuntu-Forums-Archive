---
title: "[SOLVED] /var/spool/cups retains files after printing"
date: 2008-10-09
forum: Server Platforms
---

### Post by cmnorton on 2008-10-09
After my terminal emulator prints a screen, I look at the /var/spool/cups directory and see files still sitting there. What settings do I need to change in configuration to have these files be deleted after the print job is complete?

Edit:
----------------
This is solved. I found
[http://ubuntuforums.org/showthread.php?t=87675](http://ubuntuforums.org/showthread.php?t=87675)

Here are some things to bear in mind:

1) cupsd.config is now called cupsd.conf, 

2) PreserveJobHistory No is not in my 8.04 cups.conf; it had to be added.

---

