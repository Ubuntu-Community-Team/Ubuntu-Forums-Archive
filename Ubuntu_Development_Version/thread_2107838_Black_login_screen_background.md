---
title: "Black login screen background"
date: 2013-01-22
forum: Ubuntu Development Version
---

### Post by lardlad on 2013-01-22
Hello,

I recently installed Xubuntu 13.04 on my netbook. I previously had Xubuntu 12.10 on it but screwed up the partitions while trying to dual boot Win7. Before I reinstalled I backed up my home directory with the command "rsync -av", and then restored it after the install. I do not remember if the login screen had the black background before I restored the backup, so I don't know if this is the problem or not. The login screen appears to be normal except the background is black rather than the blue Xubuntu Greybird image. 

When I change the background param in lightdm-gtk-greeter.conf to a color code such as #f00505 the login background does change to that color. I also changed it to other images in /usr/share/pixmaps, but the background was black.

Here are some relevant files:

/etc/lightdm/lightdm-gtk-greeter.conf:
```
[greeter]
logo=/usr/share/pixmaps/xubuntu-lightdm-computer.png
background=/lib/plymouth/themes/xubuntu-logo/xubuntu-greybird.png
theme-name=Greybird
icon-theme-name=elementary-xfce
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-language-selector=true
```

ls -l /lib/plymouth/themes/xubuntu-logo/:
```
-rw-r--r-- 1 root root     98 Sep 15 08:59 fsck-fade_16bit.png
-rw-r--r-- 1 root root    326 Jun 30  2012 fsck-fade.png
-rw-r--r-- 1 root root   2820 Sep 15 09:00 logo_16bit.png
-rw-r--r-- 1 root root   5912 Jun 30  2012 logo.png
-rw-r--r-- 1 root root   2771 Jun 30  2012 passw-dialog.png
-rw-r--r-- 1 root root     88 Sep 15 09:00 progress-fade_16bit.png
-rw-r--r-- 1 root root    269 Sep 15 08:59 progress-fade.png
-rw-r--r-- 1 root root     89 Sep 15 08:59 progress-meter_16bit.png
-rw-r--r-- 1 root root    236 Jun 30  2012 progress-meter.png
-rw-r--r-- 1 root root    148 Sep 15 08:59 test.png
-rw-r--r-- 1 root root 583413 Sep 12 07:35 xubuntu-greybird.png
-rw-r--r-- 1 root root    231 Jun 30  2012 xubuntu-logo.plymouth
-rw-r--r-- 1 root root   9953 Aug 29 11:51 xubuntu-logo.script
```

/var/log/lightdm/x-0-greeter.log:
```

** (lightdm-gtk-greeter:5098): WARNING **: Failed to open sessions directory: Error opening directory '/usr/share/lightdm/remote-sessions': No such file or directory

```

Thank you for any and all help!

---

### Post by brainwash on 2013-01-23
You can find the bug report here:

[https://bugs.launchpad.net/lightdm/+bug/1086199](https://bugs.launchpad.net/lightdm/+bug/1086199)

---

### Post by lardlad on 2013-01-23
Thank you for that link brainwash, it led to a solution.
The problem was that lightdm would only use the image if it had an alpha channel, so by using the command
```
convert <input> -alpha on <output>
```
to add an alpha channel to the desired background image I was able to get it to display the image correctly.

---

