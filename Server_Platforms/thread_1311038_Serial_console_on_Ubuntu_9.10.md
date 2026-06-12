---
title: "Serial console on Ubuntu 9.10?"
date: 2009-11-02
forum: Server Platforms
---

### Post by LeoPanthera on 2009-11-02
Now that Ubuntu 9.10 does not, apparently, use grub anymore, how do I configure a console on the serial port?

---

### Post by TwiceOver on 2009-11-02
Karmic uses Grub2, you may want to start there.  The default file is now /etc/default/grub

Run sudo update-grub when done.

---

