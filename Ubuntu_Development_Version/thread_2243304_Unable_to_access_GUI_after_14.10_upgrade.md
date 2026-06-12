---
title: "Unable to access GUI after 14.10 upgrade"
date: 2014-09-07
forum: Ubuntu Development Version
---

### Post by m-chabot on 2014-09-07
Hi everyone,

I usually upgrade to "beta" versions without any major problem, but this time, I can't find the fix.

Did an "update-manager -d" and after doing and rebooting, I'm stuck at terminal mode which I can login but receive this message:

systemd-logind: Failed to start user service [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e

If I try to enter GUI by typing "startx" I get to the GUI but no menu on the left (as it should be) and no way to resize or close windows, etc...

Please help.

---

### Post by EuclideanCoffee on 2014-09-07
I found Debian users talking about this problem.
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756247](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756247)

It looks like it will be a common problem with the next move. Whenever you upgrade, you risk breaking something. You can try to recover your data with a Live Ubuntu and then reinstall Ubuntu 14.10.

Good luck.

---

### Post by micha2358 on 2014-10-11
I have exactly the same problem. Yes, there is a discussion about the problem behin your link, but I don't see any solutions there.
Has anyone solved the problem yet?

---

### Post by n-fit-8 on 2014-10-11
[COLOR=#000000]> [/COLOR][COLOR=#000000] lsystemd-logind: Failed to start user service [/COLOR][EMAIL="user@1000.servic"]user@1000.servic[/EMAIL][COLOR=#000000]e[/COLOR][COLOR=#000000]
i use ubuntu 14.10 and this is reported every time i log in and my system boots normally.

what gpu are you[/COLOR] using?

---

### Post by micha2358 on 2014-10-13
There is a workaround to use systemd managmement daemon instead of upstart but I still get a black screen at booting. I guess it is a graphics driver issue (I have AMD). 
Can somebody tell me how to change the graphics driver from fglrx (proprietary) to fglrx-updates (proprietary) or to driver wrapper from xserver-xorg-video-ati (for test puropose) in terminal mode?

---

### Post by n-fit-8 on 2014-10-13
sudo apt-get purge fglrx*
sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
sudo apt-get install fglrx-updates*

---

### Post by micha2358 on 2014-10-18
Thanks, that helped.

---

