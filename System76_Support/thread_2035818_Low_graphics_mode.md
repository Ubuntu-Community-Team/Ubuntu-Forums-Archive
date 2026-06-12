---
title: "Low graphics mode"
date: 2012-07-31
forum: System76 Support
---

### Post by MoebusNet on 2012-07-31
Since the last batch of updates about 4 days ago or so, on initial boot-up of the day I'm not getting a login screen but am getting an error saying that I'm running in low-graphics mode. Clicking OK gets me to a menu of four options, like reconfigure, troubleshoot, and exit to console login, but I have no cursor and am unable to select any of the options.

I've been using CTRL-alt-SysRq REISUB to recover, but what can I do to fix or at least troubleshoot this issue?

System76 Serp7 with NVIDIA GeForce 560M

---

### Post by AbbasKhalil on 2012-08-01
Note: I do not mean to Hijack this thread but I have a same situation as the OP.

I Second the situation.
I am having the same problem on Startup.
I have a HD7000 series ATI card.
I am using the official drivers from AMD for support of full 3D acceleration.
The AMD Catalyst gives me the option to switch to Intel Integrated graphics. When I do that, I have to restart for it to take effect. It boots into low graphics mode desktop where my mouse cursor never shows up and there is no keyboard functionality so that I can choose one of the four options.
I then have to switch to terminal and reconfigure the catalyst through command-line to switch to the ATI GPU and ubuntu works fine again. Running the laptop on ATI GPU isnt helping with the battery life at all.

---

### Post by isantop on 2012-08-01
> **AbbasKhalil said:**
> Note: I do not mean to Hijack this thread but I have a same situation as the OP.

I Second the situation.
I am having the same problem on Startup.
I have a HD7000 series ATI card.
I am using the official drivers from AMD for support of full 3D acceleration.
The AMD Catalyst gives me the option to switch to Intel Integrated graphics. When I do that, I have to restart for it to take effect. It boots into low graphics mode desktop where my mouse cursor never shows up and there is no keyboard functionality so that I can choose one of the four options.
I then have to switch to terminal and reconfigure the catalyst through command-line to switch to the ATI GPU and ubuntu works fine again. Running the laptop on ATI GPU isnt helping with the battery life at all.

I think you have a different problem. Plus, we can't really provide good support for non-System76 PCs here. You might try this section: [http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

As for the original problem, try pressing Ctrl+Alt+F1 on your keyboard, then log in. From here, run these commands:

```
sudo rm -v /etc/X11/xorg.conf
sudo reboot
```

This will clear any existing configuration you may have, then reboot the system.

---

### Post by MoebusNet on 2012-08-02
Thank you. Marking as "Solved".

---

### Post by MoebusNet on 2012-09-30
Another set of updates, another recurrence of "Low Graphics Mode". This time ```
sudo rm -v /etc/X11/xorg.conf
``` resulted in '/etc/X11/xorg.conf not found'.

Entered ```
sudo reboot
```but wound up back in 'Low Graphics Mode' after the reboot.

BTW, attempting to use the 'One Time Boot Into Low Graphics Mode' option just drops to console. Using startx just returns 'xserver already in use' (or similar) message.

Finally used Ctrl-Alt-SysRq+REISUB which finally got booted correctly.

Is this a flaw in the kernel module for Nvidia? I seem to get 'Low Graphics' Mode' about once a week; more often after various updates.

EDIT: Latest updates seem to have solved this for now *fingers crossed*

---

