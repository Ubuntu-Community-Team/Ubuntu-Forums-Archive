---
title: "Resolution in Xen Server instance of Ubuntu VM"
date: 2015-12-11
forum: Virtualisation
---

### Post by Zorrokan Zenovka on 2015-12-11
Hi

I've installed Ubuntu 14.04 in Xen Server and I'm having a little bit of trouble changing the screen resolution.

I have searched a few of the categories here at the Ubuntu forums and this seems the most appropriate, but let me know if there is a better place for this thread.

So far I have tried following this guide, however "Using x86 virtualization solution…. " at step 2 does not appear for me: [http://linuxbsdos.com/2014/10/31/solutions-for-low-screen-resolution-in-ubuntu-14-0414-10-and-virtualbox/](http://linuxbsdos.com/2014/10/31/solutions-for-low-screen-resolution-in-ubuntu-14-0414-10-and-virtualbox/)

And even though it's in a Windows 7 forum, I even tried this: [http://superuser.com/questions/826302/cant-use-1920x1080-resolution-on-xenserver-windows-7-guest](http://superuser.com/questions/826302/cant-use-1920x1080-resolution-on-xenserver-windows-7-guest)

From the ubuntu forums themselves I have tried the solution outlined in [http://askubuntu.com/questions/377937/how-to-set-a-custom-resolution](http://askubuntu.com/questions/377937/how-to-set-a-custom-resolution) but at the point where I am supposed to enter:
sudo xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
I get an error saying "xrandr: Failed to get size of gamma for output default".

Not sure where I'm going wrong.

Regards,


ZZ

---

### Post by Zorrokan Zenovka on 2015-12-11
Ok, slightly embaressing, the option to use a higher resolution does appear after a reboot due to one of the steps in [http://askubuntu.com/questions/377937/how-to-set-a-custom-resolution](http://askubuntu.com/questions/377937/how-to-set-a-custom-resolution) ... however it still doesn't fill the whole of my laptops monitor when 'viewing console' in the xen server management program.

---

