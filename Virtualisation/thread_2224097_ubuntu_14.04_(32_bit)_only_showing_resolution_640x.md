---
title: "ubuntu 14.04 (32 bit) only showing resolution 640x480 (minimum, current, maximum)"
date: 2014-05-14
forum: Virtualisation
---

### Post by Prosanta on 2014-05-14
Hi,

I am having host OS Windows 7. I install ubuntu 14.04 (32 bit) recently with virtualbox 4.3 .ubuntu 14.04 (32 bit) only showing resolution 640x480 (minimum, current, maximum). My laptop is having Intel HD Graphics (HP pavilion dv5). It best resolution is 1366x768, windows 7 is running at that resolution. Please help me out to rectify these issue.

---

### Post by TheFu on 2014-05-14
Have you loaded the guest additions?

---

### Post by Prosanta on 2014-05-16
It is "ubuntu-14.04-desktop-i386",
virtual box edition   "VirtualBox-4.3.10-93012-Win"

---

### Post by TheFu on 2014-05-16
So ... did you load the guest additions?

---

### Post by Prosanta on 2014-05-17
No its not a guest edition....

---

### Post by plucky on 2014-05-17
> So ... did you load the guest additions? 

> No its not a guest edition.... 

Guest Additions (VboxAdditions) is built into Virtualbox. You normally have to reload Guest Additions after a kernel update.

Right click on the CD icon in the launcher. If there is no CD icon,open Devices > "Insert Guest Additions CD Image" to place the Cd image onto the launcher.

Good Luck

---

### Post by TheFu on 2014-05-17
> **Prosanta said:**
> No its not a guest edition....

Guest additions make the user experience better - specifically for the video, keyboard and mouse integration, but also for USB passthru and to access hostOS shared drives. YOU WANT THESE LOADED inside every guestOS you can get them into.
[https://forums.virtualbox.org/viewtopic.php?t=15679](https://forums.virtualbox.org/viewtopic.php?t=15679)

---

### Post by Elfy on 2014-05-17
*Thread moved to **Virtualisation**.*

---

### Post by Prosanta on 2014-05-21
Thanks
Problem is resolved after loading guest edition.

But it is acting very slow now. When I type something on terminal, it is taking 2-3 sec to appear on the screen.
In my system config is core i3 cpu m330  @2.13Ghz, 3GB RAM, Win 7 OS.

---

