---
title: "turning off ubuntu server by pressing power off"
date: 2009-01-18
forum: Server Platforms
---

### Post by angelochen960 on 2009-01-18
Hi,
i used to install ubuntu 6 or 7 server in an old Compaq P3, pressing the power button will automatically shutdown the ubuntu server. I just installed the 8.10 server in the same machine, but I can't shut it down any more by pressing power button, I have to login, sudo shutdown -h 0
any idea? thanks.

Angelo

---

### Post by angelochen960 on 2009-01-18
i have changed from acpi to apm and now, when the power button is pressed, the machine shuts down without going thru the shutting down process. I remember it was working in version 6 or 7. the reason why I want to do this is, the machine does not have a keyboard and monitor, and now I have to ssh first and issue: shutdown -h 0
. will be glad if anybody can help. thanks.

Angelo

---

