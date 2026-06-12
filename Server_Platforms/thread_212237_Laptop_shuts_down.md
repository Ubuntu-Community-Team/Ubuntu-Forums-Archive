---
title: "Laptop shuts down"
date: 2006-07-09
forum: Server Platforms
---

### Post by Paddo on 2006-07-09
Hi, I have recently installed a LAMP server on an old laptop so I can learn a bit about web servers. It has all gone well and I have the web server up and running.
Now I am at the point of putting the laptop out of sight and leaving it running, hosting my own page. I now have a problem... if I don't log in, the laptop shuts itself down after a few minutes. This is obviously not good for a server. Can anyone let me know how to keep the laptop running?

Thanks.

---

### Post by lamego on 2006-07-09
It could be related to the power savint options, turn of acpi.
Todo so add the "acpi=off" to the kernel params in the '/boot/grub/menu.lst'.
Be aware to also add it to the "# defoptions=..." line.

---

### Post by Paddo on 2006-07-10
Thanks. Looks like that has done the trick - it's still running.

---

