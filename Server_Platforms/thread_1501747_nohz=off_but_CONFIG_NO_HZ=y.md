---
title: "nohz=off but CONFIG_NO_HZ=y"
date: 2010-06-04
forum: Server Platforms
---

### Post by MattFS218 on 2010-06-04
I'm trying to disable tickless kernel on my Ubuntu server (10.4 64-bit). I've added the nohz=off to my grub kernel boot options, but when I look inside /boot/config-2.6.32-21-server CONFIG_NO_HZ is still being set to y.

Is this normal? or did I forget a configuration step somewhere? I ran update-grub and the kernel parm is showing up in /var/log/messages. Is there anyway to test to see if the loaded kernel is tickless or not? Thanks.

--matt
[Hosted VoIP]("http://www.hellohunter.com")

---

