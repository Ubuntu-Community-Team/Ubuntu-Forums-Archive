---
title: "Default Screen Brightness"
date: 2013-02-24
forum: Ubuntu Development Version
---

### Post by mykrob on 2013-02-24
My son has a new Lenovo G580, and it works great with 13.04, except for one minor thing... How can I set the default screen brightness? He has to manually increase the brightness once the laptop is booted up, because it wants to black out the screen for some reason.

---

### Post by Toz on 2013-02-25
Have a look at this thread ([http://ubuntuforums.org/showthread.php?p=12279200]("http://ubuntuforums.org/showthread.php?p=12279200")) and the **acpi_backlight=vendor** kernel boot parameter.

If that doesn't work, what video card do you have? This command might help:
```
sudo lspci -vnn | grep -A12 VGA
```

---

### Post by nismoryco on 2013-02-25
I seem to have the opposite problem (my screen is too bright). I've been using xbacklight to set the back light level when I log in. I created a file ~/.config/autostart/xbacklight.desktop with the following contents:

```

[Desktop Entry]
Name=Backlight
GenericName=Set backlight
Comment=Lowers backlight to a reasonable level
Exec=xbacklight -set 40
Terminal=false
Type=Application
Categories=Utility;
StartupNotify=false

X-GNOME-Autostart-enabled=true

```

The value after -set is the percentage of back light.

---

