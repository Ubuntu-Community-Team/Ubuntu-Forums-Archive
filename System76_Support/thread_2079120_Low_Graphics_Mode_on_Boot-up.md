---
title: "Low Graphics Mode on Boot-up"
date: 2012-11-01
forum: System76 Support
---

### Post by MoebusNet on 2012-11-01
I've had this problem before, but this is now occurring every morning. On the first boot-up of the day, the computer starts, begins showing the splash screen then suddenly changes to a black screen. This is followed by a window saying that I am running in Low Graphics Mode. The window offers 4 choices, none of which are available because the trackpad is non-functional.

Because I've been through this before [http://ubuntuforums.org/showthread.php?t=2035818](http://ubuntuforums.org/showthread.php?t=2035818)
I attempt
```
sudo rm -v /etc/X11/xorg.conf
```
I always get a message saying there is no such file.
```
sudo reboot
```
which brings me to a console boot-up. Then I try
```
sudo service lightdm --full-restart
```
which get me to a desktop. Unfortunately, about half of the time I am unable to log in as my username, but only as guest. I fix this with
```
sudo chown -R $USER:$USER $HOME
```
which sometimes starts the entire cycle over.

The next morning, I go through this again. Is there some way I can fix this? What information can I provide?

---

### Post by MoebusNet on 2012-11-01
Additional information:

This afternoon I booted up my notebook again. Again it booted into Low Graphics Mode with the trackpad unresponsive, so this time I went straight to Crl-Alt-F1 ```
sudo service lightdm --full-restart
``` which brought me to a login screen that worked properly. That hasn't always been the case.

---

### Post by isantop on 2012-11-02
Go ahead and make sure your system is fully up to date. If you still experience the issue, use the restore process in the latest System76 Driver to fix the problem.

---

### Post by MoebusNet on 2012-11-02
Thanks, isantop. I'm in the habit of installing updates as soon as they become available, so when I read your reply I found about 6 updates since yesterday. After installing them, I am getting a normal boot to desktop now although none of the updates appeared to affect the X system or Nvidia's driver. Puzzling to be sure; this is the first experience I've had with updates borking the desktop GUI then fixing them as a repeated occurrence.

Maybe this is why Linus got so upset with Nvidia, eh?

I'll go ahead and mark this "Solved" (fingers crossed).

---

