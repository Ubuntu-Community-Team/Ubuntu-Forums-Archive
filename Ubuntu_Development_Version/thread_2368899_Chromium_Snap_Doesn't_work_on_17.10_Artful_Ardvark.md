---
title: "Chromium Snap Doesn't work on 17.10 Artful Ardvark"
date: 2017-08-16
forum: Ubuntu Development Version
---

### Post by lsmith33990 on 2017-08-16
I just tried install my first snap.  Never installed one before.

So I tried "snap install --candidate chromium"

It installed fine.  But when I load it all I get is a black screen within the Chromium window.  It eventually times
out and asks me if I want to "Force Quit".  I tried "Wait" and nothing happens.  I also noticed that Ubuntu takes longer to boot when that particular snap is installed.

Side Note:  I tested it under my admin account and have autologin set up and no keyring PW.

Anyone have any solutions or similar experience?

I've heard it depends on gnome keyring and was wondering if thats the issue, but even so, it should still work if I choose
a blank keyring password for loggin in automatically at boot.

---

### Post by ventrical on 2017-08-16
Try systemd-analyze blame and see what that reports.

Regards..

---

### Post by ventrical on 2017-08-16
Installed, run in (unity) terminal and got these:

```

ventrical@ventrical-Precision-WorkStation-T3400:~$ chromium
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
[3082:3159:0816/153453.065205:ERROR:connection.cc(1963)] History sqlite error 5, errno 0: database is locked, sql: CREATE TABLE meta(key LONGVARCHAR NOT NULL UNIQUE PRIMARY KEY, value LONGVARCHAR)
[3082:3082:0816/153453.998451:ERROR:desktop_window_tree_host_x11.cc(1155)] Not implemented reached in virtual void views::DesktopWindowTreeHostX11::InitModalType(ui::ModalType)
[3082:3255:0816/153506.797964:ERROR:udev_watcher.cc(60)] Failed to begin udev enumeration.
ventrical@ventrical-Precision-WorkStation-T3400:~$ 


```

---

### Post by ventrical on 2017-08-16
logoff/logon -> works fine now in unity.

---

### Post by ventrical on 2017-08-16
Can't find a way to  stop pop-up adds from opening in tabs. Preferences does not seem to work.

---

### Post by mc4man on 2017-08-16
> **lsmith33990 said:**
> I just tried install my first snap.  Never installed one before.

So I tried "snap install --candidate chromium"

It installed fine.  But when I load it all I get is a black screen within the Chromium window.  It eventually times
out and asks me if I want to "Force Quit".  I tried "Wait" and nothing happens.  I also noticed that Ubuntu takes longer to boot when that particular snap is installed.

Side Note:  I tested it under my admin account and have autologin set up and no keyring PW.

Anyone have any solutions or similar experience?

I've heard it depends on gnome keyring and was wondering if thats the issue, but even so, it should still work if I choose
a blank keyring password for loggin in automatically at boot.

If you're using a wayland session then it probably won't work & likely not the only snap to fail with wayless

---

