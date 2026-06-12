---
title: "Black screen after upgrade 16.04 to 17.10"
date: 2018-05-14
forum: Virtualisation
---

### Post by hawaii243 on 2018-05-14
title is wrong ---- upgraded from 16.04 to Ubuntu 17.10


black screen after update / upgrade. everything was working fine prior. 


vmware... thought I created a snapshot before updating / upgrading. nope.


[https://image.ibb.co/cUZ66J/Clipboard_20180514_2.png](https://image.ibb.co/cUZ66J/Clipboard_20180514_2.png)

booted into recovery and added nouveau.modeset=0 


this did not work

so proceeded to:

root (drop to root shell)
mount -o remout,rw /
mount --all


sudo nano /etc/default/grub
and then add nomodeset to GRUB_CMDLINE_LINUX_DEFAULT:


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""
And then save by hitting Ctrl+O, then exit nano with Ctrl+X, then:

sudo update-grub

[https://preview.ibb.co/kB1BOy/Clipboard_20180514_01.png](https://preview.ibb.co/kB1BOy/Clipboard_20180514_01.png)

after this I rebooted and the following displays:

Ubuntu 17.10 . . . . . splash screen
Then: orange cursor upper left corner
Then: black screen 
Then: wait .... a long time .... nothing.

[https://ibb.co/bxyYmJ](https://ibb.co/bxyYmJ)

ran failsafe graphics and selected all the defaults, still a black screen.

[https://ibb.co/j9BxDy](https://ibb.co/j9BxDy)

---

### Post by hawaii243 on 2018-05-30
so no one has any experience with an issue like this?

---

### Post by wildmanne39 on 2018-05-30
*Thread moved to **Virtualisation for a more appropriate fit**.*

Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

If you do not receive a reply you can bump your thread once every twelve hours to keep it in view, otherwise the thread may get overlooked.

---

### Post by hawaii243 on 2018-06-11
nbump

---

### Post by KillerKelvUK on 2018-06-12
Drop the "quiet" and "splash" from the grub defaults and see if you can see from the kernel output on boot where it's getting stuck?

---

### Post by sp40140 on 2018-06-13
I am bit confused
What are the specs of host? what are the resources of guest?
Are you having issue with guest or host?
What version of vmware are you using?

---

