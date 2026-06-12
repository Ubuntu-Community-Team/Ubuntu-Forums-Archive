---
title: "Windows server 2016 VirtualBox - No text"
date: 2019-10-23
forum: Virtualisation
---

### Post by nibz-au on 2019-10-23
Hi all

im very new to ubuntu but am trying to setup windows server in Virtual box
when i install it, it works ok but then once i install the guest additions for full screen and it seems to run smoother, i lose text in server manager

Anyone know how this can be fixed? is it a ubuntu issue or VM issue maybe?

[IMG]https://imgur.com/MjpX6ug[/IMG][IMG]https://i.imgur.com/MjpX6ug.png[/IMG]

---

### Post by nibz-au on 2019-10-23
All sorted

I changed the graphic controller in Virtual Box and rebooted and it seems to work now.

---

### Post by lammert-nijhof on 2019-10-23
I had the same problem with the Virtualbox Guests: Windows 7, Ubuntu 16.04 and Ubuntu 19.10. I solved it by disabling 3D acceleration. Also changing Windows 7 to vgavbox did help, but I had the impression that the system was running slower with vgavbox. I created a bug report #19028 for Oracle. Somebody else had the same problem with Windows Vista and joined the bug report. Maybe you could do the same. In that case you have to add the screenshot (smaller than 500 KB) and the vbox.log file from a time of the error occurred.

---

