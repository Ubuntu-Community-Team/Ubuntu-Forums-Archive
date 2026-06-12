---
title: "Ubuntu 9.1: mouse, keyboard grabbing not working in the whole screen"
date: 2009-11-06
forum: Virtualisation
---

### Post by FrankA on 2009-11-06
I have the following issue since I upgraded from Ubuntu 9.04 to Version 9.1
I'm using vmware server 2.01. If I open my virtual windows 2003 machines the mouse grapping is only working in the left hand upper area of the screen in the virtual machine.
Therefore I'm only able to grab mouse and keyboard in the upper left quarter of the screen. If I moved the mouse in another area of the screen, mouse and keyboard are getting released and the mouse arow is changing to a hand icon. The vmware tools are uptodate, a new installation of the vm tools has not solved the issue. I tried also different screen resolutions

---

### Post by FrankA on 2009-11-08
Found a temporary solution, by starting firefox with command 
"sudo VMWARE_USE_SHIPPED_GTK=yes firefox"

references for problem solution:
[http://ubuntuforums.org/showthread.php?t=1298781](http://ubuntuforums.org/showthread.php?t=1298781)
[http://shellack.de/info/content/vmware-server-20-console-failur](http://shellack.de/info/content/vmware-server-20-console-failur)

---

