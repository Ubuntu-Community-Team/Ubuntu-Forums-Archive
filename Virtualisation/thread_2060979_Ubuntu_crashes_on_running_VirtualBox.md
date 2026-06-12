---
title: "Ubuntu crashes on running VirtualBox"
date: 2012-09-21
forum: Virtualisation
---

### Post by kwanylongy on 2012-09-21
Hi all,

I am on Ubuntu 12.04. I just started using virtualbox at work (on win7) and now I wish to run virtualbox on my home PC (running Ubuntu). However, my computer crashes every time when I start running a guest OS using VirtualBox. Anyone knows how to fix it? Please indicate what information I need to provide in order to get this problem fixed since I'm pretty much a n00b...

EDIT: The version of my VirtualBox on Ubuntu is 4.1.12_Ubuntur77245

Many thanks!  :-P

---

### Post by daslinkard on 2012-09-21
I'm going to start with this for you to try: 

[LIST=1]
[*]open a terminal window
[*]type "sudo gedit /etc/default/grub" (without the quotes) and press enter
[*]Comment out the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" by adding a "#" character in front.
[*]Add new line below: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nmi_watchdog=0 nowatchdog"
[*]Save and exit
[*]type "sudo update-grub" (without the quotes) and press enter
[*]reboot.
[/LIST]
The potential workarounds can be found [here]("https://forums.virtualbox.org/viewtopic.php?f=7&t=50009").

---

### Post by jerrrys on 2012-09-21
How did you install it?  What installation document did you follow?  And what are your computer specifications?

[https://www.virtualbox.org/manual/ch02.html#idp14255536](https://www.virtualbox.org/manual/ch02.html#idp14255536)

---

### Post by kwanylongy on 2012-10-01
> **daslinkard said:**
> I'm going to start with this for you to try: 

[LIST=1]
[*]open a terminal window
[*]type "sudo gedit /etc/default/grub" (without the quotes) and press enter
[*]Comment out the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" by adding a "#" character in front.
[*]Add new line below: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nmi_watchdog=0 nowatchdog"
[*]Save and exit
[*]type "sudo update-grub" (without the quotes) and press enter
[*]reboot.
[/LIST]
The potential workarounds can be found [here]("https://forums.virtualbox.org/viewtopic.php?f=7&t=50009").

Daslinkard,

Thank you so much for your help and sorry for my late reply. I forgot to subscribe to this thread and so thought nobody had replied

I tried the steps you suggested, but with no luck. I'll read the workaround your posted and post the results here later.

---

### Post by Stonecold1995 on 2012-10-01
How much RAM do you have, and how much RAM have you given the guest OS?  VirtualBox requires a lot of RAM, and your computer may crash if the RAM runs out.

---

### Post by kwanylongy on 2012-10-07
> **Stonecold1995 said:**
> How much RAM do you have, and how much RAM have you given the guest OS?  VirtualBox requires a lot of RAM, and your computer may crash if the RAM runs out.

4GB, and I have only assigned 1GB to my VirtualBox GuestOS, so I don't think that is the problem.

Thanks!

---

### Post by nothingspecial on 2012-10-08
*Thread moved to **Virtualisation**.*

---

