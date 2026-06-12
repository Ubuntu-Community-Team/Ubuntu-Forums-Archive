---
title: "Sending patches from the System76 driver upstream"
date: 2012-10-20
forum: System76 Support
---

### Post by Carborundum on 2012-10-20
The latest version of the System76 driver (3.2.1) claims to do the following:
> Fix race condition causing the Ubuntu login screen to not show on occasionWhich is great! I used to have this problem earlier, but it hasn't happened since I upgraded the driver.

However, I still occasionally see people with non-System76 computers affected by (what appears to be) the same problem, for example LP bugs [#1066410]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1066410") and [#1009303]("https://bugs.launchpad.net/lightdm/+bug/1009303"). Does System76 have any policy to send patches such as this upstream, so they can benefit the entire community?

---

### Post by cprofitt on 2012-10-21
I believe this is just a modification that amounts to a work-a-round. If I am correct it modifes the /etc/init/lightdm.conf file by adding a sleep command.

---

