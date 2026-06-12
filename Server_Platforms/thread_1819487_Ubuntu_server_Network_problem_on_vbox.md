---
title: "Ubuntu server Network problem on vbox"
date: 2011-08-06
forum: Server Platforms
---

### Post by gouravgargg on 2011-08-06
[SIZE=3]Host Machine = Ubuntu 11.04

Guest Machine = Ubuntu 11.04

Now I copy to my guest OS image to anther Machine with Windows Server OS

When i trying to run the machine by adding my network card is not working
but it's working with host only not with Bridging Network
[/SIZE][SIZE=3][COLOR=Red]

SIOCSIFADDR: no such device

Failed to bring up ethX[/COLOR][/SIZE][SIZE=3]

by removing this file and after reboot i am getting same error 
 */etc/udev/rules.d/70-persistent-net.rules*[/SIZE]

---

