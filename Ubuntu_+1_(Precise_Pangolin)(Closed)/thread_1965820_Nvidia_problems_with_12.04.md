---
title: "Nvidia problems with 12.04"
date: 2012-04-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by geovino on 2012-04-26
Just install 12.04. 

It wanted to install the Nvidia drivers (geforce 6100) like in the past. This time after install the log in screen comes up I log in then the screen goes black! I've had trouble with Nvidia drivers for the past five years and its always the same. 

How do I just use the generic drivers that come with Ubuntu and forget about Nvidia altogether? 

I'll have to reinstall 12.04 and just ignore the driver pop up. Maybe the Ubuntu logo will show up on start up and shut down like it should. I'm sick of proprietory drivers! They are nothing but trouble.

---

### Post by ubuntu27 on 2012-04-26
Open Dash by pressing the Super (or Windows) button, and type "driver"

Open "Additional Driver"



Another way to do this is to go to

System Settings------> Additional Drivers




Then select the driver that you want to remove, and click "Remove"

---

### Post by lovinglinux on 2012-04-26
When you see the log in screen, hit CTRL+ALT+F2, enter your login name and password, then run these commands in the terminal:


```
sudo apt-get purge nvidia*
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by geovino on 2012-04-26
> **lovinglinux said:**
> When you see the log in screen, hit CTRL+ALT+F2, enter your login name and password, then run these commands in the terminal:


```
sudo apt-get purge nvidia*
sudo dpkg-reconfigure -phigh xserver-xorg
```

What will that do?

After reinstalling 12.04 and ignoring the additional drivers, all is well. Would like nvidia dirvers to work, but they have a bad track record. I'm willing to try though.

---

### Post by ubuntu27 on 2012-04-26
> **lovinglinux said:**
> When you see the log in screen, hit CTRL+ALT+F2, enter your login name and password, then run these commands in the terminal:


```
sudo apt-get purge nvidia*
sudo dpkg-reconfigure -phigh xserver-xorg
```


> **geovino said:**
> What will that do?

After reinstalling 12.04 and ignoring the additional drivers, all is well. Would like nvidia dirvers to work, but they have a bad track record. I'm willing to try though.

Hi Geovino. You do not need to that what LovingLinux said anymore since you reinstalled Ubuntu 12.04 without Nvidia driver.

That command removes any packages that are nvidia related.

---

### Post by coffeecat on 2012-04-26
> **geovino said:**
> What will that do?

For future reference, you didn't need to re-install. Those commands were for removing the proprietary nvidia driver from your system when you are unable to log into the GUI. I had to do something similar a few days ago - I too was confronted with a black screen with the nvidia driver, but uninstalling the driver from the CLI and then rebooting soon had me back with a GUI.

And then I replaced the nvidia card with an AMD card, and I've been happy since. :)

---

### Post by geovino on 2012-04-26
> **coffeecat said:**
> For future reference, you didn't need to re-install. Those commands were for removing the proprietary nvidia driver from your system when you are unable to log into the GUI. I had to do something similar a few days ago - I too was confronted with a black screen with the nvidia driver, but uninstalling the driver from the CLI and then rebooting soon had me back with a GUI.

And then I replaced the nvidia card with an AMD card, and I've been happy since. :)

Thanks, I'll live without Nvidia for now, and maybe install another video card, but I have 3 other hard drives on this PC with Debian 6, Fedora 16, and Windows 7. Debian and Fedora have always had trouble Nvidia and I gave up with them and Nvidia a long time ago. I like Ubuntu the best overall. What would you suggest if I look for another video card?

---

### Post by KozaG on 2012-04-26
I shall continue here with another problem of NVIDIA Graphic drivers. When I use *Additional Drivers* and choose any of those two options I get same problem. After reboot everything, except wallpaper, (Unity bar, other bars, all windows) goes slightly blur and starts vibrating one pixel up and down.

Because of this I'm forced to work without NVIDIA Graphic Drivers. Not very nice. Back when I was using Ubuntu 10.10, 11.04 or Mint 11 I didn't had any problems like this.

I have NVIDIA GeForce 7900 and Ubuntu 12.04 64 bit.

Anyone knows solution for this?

---

### Post by VMC on 2012-04-26
Here's the problem with nvidia cards:
[http://www.nvnews.net/vbulletin/showthread.php?t=178460](http://www.nvnews.net/vbulletin/showthread.php?t=178460)

---

### Post by grahammechanical on 2012-04-26
With 12.04 when we tick install restricted extras as part of the install we also get the proprietary video driver installed as well.

If we do not tick to install restricted extras, then the open source driver should be activated.

We might then be able to use Synaptic (not installed by default) to activate an older Nvidia driver that does not do this kind of thing.

Regards.

---

