---
title: "Screensaver..."
date: 2018-12-28
forum: Ubuntu Development Version
---

### Post by Smask on 2018-12-28
The screensaver loses the connection to the desktop. Dragging the saver screen upwards doesn't bring back the desktop, just the blank purple screen with the indicator at the top corner. I can use this indicator to  invoke hibernate/sleep mode and then use that to get unlocked and restore my desktop.

I don't know if this is a continuation of the old screensaver bug that happened on Gnome Flashback computers that got only one display connected. I can't login to Flashback any more to check this, since something broke at the same time as the system went from Nautilus 3.26 to 3.30.

---

### Post by mc4man on 2018-12-28
Do you mean the lockscreen or some actual screensaver?
Since when did nautilus go to 3.30?

---

### Post by P-I H on 2018-12-29
I activated the Developer Options and got these updates , that include nautilus:amd64 (1:3.26.4-0ubuntu9, 1:3.30.4-1ubuntu1)
```
Start-Date: 2018-12-19  15:13:46
Commandline: /usr/sbin/synaptic
Requested-By: p-i (1000)
Install: linux-image-4.19.0-9-generic:amd64 (4.19.0-9.10, automatic), tracker-extract:amd64 (2.1.5-3ubuntu1, automatic), linux-modules-extra-4.19.0-9-generic:amd64 (4.19.0-9.10, automatic), linux-headers-4.19.0-9-generic:amd64 (4.19.0-9.10, automatic), libgsf-1-114:amd64 (1.14.44-1, automatic), tracker-miner-fs:amd64 (2.1.5-3ubuntu1, automatic), libtracker-miner-2.0-0:amd64 (2.1.6-4, automatic), linux-modules-4.19.0-9-generic:amd64 (4.19.0-9.10, automatic), libgif7:amd64 (5.1.4-3, automatic), libgsf-1-common:amd64 (1.14.44-1, automatic), linux-headers-4.19.0-9:amd64 (4.19.0-9.10, automatic), tracker:amd64 (2.1.6-4, automatic), libtracker-control-2.0-0:amd64 (2.1.6-4, automatic), libtagc0:amd64 (1.11.1+dfsg.1-0.2build3, automatic), libcue2:amd64 (2.2.1-2, automatic)
Upgrade: init:amd64 (1.56, 1.56+nmu1), libmpx2:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), init-system-helpers:amd64 (1.56, 1.56+nmu1), libldb1:amd64 (2:1.4.0+really1.3.5-2, 2:1.5.1+really1.4.3-1ubuntu1), libcom-err2:amd64 (1.44.4-2ubuntu1, 1.44.5-1), linux-headers-generic:amd64 (4.18.0.11.12, 4.19.0.9.10), gir1.2-gtk-3.0:amd64 (3.24.1-1ubuntu2, 3.24.2-2ubuntu2), linux-libc-dev:amd64 (4.18.0-11.12, 4.19.0-9.10), libllvm7:amd64 (1:7-9~build1, 1:7.0.1-1), libgirepository-1.0-1:amd64 (1.58.1-1, 1.58.2-1), sane-utils:amd64 (1.0.27-1, 1.0.27-3.1), libwbclient0:amd64 (2:4.8.4+dfsg-2ubuntu2, 2:4.9.2+dfsg-2ubuntu1), libgtk-3-common:amd64 (3.24.1-1ubuntu2, 3.24.2-2ubuntu2), linux-image-generic:amd64 (4.18.0.11.12, 4.19.0.9.10), libgtk-3-0:amd64 (3.24.1-1ubuntu2, 3.24.2-2ubuntu2), cpp-8:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), gcc-8-base:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), binutils:amd64 (2.31.1-10ubuntu1, 2.31.1-11ubuntu1), libgpg-error0:amd64 (1.32-3, 1.33-3), e2fsprogs:amd64 (1.44.4-2ubuntu1, 1.44.5-1), libitm1:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), python3-gi-cairo:amd64 (3.30.2-1, 3.30.4-1), plymouth-label:amd64 (0.9.3-1ubuntu11, 0.9.3-1ubuntu12), libharfbuzz-icu0:amd64 (2.1.1-1build1, 2.2.0-1), plymouth-theme-ubuntu-text:amd64 (0.9.3-1ubuntu11, 0.9.3-1ubuntu12), python3-six:amd64 (1.11.0-2, 1.12.0-1), libasan5:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), libquadmath0:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), gir1.2-freedesktop:amd64 (1.58.1-1, 1.58.2-1), libassuan0:amd64 (2.5.1-2, 2.5.2-1), linux-signed-generic:amd64 (4.18.0.11.12, 4.19.0.9.10), libplymouth4:amd64 (0.9.3-1ubuntu11, 0.9.3-1ubuntu12), libgcc1:amd64 (1:8.2.0-12ubuntu1, 1:8.2.0-13ubuntu1), libss2:amd64 (1.44.4-2ubuntu1, 1.44.5-1), samba-libs:amd64 (2:4.8.4+dfsg-2ubuntu2, 2:4.9.2+dfsg-2ubuntu1), binutils-x86-64-linux-gnu:amd64 (2.31.1-10ubuntu1, 2.31.1-11ubuntu1), libext2fs2:amd64 (1.44.4-2ubuntu1, 1.44.5-1), libgcc-8-dev:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), nautilus:amd64 (1:3.26.4-0ubuntu9, 1:3.30.4-1ubuntu1), libnautilus-extension1a:amd64 (1:3.26.4-0ubuntu9, 1:3.30.4-1ubuntu1), libtsan0:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), libgtk-3-bin:amd64 (3.24.1-1ubuntu2, 3.24.2-2ubuntu2), libubsan1:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), gir1.2-glib-2.0:amd64 (1.58.1-1, 1.58.2-1), g++-8:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), gcc-8:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), ucf:amd64 (3.0038, 3.0038+nmu1), gnome-shell-common:amd64 (3.30.1-2ubuntu3, 3.30.1-2ubuntu4), libgail-3-0:amd64 (3.24.1-1ubuntu2, 3.24.2-2ubuntu2), python3-pkg-resources:amd64 (40.5.0-1, 40.6.2-1), liblsan0:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), libgomp1:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), libsmbclient:amd64 (2:4.8.4+dfsg-2ubuntu2, 2:4.9.2+dfsg-2ubuntu1), binutils-common:amd64 (2.31.1-10ubuntu1, 2.31.1-11ubuntu1), plymouth:amd64 (0.9.3-1ubuntu11, 0.9.3-1ubuntu12), python3-gi:amd64 (3.30.2-1, 3.30.4-1), libbinutils:amd64 (2.31.1-10ubuntu1, 2.31.1-11ubuntu1), libgnutls30:amd64 (3.6.4-2ubuntu2, 3.6.5-2ubuntu1), libedit2:amd64 (3.1-20180525-1, 3.1-20181209-1), nautilus-data:amd64 (1:3.26.4-0ubuntu9, 1:3.30.4-1ubuntu1), gnome-shell:amd64 (3.30.1-2ubuntu3, 3.30.1-2ubuntu4), gtk-update-icon-cache:amd64 (3.24.1-1ubuntu2, 3.24.2-2ubuntu2), libatomic1:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), libharfbuzz0b:amd64 (2.1.1-1build1, 2.2.0-1), libcc1-0:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), plymouth-theme-ubuntu-logo:amd64 (0.9.3-1ubuntu11, 0.9.3-1ubuntu12), libreoffice-help-en-us:amd64 (1:6.1.3-0ubuntu9, 1:6.1.4-0ubuntu1), libstdc++6:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1), tree:amd64 (1.7.0-5, 1.8.0-1), linux-generic:amd64 (4.18.0.11.12, 4.19.0.9.10), libgpg-error-l10n:amd64 (1.32-3, 1.33-3), libstdc++-8-dev:amd64 (8.2.0-12ubuntu1, 8.2.0-13ubuntu1)
End-Date: 2018-12-19  15:14:47

```

---

### Post by Smask on 2018-12-29
I don't know if the screensaver uses parts of the lock screen functionality. I usually don't lock the screen when the screen blanks, maybe I  should. When I click on the pause button on my laptop, it hibernates and can be brought back with a swift flick of the USB mouse. But on my media computer the pause button makes it sleep and I have to press the power button because sleeping cuts all the USB power.
Corrado posted about the 3.30 about a week ago and it was about that time I've got the login troubles with Flashback.

---

### Post by mc4man on 2018-12-29
Well if nautilus was ready to be used at 3.30 it wouldn't still be in proposed.

---

