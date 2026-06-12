---
title: "Blank Desktop"
date: 2014-08-21
forum: Ubuntu Development Version
---

### Post by P-I H on 2014-08-21
When I login with Ubuntu (Default) I get a blank desktop. Ctrl+Alt+T is not working. I am able to get a terminal with Ctrl+Alt+F1, but the keybord is changed from "se" to I suppose "us".
Login with Gnome Flashback (Compiz) and Guest Session works fine. The Guest Session uses Unity. I have also created a new user, that works fine with Unity.
As I understand the only difference between the old user and the new user is /home/user. I have not succeeded to identify the file in /home/user, that creates the problem.

I am using systemd, but .xsession-errors contains the following for the working user
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
upstart: gpg-agent post-stop process (11578) killed by TERM signal
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd respawning too fast, stopped

```
and this for the user with the blank screen
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
upstart: gpg-agent post-stop process (9924) killed by TERM signal
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd main process ended, respawning
upstart: at-spi2-registryd respawning too fast, stopped
upstart: unity-settings-daemon main process (9987) terminated with status 1
upstart: hud main process (9991) terminated with status 1
upstart: unity7 main process (9993) terminated with status 1
upstart: gnome-session (Unity) main process (9999) terminated with status 1
upstart: unity-panel-service main process (10010) terminated with status 1
upstart: indicator-keyboard main process (10088) terminated with status 1
upstart: indicator-printers main process (10091) terminated with status 1
upstart: indicator-bluetooth main process (10079) killed by TERM signal
upstart: indicator-power main process (10082) killed by TERM signal
upstart: indicator-datetime main process (10085) killed by TERM signal
upstart: indicator-session main process (10095) killed by TERM signal
upstart: indicator-application main process (10116) killed by TERM signal
upstart: Disconnected from notified D-Bus bus

```

The system uses the Nvidia 331.89 driver.

---

### Post by Alan F on 2014-08-21
Look at this thread. Is it the same problem?

[http://ubuntuforums.org/showthread.php?t=2239381](http://ubuntuforums.org/showthread.php?t=2239381)

---

### Post by grahammechanical on 2014-08-21
Unlike you I have not specifically installed systemd. I am letting things take their course. Today's updates brought in systemd stuff and my system reboots fine. I have systemd version 208-8ubuntu1. What version do you have?

Apport interacts with DBus and so must SystemD and at-spi2-core is described as Assistive Technology Service Provider Interface (dbus core). I have version at-spi2-core 2.10.1. What version do you have? Try removing systemd from your boot parameters and using recovery mode to update and see what effect that has.

[https://launchpad.net/ubuntu/+source/at-spi2-core](https://launchpad.net/ubuntu/+source/at-spi2-core)

Regards.

---

### Post by jerrylamos on 2014-08-22
My experience on my Lenovo ThinkCentre 58p Intel core 2 duo 3 gHz

Utopic amd64 boots to desktop and cursor, no unity.  Looks much like your experience.

I've a pile of launchpad bugs on that, example [https://bugs.launchpad.net/bugs/1359299](https://bugs.launchpad.net/bugs/1359299)

Utopic i386 32 bit most always boots O.K. to unity, occasionally only desktop.

From a couple other bugs, Compiz fails to start because of some interaction with X.  No compiz, no unity.  X is running fine.

amd64 Utopic 3.16.0-6 and previous run fine.  

Utopic 3.16.0-7 and later compiz/unity fail mostly. 

There've been notes that a compiz change was made.  

I'm not aware that the Intel driver has changed.  I don't know if utopic i386 and amd64 use the same Intel video driver and compiz.  How do I tell?

---

### Post by ventrical on 2014-08-22
Use code:

```

lshw

```

in terminal.

```

        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
 
```

---

### Post by jerrylamos on 2014-08-22
22 August update to 

3.16.0-10 amd64 iso boots to desktop no unity i.e. no compiz.

3.16/0-10 i386 32 bit desktop, compiz, and unity running O.K. for a development release.

---

### Post by Alan F on 2014-08-22
> **jerrylamos said:**
> 22 August update to 

3.16.0-10 amd64 iso boots to desktop no unity i.e. no compiz.

3.16/0-10 i386 32 bit desktop, compiz, and unity running O.K. for a development release.

+1 for amd64. Don't have a i386 install to test.

---

### Post by P-I H on 2014-08-23
This might be the same problem as reported by jerrylamos. There are however some differences.
- I have created a new user that works fine with Unity
- I am using Nvidia graphics with the proprietary driver

The at-spi2-core version is listed as "2.10.2.is.2.10.1-0ubuntu1" in Synaptic.
This is an amd64 installation upgraded from Ubuntu 13.10 to 14.04 to 14.10.

I don't think it's a HW problem as Unity works fine in the new user.
lshw
           ```
*-display
                description: VGA compatible controller
                product: GK106 [GeForce GTX 660]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
```

---

### Post by fooman on 2014-08-23
> **P-I H said:**
> This might be the same problem as reported by jerrylamos. There are however some differences.
- I have created a new user that works fine with Unity
- I am using Nvidia graphics with the proprietary driver


same results for me. started a few days ago....blank desktop, no unity, launcher, or dash,  just wallpaper.  was able to get to terminal with ctrl-alt-f1.  then did a sudo reboot and ended up booting into gnome shell,  which loaded without issue.  like P-I H.  i was also able to create a new user which booted up into unity without a problem.  also have an nvidia card w/proprietary drivers.

i finally fixed it by resetting compiz/unity with the following commands:

```
dconf reset -f /org/compiz/
 
setsid unity
```

---

### Post by P-I H on 2014-08-24
dconf reset didn't work. The system complained about X11 not started.
I used this command in a terminal to remove most configurations in the /home/user directory.
```
rm ~/.gconf ~/.gconfd ~/.metacity ~/.compiz-1 ~/.config/compiz-1 ~/.config/dconf -rf
```

This was much easier compared to a new installation.
I got a default launcher and theme. The panel included the same indicators as before.
When I use the Dash to start an application, the configuration of the application is OK and I only need to lock the icon in the Launcher.

---

### Post by cariboo on 2014-08-24
Dconf reset didn't work for me either, I backed up ~/.config then removed it, restarted then selectively restore the configuration files I needed. Before updating to nvidia-343, all I was getting was a black screen with a flashing cursor.

---

### Post by jerrylamos on 2014-08-27
> **fooman said:**
> same results for me. started a few days ago....blank desktop, no unity, launcher, or dash,  just wallpaper.  was able to get to terminal with ctrl-alt-f1.  then did a sudo reboot and ended up booting into gnome shell,  which loaded without issue.  like P-I H.  i was also able to create a new user which booted up into unity without a problem.  also have an nvidia card w/proprietary drivers.

i finally fixed it by resetting compiz/unity with the following commands:

```
dconf reset -f /org/compiz/
 
setsid unity
```
I tried, no luck, to reset compiz and unity.

BTW, a flood of messages on the screen.  Example:

Unity is fully supported by your hardware.
Unity is not supported by your hardware.

These are on two consecutive lines....

---

