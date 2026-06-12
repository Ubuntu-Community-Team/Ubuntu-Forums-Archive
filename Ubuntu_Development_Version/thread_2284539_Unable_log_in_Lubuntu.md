---
title: "Unable log in Lubuntu"
date: 2015-06-30
forum: Ubuntu Development Version
---

### Post by fillip1 on 2015-06-30
I can't log-in to Lubuntu enviroment on Lubuntu 15.10.
When i try to log-in massage from log-out is shoved and then I'm back on login screen.
Now I'm loged in LXDE. I try instal Xfce but it have same error.


[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1450785](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1450785)

---

### Post by sudodus on 2015-06-30
Welcome to the Ubuntu Forums :-)

Please realize that Lubuntu 15.10 is not yet released. It is in a heavy development phase, has just passed the alpha 1 milestone. You are welcome to help testing it. If that is what you want, I (or some other moderator) can move your thread to the [Ubuntu Development Version](http://ubuntuforums.org/forumdisplay.php?f=427) subforum. See also this link [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

Otherwise, if you want a stable Lubuntu version, I would recommend Lubuntu 14.04.2 LTS that is well debugged and polished.

---

### Post by fillip1 on 2015-06-30
These error is appeard first on 15.04, I upgrade besides to fix it.

But I can try downgrade to 14.04. if is here some easy way (= not clean install required).

---

### Post by Bucky Ball on 2015-06-30
Only way is a clean install required. Not wise to install a testing release unless you know your way around and are willing to test and put up with breakage. Also, unless it is a specific driver that is lacking in an older release, upgrading to a new release to fix an issue generally has about a 99% chance of not fixing anything. The original problem usually remains.

Installing 15.10 may have given you a whole set of new ones. If you want to continue trying to fix 15.10, though, it will be a nice learning curve and I will move this thread to the appropriate forum section. Good luck, whichever way you go. :)

---

### Post by sudodus on 2015-06-30
Unfortunately there is not easy way to downgrade. The best way is to save the personal files and settings by backing up the home directory, and make a fresh install. After that you restore the home directory from the backup. (You can also create a separate home partition.)

If you have added a few program packages, re-install them. If you have a lot of added program packages, there are ways to keep track of them (I don't know the details, but other people at these Ubuntu Forums know).

---

### Post by ajgreeny on 2015-06-30
This sort of loop around the login screen can sometimes occur when the permissions of folders and files in your home are incorrect for some reason.

At the login screen use Ctrl+Alt+F1 to get to a command-line and login there.  Type your username which will show on screen, then when asked type your password; nothing will show on screen at this point but don't worry, it is still being entered.

If that gets you to a login as I expect it may, use command ```
ls -la | grep root
``` which will show you if any of your files or folders are owned by root.  If all is as it should be there will be only one line of output which ends with two points, eg
```
drwxr-xr-x  4 root   root        4096 Apr 26 14:55 ..
```

---

### Post by fillip1 on 2015-06-30
It seems folder permission is correct.
grep output:
drwxr-xr-x  4 root root   4096 &#269;en 16 09:39 ..

---

### Post by Bucky Ball on 2015-06-30
*Thread moved to **Ubuntu Development Version**.*

---

### Post by grahammechanical on 2015-06-30
Do you have more than one keyboard layout installed? I do. I have both English and Greek keyboard layouts. That does not mean I know Greek. So, please do not assume that I do.

I does mean that from time to time my login password gets rejected because when I shut down Ubuntu I was using the Greek keyboard layout and that same layout was active at the login screen. Sometimes it takes me a few minutes to workout why I had the problem.

Oh, by the way. When we are running the development version it is always best to be prepared to re-install. There are only 2 times when I will upgrade to the development version. At the very beginning of the 26 week development period and at the very end of the development period. During the 4 months in between I will always put in a fresh install. The code differences between 15.04 and 15.10 under construction are by now so great, in my opinion, that I would not risk an upgrade failing in some way.

If you can login to some kind of working desktop, then use that and update the system daily and this problem might get fixed along the way. It is how I live with the development version.

Regards.

---

### Post by fillip1 on 2015-06-30
I have got more keyboard layouts (I was experimenting with esperanto.) but I think these is not related to password rejection because I can log in LXDE enviroment.

---

### Post by ventrical on 2015-06-30
Lubuntu 15.10 is the 5 minute (USB ver2.0) install :). Todays current went exceptionally well. Only plymouthd bug but that is in xubuntu also.

```

ventrical@ventrical-MS-7850:~$ systemd-analyze
Startup finished in 916ms (kernel) + 8.098s (userspace) = 9.014s
ventrical@ventrical-MS-7850:~$ 


```

```

ventrical@ventrical-MS-7850:~$ inxi -b
System:    Host: ventrical-MS-7850 Kernel: 3.19.0-22-generic x86_64 (64 bit)
           Desktop: LXDE (Openbox 3.5.2) Distro: Ubuntu 15.10 wily
Machine:   Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0
           Bios: American Megatrends v: V2.8 date: 07/17/2014
CPU:       Dual core Intel Pentium G3240 (-MCP-) speed/max: 2293/3100 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           Display Server: X.Org 1.17.1 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 10.5.8
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 120.0GB (5.4% used)
Info:      Processes: 132 Uptime: 8 min Memory: 422.4/3814.9MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-MS-7850:~$ 


```


Oh yeah .. a motherboard called 'Mate" ... wonder how ubuntu mate desktop will whirl? :)
Regards..

---

### Post by fillip1 on 2015-07-15
Any other suggestions what can cause problem or how to repair it? So, thanks to everyone for yours help.

---

### Post by sudodus on 2015-07-27
Sometimes things happen with the developing release, particularly when you install packages, that do not come with the install iso file. In these cases it may work 'directly', when you re-install, while it can be hard to repair an installed system.

---

### Post by ventrical on 2015-07-28
You can always try the 'alternate' option during install.

[https://wiki.ubuntu.com/U+1/InstructionalDevelopment#What_are_the_F6_options_during_installation](https://wiki.ubuntu.com/U+1/InstructionalDevelopment#What_are_the_F6_options_during_installation).

---

