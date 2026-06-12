---
title: "Failed to start session with LXDE on Ubuntu Server"
date: 2024-03-09
forum: Server Platforms
---

### Post by fabius85 on 2024-03-09
I'm having trouble starting LXDE on Ubuntu Server.

I installed Ubuntu Server 22.04.4 LTS on a VM, logged in and run:
```
sudo apt update && sudo apt upgrade
```
Then installed LXDE:
```
sudo apt install lxde
```
After that i rebooted and when entering the password I got the error message: "[COLOR=#ff0000]Failed to start session[/COLOR]" and nothing else happened.
If installing **xinit** package i can succesfully start LXDE from the command line with **startx** command.
But this doesn't solve the problem cause if i try to login from LightDM, i always get that message.

The only wordaround i found to make this work is to install **lightdm-gtk-greeter** package, reboot, login from the gtk greeter at least once.
After that i can even remove **lightdm-gtk-greeter** package and purge it, and the default ubuntu greeter for LightDM will work as expected and no longer give "Failed to start session" error.

I'm wondering why that error occurs and if there's a proper way to fix it without the **lightdm-gtk-greeter** workaround.

PS: installing **lubuntu-desktop** package is not an option as i dont need any of the stuff that it comes with. I just need a minimal graphical interface.

---

### Post by MAFoElffen on 2024-03-10
When you install a minimal LXDE or LXQT desktop with LightDM, it is installed without a default pointer to the user-session set in file  /etc/lightdm/lightdm.conf.

When it only has one Desktop installed, it doesn't trigger the process to turn on and populate LightDM's Session Chooser, so you need to tell it which session to use. As you mentioned, if you installed something like ubuntu-desktop, it would trigger that process, because it has two session types (more than one), Ubuntu Xorg & Ubuntu Wayland, so would trigger that process to populate the Session Chooser. 

Of course that would add unwanted fluff. Not what needs to happen with a minimal install goal. 

If you open file /etc/lightdm/lightdm.conf, and look under the Section [SeatDefaults]... By default, on a clean minimal install, here is the default contents:
```

[SeatDefaults]
autologin-user=

```
To get around that error ("Failed To Start Session"), and get it to work, add this line to point a session:
```

user-session=lxde

```
Just one of those things that isn't well documented.

Of course, now that you have installed a desktop on a Server Eition, this thread is now more of a "Desktop" question, but no matters.

---

### Post by fabius85 on 2024-03-10
There was no **/etc/lightdm/lightdm.conf** file, so I created it and added the following content:
```

[SeatDefaults]
user-session=LXDE

```
rebooted and it worked!

I initially tried with user-session=lxde (lowercase) but i still got the "[COLOR=#ff0000]Failed to start session[/COLOR]" error.
I think it's uppercase because there's a "LXDE.desktop" file inside "/usr/share/xsessions/" folder.

It works also this way:
```

[Seat:*]
user-session=LXDE

```

Btw, thank you for the help!

---

### Post by MAFoElffen on 2024-03-10
You are very welcome. Glad that I could explain that for you.

---

