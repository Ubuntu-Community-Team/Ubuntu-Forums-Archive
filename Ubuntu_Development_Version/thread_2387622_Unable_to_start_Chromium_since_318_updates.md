---
title: "Unable to start Chromium since 3/18 updates"
date: 2018-03-21
forum: Ubuntu Development Version
---

### Post by crcarson on 2018-03-21
Install the system update on 3/18 (or 3/17) and now cannot start chromium.  No indication of any error or crash.  Syslog is not much help (at least to me). The only chromium entries are;

Mar 21 10:45:01 cliffps chromium_chromium.desktop[2149]: execl failed: No such file or directory
Mar 21 10:45:01 cliffps chromium_chromium.desktop[2149]: child exited with status 1

with a large number of gnome shell messages (sample)

Mar 21 10:44:57 cliffps org.gnome.Shell.desktop[1601]: #5 0x7ffe7d2e7cb0 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:345 (0x7fd54c2d2a28 @ 100)
Mar 21 10:44:57 cliffps org.gnome.Shell.desktop[1601]: #6 0x7ffe7d2e7d40 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:360 (0x7fd54c2d2ab0 @ 10)
Mar 21 10:44:57 cliffps org.gnome.Shell.desktop[1601]: #7 0x7ffe7d2e7dc0 I   resource:///org/gnome/gjs/modules/signals.js:126 (0x7fd54c2cff78 @ 386)
Mar 21 10:44:57 cliffps org.gnome.Shell.desktop[1601]: #8 0x7ffe7d2e7e70 b   resource:///org/gnome/shell/ui/tweener.js:207 (0x7fd54c2cf5e8 @ 159)
Mar 21 10:44:57 cliffps gnome-shell[1601]: Object St.BoxLayout (0x55f3526a45c0), has been already finalized. Impossible to set any property to it.
Mar 21 10:44:57 cliffps org.gnome.Shell.desktop[1601]: #9 0x7ffe7d2e7ed0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fd54c2b4de0 @ 71)
Mar 21 10:44:57 cliffps org.gnome.Shell.desktop[1601]: #10 0x7ffe7d2e7f70 b   resource:///org/gnome/shell/ui/tweener.js:182 (0x7fd54c2cf560 @ 15)

before and after the chromium message.  Feel certain this is not a chromium problem, it was working well and no updates to it have been done for sometime.  Wanted to start chromium from a command line but unable to figure out the right command to use.

---

### Post by #&amp;thj^% on 2018-03-21
From the terminal:
```
chromium-browser
```

---

### Post by crcarson on 2018-03-21
I had for some time been using the chromium install by snap.  That is the version (or product) that is now failing.  Issuing the command chromium-browser indicates that I need to install the product via apt.  Did the install and indeed chromium-browser works but the one installed via snap does not.  Checked the version of chromium supplied by apt and it is the version of the "canididate" level in snap not the "stable" version.  Deleted chromium with apt and snap and install the snap chromium using --canididate option.  The problem still exists, chromium will not start using the supplied ICON.

---

### Post by crcarson on 2018-03-21
Interesting, all the products install via snap no longer start.  Here is what displays when starting gimp;

cliff@cliffps:~$ gimp
ln: failed to create symbolic link '/home/cliff/snap/gimp/30/.config/gtk-2.0/gtkfilechooser.ini': File exists
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Cannot open display: 

Something in a recent update has broken snap.

---

### Post by #&amp;thj^% on 2018-03-21
Curious??
See what this produces 
```
snap run chromium-browser
```
Or:
```
snap run gimp
```

---

### Post by crcarson on 2018-03-21
Tried both commands also add snap list;

cliff@cliffps:~/Scripts$ snap run gimp
ln: failed to create symbolic link '/home/cliff/snap/gimp/30/.config/gtk-2.0/gtkfilechooser.ini': File exists
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Cannot open display: 
cliff@cliffps:~/Scripts$ snap run chromium-browser
error: cannot find current revision for snap chromium-browser: readlink /snap/chromium-browser/current: no such file or directory
cliff@cliffps:~/Scripts$ snap list
Name                  Version           Rev   Tracking   Developer     Notes
chromium              65.0.3325.146     262   candidate  canonical     -
clementine            1.3.1.29+git      54    stable     kz6fittycent  -
core                  16-2.31.2         4206  stable     canonical     core
gimp                  2.8.22            30    stable     snapcrafters  -
gnome-3-26-1604       3.26.0            53    stable     canonical     -
gnome-calculator      3.26.0            154   stable     canonical     -
gnome-characters      3.26.2            69    stable     canonical     -
gnome-logs            3.26.2            25    stable     canonical     -
gnome-system-monitor  3.26.0            36    stable     canonical     -
notepadqq             1.2.0-2           115   stable     danieleds     -
vlc                   3.0.1-4-g14a4897  190   stable     videolan      -
cliff@cliffps:~/Scripts$

In snap it is chromium not chromium-browser.  Running snap run chromium you get the error seen in the syslog.

cliff@cliffps:~/Scripts$ snap run chromium
execl failed: No such file or directory
child exited with status 1

---

### Post by #&amp;thj^% on 2018-03-21
Yes I can see the mess that snap installed apps create...Not a snap fan myself.
Gnome is now for the most part using Versions eg:
```
gnome-calculator:
  Installed: (none)
  Candidate: 1:3.28.0-1ubuntu1
  Version table:
     1:3.28.0-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages

```
Where you see "gnome-3-26"
So i guess your left with a trade off>>>To snap or not to snap. ;)
When the last time you updated and upgraded?

---

### Post by mc4man on 2018-03-21
Don't use snap as of yet so (re)installed snapd, see no issue in Ubuntu with any of the ones you mentioned
Using snapd 2.32+18.04~pre6

---

### Post by crcarson on 2018-03-21
If the update/upgrade is directed to me I update/upgrade every morning after bringing up the systems.  Have a laptop and desktop both running 18.04 and both with this problem.

---

### Post by mc4man on 2018-03-21
> **crcarson said:**
> If the update/upgrade is directed to me I update/upgrade every morning after bringing up the systems.  Have a laptop and desktop both running 18.04 and both with this problem.
You could always try removing snapd (sudo apt purge snapd), removing any launchers (icons),if any, rebooting & then install snapd & a snap or two to see. If still no good then maybe *buntu related or something local.

---

### Post by #&amp;thj^% on 2018-03-21
If you did as mc4man suggested:
```
 sudo apt install --reinstall snapd
```
And:
```
sudo snap install chromium

``` 
And:
```
snap run chromium
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
ATTENTION: default value of option force_s3tc_enable overridden by environment.

```
Results:Screenshot

---

### Post by crcarson on 2018-03-21
> **mc4man said:**
> You could always try removing snapd (sudo apt purge snapd), removing any launchers (icons),if any, rebooting & then install snapd & a snap or two to see. If still no good then maybe *buntu related or something local.

Removed chromium with snap remove
Removed snapd with apt remove
Restarted
Installed snapd with apt install
Installed chromium with snap install
Tried to start chromium with the same result (same info in the syslog)

---

### Post by kerry_s on 2018-03-21
just update:
sudo apt update && sudo apt -y full-upgrade

---

### Post by crcarson on 2018-03-21
> **kerry_s said:**
> just update:
sudo apt update && sudo apt -y full-upgrade

Made no difference.  Did update/full-upgrade, rebooted, and tried to start gimp with the same result.

cliff@cliffps:~$ gimp
ln: failed to create symbolic link '/home/cliff/snap/gimp/30/.config/gtk-2.0/gtkfilechooser.ini': File exists
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Cannot open display:

---

### Post by kerry_s on 2018-03-21
did you run: sudo snap refresh

---

### Post by crcarson on 2018-03-21
> **kerry_s said:**
> did you run: sudo snap refresh

Ran snap refresh, no help.  Sure this was done when removing snapd and re-installing.

---

### Post by kerry_s on 2018-03-21
so weird all my snaps work.
[ATTACH=CONFIG]279031[/ATTACH]

---

### Post by mc4man on 2018-03-21
Well they work fine in a lubuntu daily live session, (not inclined to install) so must be something about your install. (or diff between a live session & your's.
In the lubuntu live the terminal doesn't even show any warnings, ect..
If you can't figure out just do a fresh install, no big deal, shouldn't take very long at all.

(- whether you purgerd snapd or whether that matters, don't know. Again you simply had to purge snapd, reboot, add back, install a snap, no need to remove anything else.. Probably doesn't matter.
What you could do right now  is  remove the  ~/snap folder entirely, then try opening a snap from terminal.

---

### Post by crcarson on 2018-03-22
Indicated that there were two different 18.04 system failing.  Check the desktop yesterday and found it was able to start the snap version of chromium and gimp.  Thought I just wrong about both system failing but started the laptop this morning and did the normal update/upgrade and it is no longer failing.  Go figure.

---

### Post by corradoventu on 2018-03-23
I had many problems with snap applications having  snapd 2.32+18.04~pre5
after update to new snapd```
corrado@corrado-p13-bb-0319:~$ snap version
snap    2.32+18.04~pre6
snapd   2.32+18.04~pre6
series  16
ubuntu  18.04
kernel  4.15.0-12-generic
corrado@corrado-p13-bb-0319:~$ 
```snap applications run well

---

