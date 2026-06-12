---
title: "How can I permenantly turn off screen rotation?"
date: 2018-03-24
forum: Ubuntu Development Version
---

### Post by exploder on 2018-03-24
I have an HP 17-121 wm laptop I am running 18.04 on. The screen rotates randomly all the time! It happens on the GDM even in the middle of logging on and at all kinds of crazy random times! I have searched online for a way to kill this feature with no luck. The button for the feature seems to do nothing. This is driving me crazy! Is there a way to get rid of this feature or permanently turn it off?

---

### Post by #&amp;thj^% on 2018-03-24
This has been an issue since 17.10 and possibly earlier.

FTR: "xrandr" does not work on Wayland.

See if this helps:
```

gsettings set org.gnome.settings-daemon.peripherals.touchscreen orientation-lock true
```

Additionally,[B] the below command ought/should disable the orientation plugin completely.
[/B]
```

gsettings set org.gnome.settings-daemon.plugins.orientation active false
```

Also, gnome provides an option to rotate the screen from Settings->>>Devices->>>Displays->>>Orientation setting (search for displays in Activities)
Which you say it dose not work.

---

### Post by exploder on 2018-03-25
Thanks! I ran both commands. Hope it takes care of that extremely annoying behavior permanently.

---

### Post by exploder on 2018-03-28
Well, that worked fo a few days... This morning when I booted up the GDM appeared sideways. After logging on the desktop rotated to normal but this is by far the most annoying problem I have ever dealt with.

---

### Post by simonsoelberg on 2018-08-13
> **1fallen said:**
> 
```

gsettings set org.gnome.settings-daemon.peripherals.touchscreen orientation-lock true
gsettings set org.gnome.settings-daemon.plugins.orientation active false
```



This seems to have fixed a similar problem on my computer (rotating the laptop would make the screen go blank or flip upside down, now it doesn't). Thanks! :) 

(Ubuntu 18.04, HP Zbook 15)

---

### Post by Glasairman on 2018-09-30
> **simonsoelberg said:**
> This seems to have fixed a similar problem on my computer (rotating the laptop would make the screen go blank or flip upside down, now it doesn't). Thanks! :) 

(Ubuntu 18.04, HP Zbook 15)

Make your life easier with dconf-editor & follow the chain as in the gsettings  you were recommended  by others above

---

### Post by slickymaster on 2018-10-01
18.04 is no longer in development stage

Thread closed

---

