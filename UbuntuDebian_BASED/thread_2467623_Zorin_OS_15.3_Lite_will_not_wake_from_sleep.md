---
title: "Zorin OS 15.3 Lite will not wake from sleep"
date: 2021-10-02
forum: Ubuntu/Debian BASED
---

### Post by ardouronerous on 2021-10-02
I've installed Zorin OS 15.3 Lite on my Dell Inspiron E1505 from 2006, it has 1GB RAM and a 120GB SSD, I've set my swapfile from the default 2GB to 4GB to get more mileage out of my limited RAM. 

Everything was going smoothly until I left to go take a shower. When I got back, the laptop was asleep and when I tried to move my mouse, the screen wouldn't appear, all I'm left with is a blank screen, forcing me to press my power button to shut off the laptop and turn it on again. I've tried to stop my laptop from going to sleep by disabling my screensaver and lockscreen, setting screen blank after to 0  minutes on both battery and plugged in, still the same result, my laptop goes to sleep.

I've done research on this issue and apparently it's a known issue on Zorin OS Lite: [https://forum.zorin.com/t/zorin-lite-will-not-wake-from-sleep-suspend/](https://forum.zorin.com/t/zorin-lite-will-not-wake-from-sleep-suspend/)

One solution that I found is to install Caffeine:

```
sudo apt-get install caffeine
```

And I've set caffeine-indicator to run on startup:

```
cp '/usr/share/applications/caffeine-indicator.desktop' '/home/<username>/.config/autostart/'
```

But during startup, I have to activate it manually:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289230&stc=1[/IMG]

Is there a way to activate it during startup automatically?

---

### Post by indirbak on 2021-10-02
thanks

---

### Post by ardouronerous on 2021-10-03
I've found the solution to make Caffeine activate on startup: [https://www.reddit.com/r/linuxquestions/comments/q08qkz/is_there_a_way_to_make_caffeine_activate_on/hf6g81q/](https://www.reddit.com/r/linuxquestions/comments/q08qkz/is_there_a_way_to_make_caffeine_activate_on/hf6g81q/)

I've created a [FONT=courier new]**caffeinate.desktop**[/FONT] file and saved it in my [FONT=courier new]**autostart**[/FONT] folder and I restarted my laptop.

```
[Desktop Entry]
Icon=caffeine
Name=Caffeinate
Comment=Deactivate the screensaver and sleep mode
Exec=/usr/bin/caffeinate DISPLAY=:0
Terminal=false
Type=Application
Categories=Utility;
Keywords=Screensaver,Power,Saving,Blank
StartupNotify=false
```

Looks like this worked, it's been 18 minutes and my laptop hasn't gone to sleep yet.

---

### Post by ardouronerous on 2021-10-05
[COLOR=#D7DADC]UPDATE: Doesn't work. It went to sleep again. I have no idea why though because it worked before. Damn.

[/COLOR]

---

### Post by ardouronerous on 2021-10-05
UPDATE: Managed to fix it by replacing [FONT=lucida console]**Exec=/usr/bin/caffeinate DISPLAY=:0**[/FONT] with [FONT=lucida console]**Exec=/usr/bin/caffeinate sleep 9999999**[/FONT], this apparently keeps your computer up for just under 116 days or until you logout or shutdown:

> Source: [https://askubuntu.com/a/814844](https://askubuntu.com/a/814844)

```
[Desktop Entry]
Icon=caffeine
Name=Caffeinate
Comment=Deactivate the screensaver and sleep mode
**Exec=/usr/bin/caffeinate sleep 9999999**
Terminal=false
Type=Application
Categories=Utility;
Keywords=Screensaver,Power,Saving,Blank
StartupNotify=false
```

1 hour into testing and no sleep, so it worked.

---

