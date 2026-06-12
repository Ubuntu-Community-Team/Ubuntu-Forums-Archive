---
title: "GIMP snap not keeping permissions"
date: 2019-03-27
forum: Ubuntu Development Version
---

### Post by thenailedone on 2019-03-27
Snap of GIMP installed from software centre. Trying to change permissions for read/write to external drives and it doesn't stick. Ubuntu 19.04 fully up-to-date at time of post.

---

### Post by #&amp;thj^% on 2019-03-27
So this dose not work then? (Stick/Stay)
If you need GIMP to have full access to external media (such as USB flash drive, SD/MicroSD card, additional mounted hard drive and so on), run the following command:

```
sudo snap connect gimp:removable-media
```

---

### Post by thenailedone on 2019-03-27
> **1fallen said:**
> So this dose not work then? (Stick/Stay)
If you need GIMP to have full access to external media (such as USB flash drive, SD/MicroSD card, additional mounted hard drive and so on), run the following command:

```
sudo snap connect gimp:removable-media
```

Nope doesn't work. I used the toggle switch in Software Centre initially and the switch will revert after I switch it to on. Terminal command doesn't give error but still can't open files. Odd.

BTW this is an additional internal HDD I am mounting specifically to a folder in root. /data. I have taken ownership of the folder using chown.

---

### Post by #&amp;thj^% on 2019-03-27
> **thenailedone said:**
> Nope doesn't work. I used the toggle switch in Software Centre initially and the switch will revert after I switch it to on. Terminal command doesn't give error but still can't open files. Odd.

BTW this is an additional internal HDD I am mounting specifically to a folder in root. /data. I have taken ownership of the folder using chown.

Hummm, what dose this show:
```
snap interfaces gimp
```
Mine:
```
 snap list
Name                  Version                    Rev   Tracking  Publisher     Notes
core                  16-2.37.4                  6531  stable    canonical&#10003;    core
core18                18                         782   stable    canonical&#10003;    base
gimp                  2.10.8                     130   stable    snapcrafters  -
gnome-3-26-1604       3.26.0.20190228            82    stable/&#8230;  canonical&#10003;    -
gnome-3-28-1804       3.28.0-9-gce87599.ce87599  23    stable    canonical&#10003;    -
gnome-calculator      3.32.0+git2.cae338ea       352   stable/&#8230;  canonical&#10003;    -
gnome-characters      v3.32.0+git1.9ff74a2       206   stable/&#8230;  canonical&#10003;    -
gnome-logs            3.32.0                     57    stable/&#8230;  canonical&#10003;    -
gnome-system-monitor  3.32.0                     70    stable/&#8230;  canonical&#10003;    -
gtk-common-themes     0.1-16-g2287c87            1198  stable/&#8230;  canonical&#10003;    -

```
permissions;
```
root@me-ThinkPad-T430:~# cd /root
root@me-ThinkPad-T430:~# ls -al
total 40
drwx------  8 root root 4096 Mar 26 16:22 .
drwxr-xr-x 24 root root 4096 Mar 26 13:41 ..
-rw-r--r--  1 root root 3106 Aug  6  2018 .bashrc
drwx------  5 root root 4096 Mar 26 12:53 .cache
drwxr-xr-x  3 root root 4096 Mar 26 12:53 .config
drwx------  3 root root 4096 Mar 26 12:52 .dbus
drwx------  2 root root 4096 Mar 26 12:53 .gvfs
drwxr-xr-x  3 root root 4096 Mar 26 16:22 .local
-rw-r--r--  1 root root  148 Aug  6  2018 .profile
drwx------  3 root root 4096 Mar 26 12:55 .synaptic
root@me-ThinkPad-T430:~# 

```

---

### Post by thenailedone on 2019-03-27
```
nailed@adjective-animal:/$ snap list
Name                  Version                    Rev   Tracking  Publisher     Notes
core                  16-2.37.4                  6531  stable    canonical&#10003;    core
core18                18                         782   stable    canonical&#10003;    base
gimp                  2.10.8                     130   stable    snapcrafters  -
gnome-3-26-1604       3.26.0.20190228            82    stable/…  canonical&#10003;    -
gnome-3-28-1804       3.28.0-9-gce87599.ce87599  23    stable    canonical&#10003;    -
gnome-calculator      3.32.0+git2.cae338ea       352   stable/…  canonical&#10003;    -
gnome-characters      v3.32.0+git1.9ff74a2       206   stable/…  canonical&#10003;    -
gnome-logs            3.32.0                     57    stable/…  canonical&#10003;    -
gnome-system-monitor  3.32.0                     70    stable/…  canonical&#10003;    -
gtk-common-themes     0.1-16-g2287c87            1198  stable/…  canonical&#10003;    -
spotify               1.1.0.237.g378f6f25-11     34    stable    spotify&#10003;      -
nailed@adjective-animal:/$
```

```
nailed@adjective-animal:/$ snap interfaces gimp
Slot                            Plug
:desktop                        gimp
:desktop-legacy                 gimp
:gsettings                      gimp
:home                           gimp
:network                        gimp
:opengl                         gimp
:removable-media                gimp
:unity7                         gimp
:wayland                        gimp
:x11                            gimp
gimp:dbus-gimp                  -
gtk-common-themes:gtk-3-themes  gimp
gtk-common-themes:icon-themes   gimp
gtk-common-themes:sound-themes  gimp
-                               gimp:cups-control
nailed@adjective-animal:/$ 
```

```
nailed@adjective-animal:/$ ls -al
total 2097248
drwxr-xr-x   22 root   root         4096 Mar 24 11:43 .
drwxr-xr-x   22 root   root         4096 Mar 24 11:43 ..
drwx------.   9 nailed nailed       4096 Mar 21 10:17 back-up
lrwxrwxrwx    1 root   root            7 Mar 24 09:33 bin -> usr/bin
drwxr-xr-x    3 root   root         4096 Mar 27 09:33 boot
drwxrwxr-x    2 root   root         4096 Mar 24 09:34 cdrom
drwx------    8 nailed nailed       4096 Mar 26 10:01 data
drwxr-xr-x   21 root   root         4700 Mar 27 15:24 dev
drwxr-xr-x  136 root   root        12288 Mar 27 13:42 etc
drwxr-xr-x    3 root   root         4096 Mar 24 09:35 home
lrwxrwxrwx    1 root   root           31 Mar 24 09:40 initrd.img -> boot/initrd.img-5.0.0-7-generic
lrwxrwxrwx    1 root   root           31 Mar 24 09:33 initrd.img.old -> boot/initrd.img-5.0.0-7-generic
lrwxrwxrwx    1 root   root            7 Mar 24 09:33 lib -> usr/lib
lrwxrwxrwx    1 root   root            9 Mar 24 09:33 lib32 -> usr/lib32
lrwxrwxrwx    1 root   root            9 Mar 24 09:33 lib64 -> usr/lib64
lrwxrwxrwx    1 root   root           10 Mar 24 09:33 libx32 -> usr/libx32
drwx------    2 root   root        16384 Mar 24 09:32 lost+found
drwxr-xr-x    3 root   root         4096 Mar 24 10:09 media
drwxr-xr-x    2 root   root         4096 Mar 18 11:33 mnt
drwxr-xr-x    3 root   root         4096 Mar 27 13:16 opt
dr-xr-xr-x  332 root   root            0 Mar 27 15:24 proc
drwx------    4 root   root         4096 Mar 25 09:31 root
drwxr-xr-x   34 root   root         1020 Mar 27 16:27 run
lrwxrwxrwx    1 root   root            8 Mar 24 09:33 sbin -> usr/sbin
drwxr-xr-x   14 root   root         4096 Mar 27 15:29 snap
drwxr-xr-x    2 root   root         4096 Mar 18 11:33 srv
-rw-------    1 root   root   2147483648 Mar 24 09:33 swapfile
dr-xr-xr-x   13 root   root            0 Mar 27 19:49 sys
drwxrwxrwt   23 root   root         4096 Mar 27 19:45 tmp
drwxr-xr-x   14 root   root         4096 Mar 18 11:34 usr
drwxr-xr-x   14 root   root         4096 Mar 18 11:41 var
lrwxrwxrwx    1 root   root           28 Mar 24 09:40 vmlinuz -> boot/vmlinuz-5.0.0-7-generic
nailed@adjective-animal:/$
```

---

### Post by #&amp;thj^% on 2019-03-27
This has to be a permission problem.
To see examples of snap's protected mounts:
```
mount | egrep snap | egrep ro,
/var/lib/snapd/snaps/gnome-characters_124.snap on /snap/gnome-characters/124 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_23.snap on /snap/gnome-3-28-1804/23 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_701.snap on /snap/gtk-common-themes/701 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_5662.snap on /snap/core/5662 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_238.snap on /snap/gnome-calculator/238 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_57.snap on /snap/gnome-system-monitor/57 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_782.snap on /snap/core18/782 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_82.snap on /snap/gnome-3-26-1604/82 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_206.snap on /snap/gnome-characters/206 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1198.snap on /snap/gtk-common-themes/1198 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_45.snap on /snap/gnome-logs/45 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_57.snap on /snap/gnome-logs/57 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_70.snap on /snap/gnome-system-monitor/70 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_352.snap on /snap/gnome-calculator/352 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_6531.snap on /snap/core/6531 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_70.snap on /snap/gnome-3-26-1604/70 type squashfs (ro,nodev,relatime,x-gdu.hide)
**_/var/lib/snapd/snaps/gimp_130.snap on /snap/gimp/130 type squashfs (ro,nodev,relatime,x-gdu.hide)_**
```

---

### Post by thenailedone on 2019-03-27
Looks the same to me :/

```
nailed@adjective-animal:~$ mount | egrep snap | egrep ro,
/var/lib/snapd/snaps/gnome-logs_45.snap on /snap/gnome-logs/45 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/spotify_34.snap on /snap/spotify/34 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_139.snap on /snap/gnome-characters/139 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_782.snap on /snap/core18/782 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_352.snap on /snap/gnome-calculator/352 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_6531.snap on /snap/core/6531 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_57.snap on /snap/gnome-system-monitor/57 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_23.snap on /snap/gnome-3-28-1804/23 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_57.snap on /snap/gnome-logs/57 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1198.snap on /snap/gtk-common-themes/1198 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_70.snap on /snap/gnome-system-monitor/70 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_206.snap on /snap/gnome-characters/206 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_260.snap on /snap/gnome-calculator/260 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_82.snap on /snap/gnome-3-26-1604/82 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gimp_130.snap on /snap/gimp/130 type squashfs (ro,nodev,relatime,x-gdu.hide)
```

---

### Post by #&amp;thj^% on 2019-03-27
That looks good, but thats not the permissions I was speaking of.
One more to try:
```
sudo snap connect gimp:removable-media
```
Dose this help, or more or the same?
Ah, I think I'm overthinking this,  If your other partitions are mounted elsewhere, the snap will not have permission to follow the symlinks.

The ways to make this work, ordered by difficulty:
[list]
    [*]Mount the partitions into your home directory rather than symlinking them.
    [*]Mount the partitions into /media and ensure gimp uses the removable-media interface. This may be an upstream change, but a small one.[/list]
Or remove the snap installed gimp and install through "apt".

---

### Post by thenailedone on 2019-03-29
Already tried the command previously and it had no effect. I normally just use APT, was testing the Dubious Donkey to see snaps are any better. Sadly not. **sudo apt install** gimp ftw!

---

### Post by VanillaMozilla on 2019-11-30
Ohmygosh, thank you very much.  **That does work.**  The interweb is full of bogus excuses, useless and partial information, and blind alleys.  Pages and pages have been written on this, and the solution is one short command.  Flagging this as well as I can, so other people can find it.  Sorry, I can't solve the OP's problem, though.

[B]Note that the command to allow gimp to open files on external drives is
snap connect gimp:removable-media.[/B]

snap connect gimp:removable-media gimp
(which I gleaned incorrectly from the man page) does not work.

---

### Post by cariboo on 2019-12-01
Thread Closed.

---

