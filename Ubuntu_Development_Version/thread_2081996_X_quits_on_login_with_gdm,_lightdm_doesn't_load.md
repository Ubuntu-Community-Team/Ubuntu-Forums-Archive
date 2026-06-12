---
title: "X quits on login with gdm, lightdm doesn't load"
date: 2012-11-08
forum: Ubuntu Development Version
---

### Post by jfernyhough on 2012-11-08
Here's an interesting one. Everything was fine last night, did an update, shut down.

Started up this morning, GDM loads, log in -> back to GDM. Hmm.
Console, service stop GDM, service start LightDM. LightDM doesn't load (similar to missing or unbuilt kernel module for fglrx).
Reinstall fglrx, same thing.
Remove xorg.conf to load the OSS driver. Same thing. This is getting weird. ;)

Console, login, startx:
xinit: connection to X server lost.

/var/log/Xorg.0.log:
Server terminated successfully (0). Closing log file.

So, um, X is loading then quitting? Looking at the last update history:

```
Upgraded the following packages:
at-spi2-core (2.6.0-0ubuntu1) to 2.7.1-1
ca-certificates (20120623) to 20121105
coreutils (8.13-3.2ubuntu3) to 8.13-3.2ubuntu4
debhelper (9.20120608ubuntu1) to 9.20120909ubuntu1
dh-modaliases (1:0.2.71ubuntu2) to 1:0.2.72
gir1.2-atspi-2.0 (2.6.0-0ubuntu1) to 2.7.1-1
gir1.2-cogl-1.0 (1.10.4-0ubuntu1) to 1.12.0-1
gir1.2-coglpango-1.0 (1.10.4-0ubuntu1) to 1.12.0-1
libasound2-plugins (1.0.25-2ubuntu2) to 1.0.25-2ubuntu3
libatk-adaptor (2.6.0-0ubuntu1) to 2.7.1-1
libatk-bridge2.0-0 (2.6.0-0ubuntu1) to 2.7.1-1
libatspi2.0-0 (2.6.0-0ubuntu1) to 2.7.1-1
libcogl-pango0 (1.10.4-0ubuntu1) to 1.12.0-1
libdee-1.0-4 (1.0.14-0ubuntu1) to 1.0.14-0ubuntu2
libgcrypt11 (1.5.0-3ubuntu1) to 1.5.0-3ubuntu2
libgcrypt11:i386 (1.5.0-3ubuntu1) to 1.5.0-3ubuntu2
libglibmm-2.4-1c2a (2.33.13-0ubuntu2) to 2.34.1-0ubuntu1
libgucharmap-2-90-7 (1:3.5.99-0ubuntu1) to 1:3.6.0-0ubuntu1
libgweather-3-1 (3.6.0-0ubuntu1) to 3.6.1-0ubuntu1
libgweather-common (3.6.0-0ubuntu1) to 3.6.1-0ubuntu1
libmessaging-menu0 (12.10.4-0ubuntu1) to 12.10.5-0ubuntu2
libnewt0.52 (0.52.11-2ubuntu12) to 0.52.11-2ubuntu13
libparted0debian1 (2.3-10ubuntu2) to 2.3-11ubuntu1
libpython3.3 (3.3.0-2) to 3.3.0-3
libpython3.3-minimal (3.3.0-2) to 3.3.0-3
libpython3.3-stdlib (3.3.0-2) to 3.3.0-3
libxml-libxml-perl (2.0006+dfsg-1) to 2.0010+dfsg-1
linux-generic (3.5.0.17.19) to 3.7.0.0.2
meld (1.6.0-1) to 1.6.1-1
parted (2.3-10ubuntu2) to 2.3-11ubuntu1
pbuilder (0.208ubuntu1) to 0.213ubuntu1
python-dbus (1.1.1-1ubuntu1) to 1.1.1-1ubuntu2
python-dbus-dev (1.1.1-1ubuntu1) to 1.1.1-1ubuntu2
python-lxml (3.0.1-1) to 3.0.1-1build1
python-newt (0.52.11-2ubuntu12) to 0.52.11-2ubuntu13
python-pkg-resources (0.6.29-1ubuntu1) to 0.6.29-1ubuntu2
python-pyatspi2 (2.6.0+dfsg-0ubuntu1) to 2.7.1+dfsg-1
python3-dbus (1.1.1-1ubuntu1) to 1.1.1-1ubuntu2
python3-gdbm (3.3.0-1) to 3.3.0-1ubuntu1
python3-pkg-resources (0.6.29-1ubuntu1) to 0.6.29-1ubuntu2
python3.3 (3.3.0-2) to 3.3.0-3
python3.3-minimal (3.3.0-2) to 3.3.0-3
swig (2.0.7-3ubuntu1) to 2.0.8-1ubuntu1
swig2.0 (2.0.7-3ubuntu1) to 2.0.8-1ubuntu1
ubuntu-drivers-common (1:0.2.71ubuntu2) to 1:0.2.72
wget (1.13.4-3ubuntu1) to 1.14-1ubuntu1
whiptail (0.52.11-2ubuntu12) to 0.52.11-2ubuntu13
xml-core (0.13+nmu1) to 0.13+nmu2

Installed the following packages:
libcogl11 (1.12.0-1)
libegl1-mesa (9.0-0ubuntu1)
libgail-common (2.24.13-0ubuntu2)
libgbm1 (9.0-0ubuntu1)
libwayland0 (0.95.0-0ubuntu1)
libxcb-xfixes0 (1.8.1-2)
torchlight (1.0+2012+09+26-0ubuntu2)
```

I doubt it's due to Torchlight. ;) EGL? Wayland? Any other ideas?

---

### Post by jfernyhough on 2012-11-08
Argh, it's a profile issue. Bit of a weird one though.

I created a new user and can run startx successfully, and gdm will load correctly. However, lightdm still will not load, I presume because it's trying to load the wallpaper from my usual user account.

So, now it's a case of locating the wallpaper setting; hopefully this will allow me to start X.

---

### Post by jfernyhough on 2012-11-08
Hmm...
$ tail /var/log/syslog
```

Nov  8 16:31:34 arrandale gdm][3907]: pam_ecryptfs: pam_sm_authenticate: /home/jonathon is already mounted
Nov  8 16:31:34 arrandale gdm-simple-slave[3401]: WARNING: Failed to remove slave program access to the display. Trying to proceed.
Nov  8 16:31:34 arrandale gdm-simple-slave[3401]: WARNING: Child process -3441 was already dead.
Nov  8 16:31:34 arrandale gdm][3984]: pam_ecryptfs: Skipping automatic eCryptfs unmount
Nov  8 16:31:35 arrandale gdm-simple-slave[3401]: GLib-GObject-CRITICAL: g_object_ref: assertion `object->ref_count > 0' failed
Nov  8 16:31:35 arrandale gdm-simple-slave[3401]: GLib-GObject-CRITICAL: g_object_unref: assertion `object->ref_count > 0' failed
Nov  8 16:31:35 arrandale gdm[1637]: WARNING: GdmDisplay: display lasted 0.001042 seconds
Nov  8 16:31:35 arrandale acpid: client 3404[0:0] has disconnected
Nov  8 16:31:35 arrandale acpid: client connected from 3990[0:0]
Nov  8 16:31:35 arrandale acpid: 1 client rule loaded
Nov  8 16:31:35 arrandale kernel: [  592.653538] <6>[fglrx] ATIF platform detected with notification ID: 0x81
Nov  8 16:31:36 arrandale gdm-simple-slave[3987]: WARNING: Failed to give slave programs access to the display. Trying to proceed.
Nov  8 16:31:36 arrandale gnome-session[4027]: WARNING: Session 'gdm-shell' runnable check failed: Child process exited with code 1
Nov  8 16:31:36 arrandale gnome-session[4027]: WARNING: Error while executing session-migration: Failed to execute child process "session-migration" (No such file or directory)
Nov  8 16:31:36 arrandale gdm-simple-greeter[4061]: Gtk-WARNING: Overriding tab label for notebook
Nov  8 16:31:36  gdm-simple-greeter[4061]: last message repeated 4 times
Nov  8 16:31:36 arrandale gdm-simple-greeter[4061]: Gtk-CRITICAL: gtk_style_context_set_path: assertion `priv->widget == NULL' failed

```

Trying a chown -R on my $HOME.

---

### Post by jfernyhough on 2012-11-08
LightDM was a red herring; unity-greeter wasn't installed.

This is odd. I share the /home between different Ubuntu installations. I can log in to this user account from my Kubuntu Quantal installation, but not from Raring.

So far I've tried:
* deleting ~/.Xauthority
* apt-get install --reinstall xorg
* dpkg-reconfigure gdm

in various combinations and with reboots.

OK, it's not my profile. I can log in with my ElementaryOS install. This is getting annoying.

---

### Post by jfernyhough on 2012-11-08
This is possible the most random error I've come across in five years of testing - it may have happened before but I've just cleaned out my profile instead of digging.

in ~/.cache/gdm/session.log there was a line:

gpg-agent[8889]: Fatal: can't register GNU Pth with Libgcrypt: Not supported

I asked on #ubuntu+1:

> <genii-around> jonathonf: I got that earlier today after I copied over all my old home directory contents to a fresh install. Just removed ~/.gnupg

So I went in and deleted:
random_seed
gpg.conf
pubring.gpg~

One (or more) of these files were blocking login. Fixed.

---

### Post by sparker256 on 2012-11-08
> **jfernyhough said:**
> This is possible the most random error I've come across in five years of testing - it may have happened before but I've just cleaned out my profile instead of digging.

in ~/.cache/gdm/session.log there was a line:

gpg-agent[8889]: Fatal: can't register GNU Pth with Libgcrypt: Not supported

I asked on #ubuntu+1:



So I went in and deleted:
random_seed
gpg.conf
pubring.gpg~

One (or more) of these files were blocking login. Fixed.
Had the same issue and so I deleted: 
gpg.conf
pubring.gpg

Bill

---

### Post by caryb on 2012-11-09
Needed to delete the same 2 files in Kubuntu & all ok again now :)

Cary

---

### Post by computerwiz908 on 2012-11-09
After generating a new GPG key, the problem reoccurred.

I did some research and found that libgcrypt11 1.5.0-3ubuntu2 is what's causing the failed logins. The bug has been reported here: [https://bugs.launchpad.net/ubuntu/+source/libgcrypt11/+bug/1076906](https://bugs.launchpad.net/ubuntu/+source/libgcrypt11/+bug/1076906)

The upload has been reverted in raring-proposed, so the issue should be fixed soon.

---

