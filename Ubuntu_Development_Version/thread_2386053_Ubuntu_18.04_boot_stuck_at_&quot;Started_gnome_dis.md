---
title: "Ubuntu 18.04 boot stuck at &quot;Started gnome display manager....."
date: 2018-02-28
forum: Ubuntu Development Version
---

### Post by cmseuk on 2018-02-28
[h=2]Ubuntu 18.04 boot stuck at "Started gnome display manager.....[/h][COLOR=#000000][INDENT]Ubuntu updates broke my system. So I reinstalled it. Now its been fine for one day, but an update today is causing a boot failure. **"Started gnome display manager.....service link was shutdown.**


When the system boots the boot messages flash on and off the screen when I bring up the virtual console. meaning I have to wait upto 5 mins to even login to the console.

I have tried reinstalling gdm3, xserver, ubuntu desktop, switching kernels. I've purged the nvidia driver and I am now using the default display driver.

Please help.[/INDENT]
[/COLOR]

---

### Post by crcarson on 2018-02-28
Saw the same problem on my laptop after yesterdays updates that included Nvidia driver.  Going to install 18.04 2/27/18 daily build without Nvidia.

---

### Post by fthx on 2018-02-28
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053)

---

### Post by cmseuk on 2018-02-28
Doesn't help unfortunately. I have those libs installed already and there is nothing nvidia in the system anymore.

---

### Post by cmseuk on 2018-02-28
I upgraded to proposed and the issue is fixed

---

### Post by ajgreeny on 2018-02-28
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by fthx on 2018-02-28
Considering [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1752053) it may be useful to stick a warning against Nvidia 390 in this dev section of the forum ?

---

