---
title: "Laptops fail to hibernate when battery is critically low"
date: 2009-11-18
forum: System76 Support
---

### Post by HotShotDJ on 2009-11-18
Due to a bug (probably in the new DeviceKit-Power module) in Karmic, many laptop users, including System76 laptops, have found that their laptops will not hibernate when the battery is critically low.  Instead, the laptops simply loose power, risking data loss and damage to the battery itself.

Fortunately, there is a rather easy "work-around" that will restore your laptop's ability to hibernate at the appropriate time when your battery reaches a critically low state.

Open a terminal and execute the following commands:
```
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type int --set /apps/gnome-power-manager/thresholds/percentage_action 5
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type int --set /apps/gnome-power-manager/thresholds/percentage_critical 6
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type int --set /apps/gnome-power-manager/thresholds/percentage_low 10
```
Unless you have edited these parameters in your regular user account, once you log out and then log back in, these new settings will take effect and will become the default setting for all users.  When your battery reaches 10% remaining, you will receive a low battery warning.  At 6%, you will receive a battery critical warning. At 5%, your laptop will hibernate. (assuming you have not changed the default action set by System76 Driver).

WARNING:  The gnome defaults for percentage_critical and percentage_action are too low!  Do not set those values below 6 and 5 respectively or your laptop may not start the hibernation action in time to prevent a power-loss condition.  If you have an older battery that is not in good condition, you may want to set these values higher.

ThomasAaron:  Is it possible for the System76 Driver developers to add these settings to base_system.py in the System76 Driver.  Until the root problem is fixed upstream, these settings should really be the default to prevent users from loosing data or damaging their hardware.

---

### Post by thomasaaron on 2009-11-19
Hi, HotshotDJ.

I'm white-boarding this and will discuss it with our driver dev when he returns from UDS.

If it works on our in-house testing, I'm betting it will make a bee-line straight for the driver.

---

### Post by stewpac on 2009-11-21
Ummmm, for what it's worth, since the upgrade on my panp4n it hibernates when the battery is critically low even though I have it set to shutdown. Actually, hibernate is better - I didn't use it before because it was a little flaky and it hardly ever came up. The recovery from hibernate is very fast so I'm definitely *not* complaining. I just thought you might want to know the opposite 'problem' is out there too so you don't squash one bug and create another (if you can help it)

---

### Post by HotShotDJ on 2009-11-21
> **stewpac said:**
> Ummmm, for what it's worth, since the upgrade on my panp4n it hibernates when the battery is critically low even though I have it set to shutdown.The problem you describe is quite different from the problem dealt with here.  In the case of the the PanP5 (and other -- but not all -- laptops), gnome-power-manager is not detecting when the battery has reached a critical level, so no action is being triggered at all.  For your PanP4, it looks like the critical level is being detected, but the wrong action is being triggered.  But just to be sure... can you tell me if power manager (from the "battery icon" in your system tray) is correctly estimating the time remaining when running on battery?

While I realize that the behavior your are experiencing is not a problem for you, I still think we should look at why it isn't doing what you've told it to do -- that is, why is it hibernating rather than shutting down when the battery's critical level is detected.  Would you be so kind as to execute the following command and post the output?:```
gconftool-2 --recursive-list /apps/gnome-power-manager | grep critical_battery
```

---

