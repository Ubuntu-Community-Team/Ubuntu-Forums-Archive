---
title: "Problem with graphics in Ubuntu"
date: 2012-03-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by erik1001 on 2012-03-21
Hello. 
I have a problem with my Ubuntu. I've upgraded to 12.04 Beta, but I'm almost sure that the problem could be solved the same way as 11.10. So as you may know, there are troubles with ATI Radeon graphic cards with Linux, so I've tried to change my drivers by terminal. Everything was OK until I rebooted and realised that the graphical interface is unable to start. Running "startx" returns:
```

[...]
Current version of pixman: 0.18.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (–) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  4 11:35:54 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) No devices detected.
Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.

```
So I googled for sugggestions and I tried:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bckup
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

```
and
```

sudo apt-get --reinstall install fglrx

```
and
```

sudo dpkg-reconfigure xserver-xorg

```
but nothing changed. What would you suggest to do?
Sorry for my English. Thanks in advance.

---

### Post by Bucky Ball on 2012-03-21
You realise that 12.04 LTS is still testing and unreleased? Expect bugs and breakages. I have asked mods to move this thread to the appropriate forum. ;)

Was there any particular reason you decided to switch from a functioning 11.10 install?

---

### Post by nothingspecial on 2012-03-21
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by mastablasta on 2012-03-21
> **erik1001 said:**
> Hello. 
 I've upgraded to 12.04 Beta, but I'm almost sure that the problem could be solved the same way as 11.10. So as you may know, there are troubles with ATI Radeon graphic cards with Linux, so I've tried to change my drivers by terminal. 
 
i am guessing you didnt' remove drivers first before doing the upgrade and then install new ones after the upgrade finished?
 
you need to remove and purge the older drivers first then you can install new ones.
 [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by QIII on 2012-03-21
As far as I know, I have been using ATI, then AMD/ATI graphics for many years with no more trouble than I have had with NVIDIA and Intel.

Remove and purge the fglrx driver.  Reinstall the fglrx driver.

Then, BEFORE you restart, do

```
sudo aticonfig --initial
```

which will, among other things, create a useable xorg.conf that you can modify later with the Catalyst Control Center.

---

### Post by erik1001 on 2012-03-21
Thank you very much. After removing and installing again drivers everything works as it should be.
@Bucky Ball:
I thought it would have the same error even if I were with 11.10. Sorry.
@mastablasta:
You are right. I'll know I should uninstall older drivers first for the next time.
@QIII:
I have very annoying problems using Gnome3 with some color spots, disordering elements etc with ATI, but not NVIDIA graphics. So I tried almost everything on the internet and it seems I have to use Unity shell because it's the only environment which works properly on my PC. 
Thank you all. :)

---

### Post by Bucky Ball on 2012-03-21
Please mark thread as 'Solved' to help others. ;)

Incidentally, have you tried xfce as a desktop environment? From Software Centre, install 'xfce4', logout, from the Session pop-up menu down the bottom choose 'Xfce Session', log back in again.

You can switch back to Unity at anytime by repeating this process and choosing Unity from Sessions pop-up. ;)

---

### Post by grahammechanical on 2012-03-21
I wonder what is going to happen come the month of May when 12.04 ceases to be a development release? Then those who have issues like this will have to be given the same answers as those who have the same issues in 11.10.

Terminal commands do not change from release to release. Some problems are OS problems not especially development release problems.

Regards.

---

### Post by Bucky Ball on 2012-03-21
> **grahammechanical said:**
> terminal commands do not change from release to release. Some problems are os problems not especially development release problems.

Regards.

+1.

---

