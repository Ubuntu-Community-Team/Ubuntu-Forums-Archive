---
title: "Lost Ubuntu Desktop &amp; Unity after today's update"
date: 2012-01-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by iClouseau88 on 2012-01-14
Hi,

I need your help.  After today's update (kernel 3.2.0-8-generic) I was able to fix the broken packages due to libreoffice, but I am running into the following new problems:

1. Ubuntu Desktop is gone.  Found that gdm was somehow uninstalled.  Re-installing gdm and running "sudo gdm start" did not solve this problem.  Here's the error message from running in terminal mode:

> 
Unable to load /etc/gdm/custom.conf.  No such file


About 2-3 months ago I followed the guide in webupd8 to put Unity in the horizontal panel, because the original Unity kept encroaching Firefox's buttons in the top left corner. On the first reboot after today's update, Unity is on the vertical column on the left side of the screen but now it's gone.

2.  Unity is gone even though the package is still installed.

Now after logging in, I see the wallpaper only. The only way I can get Ubuntu Desktop and Unity is booting in Recovery Mode but this is just a temporary solution.

Any suggestions?

Thanks in advance for your help.

:confused:

---

### Post by bluexrider on 2012-01-14
to reset unity

```
unity --reset
```To reset icons

```
unity --reset-icons
```To reset compiz

```
gconftool-2 --recursive-unset /apps/compiz-1 gconftool-2 --recursive-unset /apps/compizconfig-1 unity --reset

```or you may nave to 
```
rm -rf ~/.config/compiz-1/compizconfig/*

```

---

### Post by effenberg0x0 on 2012-01-14
AFAIK there's no reason to have gdm installed. The current dm is lightdm, which is started/stopped as a service:
```
sudo service lightdm start
sudo service lightdm stop
```So, maybe, a good starting point if the above don't get you to unity, would be to purge gdm and reinstall lightdm, then restart it:

```
sudo apt-get remove --purge gdm
sudo apt-get install --reinstall lightdm
sudo service lightdm restart
```At this point, any effect in the sense of a black screen, a console screen, a terminal screen, anything that is not a colourful GUI screen has a more-than-90% chance of being a standard reinstalation of VGA drivers issue. If not or properly attempted with no results, dmesg and /var/log/xorg.0.log will be needed for any further procedures.

Regards,
Effenberg

---

### Post by jerrylamos on 2012-01-15
Same thing here yesterday.  

Wallpaper and cursor only.

Tried Alt-F2
login
passwd
sudo service lightdm restart

Same thing, wallpaper and cursor only.

Alt-F2
login etc.
sudo dhclient 
sudo ifconfig
to see if network was up.  It was.

sudo apt-get update
sudo apt-get dist-upgrade

rebooted, desktop back now.

?

Jerry

---

### Post by JRV on 2012-01-15
Yesterday's update worked fine for me.

This is my method for updating:

Run Update Manager, click Check.
(This is the same as "sudo apt-get update")

Look over the list to check for problems.

Close Update Manager. **Do not do the upgrade.**

Open a terminal and:```
sudo aptitude safe-upgrade
```

This usually works, sometimes it will tell you that it can't resolve all the dependancies, and to try:```
sudo aptitude safe-upgrade --full-resolver
```

Look at the list and see if the solution it proposes is acceptable.

--------------------------------

Yesterday --full-resolver told me it wanted to remove flash and about 100 of its dependancies.

I ran it, and then reinstalled flash.

---

### Post by iClouseau88 on 2012-01-15
Hello everyone,

Thank you for the replies I received.  It appears...

1. Login screen

2. Settings (Gear icon above the right of userid box):

2a. Gnome: gives a Gnome 3 desktop like in Fedora 15 & 16

2b. Gnome Classic: gives Unity Launcher on the left column of the screen

2c. Gnome Classic (No effects): gives a Gnome 2 desktop as in Ubuntu versions prior to 9.0

2d. Ubuntu (i.e. Ubuntu 3D): gives a wallpaper only.

2e. Ubuntu 2D: gives the usual Unity launcher on the left side of the screen

Cheers!

---

### Post by grahammechanical on 2012-01-15
The other day/night during the problem with Libreoffice and the repositories I was trying to get the update working with Synaptic and it wanted to remove ubuntu-desktop. I noticed that it has a bit of a habit of wanting to remove ubuntu-desktop. So, it is something that I watch out for.

This time I waited a few hours and Synaptic was now willing to do the update without removing ubuntu-desktop.

Is this what happened to iClouseau88?

And yes, I do know that synaptic is just computer code and not a person.

Regards.

---

### Post by iClouseau88 on 2012-01-16
Hello grahammechanical.,

Lately I was using Synaptic to update Ubuntu, because I was burned twice last year using "sudo aptitude update && sudo aptitude safe-upgrade"  in Beta phases.  Thank you for pointing out the tendency of Synaptic to remove "unity-desktop".  Perhaps this is the bug that developers should fix ASAP.  From now on I will be extra careful with Synaptic and/or the commands.

---

### Post by iClouseau88 on 2012-01-17
Hi everyone,

I finally was able to solve this problem.  Refer to the following thread:

[http://ubuntuforums.org/showthread.php?p=11619289#post11619289]("http://ubuntuforums.org/showthread.php?p=11619289#post11619289")

---

