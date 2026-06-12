---
title: "Various hotkey/touchpad issues 11.10 plus Gnome Shell"
date: 2011-11-22
forum: System76 Support
---

### Post by doubledown11 on 2011-11-22
Just returned to Ubuntu from Fedora 15/16.  I am running Gnome Shell on an otherwise stock 11.10 install.  My hardware is a Gazelle Ultra (GAZU1).

After dozens of unfruitful searches I'm hoping someone can help point me in a good direction to solve the following issues:

1. Brightness hotkeys have stopped working 
- acpi_video0 is the one that responds from the terminal
```
ls /sys/class/backlight
acpi_video0  intel_backlight
```

2. Play/Pause hotkey no longer works with players other than Banshee
- used to work with other players like Pithos

3. Suspend and Power buttons do not function 
- same was true in Fedora w/ Gnome 3

4. Two finger scrolling has stopped working
- seems to have started with Gnome 3.2

---

### Post by isantop on 2011-11-23
> **doubledown11 said:**
> 1. Brightness hotkeys have stopped working 
- acpi_video0 is the one that responds from the terminal

Try installing the System76 driver. You can download it from [http://planet76.com](http://planet76.com). Once it's installed, open it up and run the restore function. 

> **doubledown11 said:**
> 2. Play/Pause hotkey no longer works with players other than Banshee
- used to work with other players like Pithos

When did it work with other players? Was it Fedora, or a previous version of Ubuntu?

> **doubledown11 said:**
> 3. Suspend and Power buttons do not function 
- same was true in Fedora w/ Gnome 3

Try these from Unity. I suspect this could be an issue in Gnome Shell.

> **doubledown11 said:**
> 4. Two finger scrolling has stopped working
- seems to have started with Gnome 3.2

Make sure you have two-finger scrolling enabled in the touchpad settings.

---

### Post by doubledown11 on 2011-11-23
Thanks for the quick response.  Probably worth noting that all the issues described above exist when logged in to Unity as well.  

> **isantop said:**
> Try installing the System76 driver. You can download it from [http://planet76.com](http://planet76.com). Once it's installed, open it up and run the restore function. 

I should have mentioned in my original post that I had already installed System76 Driver app and run the restore function.  No love...

> **isantop said:**
> When did it work with other players? Was it Fedora, or a previous version of Ubuntu? 

Definitely worked in Fedora 15 (Gnome 3.0) and as recently as Ubuntu 10.10.

> **isantop said:**
> Try these from Unity. I suspect this could be an issue in Gnome Shell.

Logged in with Unity now... suspend function key and power button do nothing.

> **isantop said:**
> Make sure you have two-finger scrolling enabled in the touchpad settings.

I should have mentioned this too... I have two finger scrolling enabled in the touchpad settings and it is not working.  This worked like a champ in Fedora 15/16... can't remember whether I tried it in previous versions of Ubuntu.

---

