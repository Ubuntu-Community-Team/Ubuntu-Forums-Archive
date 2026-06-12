---
title: "Dropbox icon refuses to go in the system tray, Tint2 + Openbox on Pop!_OS"
date: 2021-06-30
forum: Ubuntu/Debian BASED
---

### Post by zano on 2021-06-30
Hi,
I have installed openbox and tint2 on pop!_OS aund use openbox as WM.
Dropbox system tray icon just sits at the top left corner of my screen instead of in the normal system tray area in tint2.
(screenshot attached) 
[ATTACH=CONFIG]288754[/ATTACH]

I've installed dropbox with the usual command:
```
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
```

I've found an old thread on Archlinux forum:
[https://bbs.archlinux.org/viewtopic.php?id=187289]("https://bbs.archlinux.org/viewtopic.php?id=187289")

thank you in advance.

---

### Post by zano on 2021-07-01
If I launch Dropbox from terminal:
```
ste@pop-os:~$ ~/.dropbox-dist/dropboxd
dropbox: locating interpreter
dropbox: logging to /tmp/dropbox-antifreeze-KEKWXE
dropbox: initializing
dropbox: initializing python 3.8.10
dropbox: setting program path '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/dropbox'
dropbox: setting python path '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474:/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/python-packages.zip'
dropbox: python initialized
dropbox: setting args
dropbox: running dropbox
dropbox: applying overrides
dropbox: enabling allocator metrics
dropbox: running command
dropbox: load fq extension '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/cryptography.hazmat.bindings._openssl.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/cryptography.hazmat.bindings._padding.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/psutil._psutil_linux.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/psutil._psutil_posix.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/apex._apex.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/tornado.speedups.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/wrapt._wrappers.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/PyQt5.QtWidgets.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/PyQt5.QtCore.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/PyQt5.QtGui.cpython-38-x86_64-linux-gnu.so'
dropbox: load fq extension '/home/ste/.dropbox-dist/dropbox-lnx.x86_64-125.4.3474/PyQt5.QtDBus.cpython-38-x86_64-linux-gnu.so'

```

---

