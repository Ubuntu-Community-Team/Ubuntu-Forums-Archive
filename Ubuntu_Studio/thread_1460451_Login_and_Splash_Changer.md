---
title: "Login and Splash Changer"
date: 2010-04-22
forum: Ubuntu Studio
---

### Post by Spawn1980 on 2010-04-22
Hi All'
I just install ubuntu studio 9.10 and I can't find a way to change my login or splash screen. I've tried the steps below and got a error

**Steps I tried:**

1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.
[B]
Error I GOT:
[/B]
(gnome-control-center:3934): Unique-DBus-WARNING **: Unable to open a connection to the session bus: Failed to connect to socket /tmp/dbus-y6UxF9c83H: Connection refused

(gnome-control-center:3934): Unique-DBus-WARNING **: Unable to connect to the running instance, aborting.
beat@Beat:~$

---

### Post by wojox on 2010-04-22
Try [GDM2]("http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html")

---

### Post by Spawn1980 on 2010-04-22
> **wojox said:**
> Try [GDM2]("http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html")
OK so far so good! I got login screen gdm2setup installed but after I pick a picture from art gnome (fusion login) and click OK it don't do anything just sits there. Any Ideas?

---

### Post by wojox on 2010-04-24
No you would have to revert back to the old GDM to use that login screen.

---

### Post by Spawn1980 on 2010-04-24
So what type of login require GDM2?

---

### Post by wojox on 2010-04-25
For GDM2 your stuck with a wallpaper and that box that you select to log in. There is no wallpaper only with the log in option like your looking for.

---

### Post by Spawn1980 on 2010-04-25
> **wojox said:**
> For GDM2 your stuck with a wallpaper and that box that you select to log in. There is no wallpaper only with the log in option like your looking for.
So my best option is to revert back to Regular GDM.. Now How do I do that? Bare with me i'm still getting a handle of ubuntu after coming from Windows for SOOO many years..

---

### Post by wojox on 2010-04-26
Never actually done it but [Ubuntu-Geek]("http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html") shows a way.

---

