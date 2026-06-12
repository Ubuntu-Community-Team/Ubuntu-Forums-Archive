---
title: "Battery alarm won't disable"
date: 2015-11-21
forum: System76 Support
---

### Post by scar3 on 2015-11-21
i have the low battery alarm disabled in the BIOS settings on my lemur laptop, but the alarm still sounds when the battery is low.  Tthe sound is very loud and annoying.  The laptop will last another 20 minutes without being plugged in so the battery level isn't properly being detected anymore anyways.  I found that if i mute my audio then the beep stops but i obviously cannot listen to anything anymore.  If i turn the volume back on even to just 1% the battery alarm is audible again at full volume.   I remember there used to be a mixer somewhere that could control the internal speaker and so if i could find that again then maybe i could mute that and fix this problem.  I have ubuntu 14.04

---

### Post by Geoffrey_Arndt on 2015-11-21
System Settings>Sound>Sound Effects Tab> . . . adjust volume or mute alarm.

---

### Post by scar3 on 2015-11-22
> **Geoffrey_Arndt said:**
> System Settings>Sound>Sound Effects Tab> . . . adjust volume or mute alarm.

thanks but i think that is just the alert sound like when ubuntu boots and the login screen is ready... i already have that turned down all the way and the slider is in the OFF position too.  

the battery alarm is this loud annoying beep that repeats every few seconds and it is extremely loud

---

### Post by Geoffrey_Arndt on 2015-11-22
The "askUbuntu" help site often includes fixes or customizations that are a bit more suited for intermediate or advanced users.   So, adjusting the low battery warning sound appears to be one of those, requiring some "Terminal" commands:

BTW . . . fully discharging a laptop battery can totally ruin it . . . and many of these batteries are not easy to replace without some research and work.    Another solution is to get an external battery you could use when the first warning sounds.

[URL="http://askubuntu.com/questions/571911/how-do-i-disable-low-and-critical-battery-notifications-in-14-10"]http://askubuntu.com/questions/571911/how-do-i-disable-low-and-critical-battery-notifications-in-14-10


[/URL]

---

### Post by scar3 on 2015-11-23
> **Geoffrey_Arndt said:**
> The "askUbuntu" help site often includes fixes or customizations that are a bit more suited for intermediate or advanced users.   So, adjusting the low battery warning sound appears to be one of those, requiring some "Terminal" commands:

BTW . . . fully discharging a laptop battery can totally ruin it . . . and many of these batteries are not easy to replace without some research and work.    Another solution is to get an external battery you could use when the first warning sounds.

[URL="http://askubuntu.com/questions/571911/how-do-i-disable-low-and-critical-battery-notifications-in-14-10"]http://askubuntu.com/questions/571911/how-do-i-disable-low-and-critical-battery-notifications-in-14-10


[/URL]

thanks i took a look at that and tried to adjust the relevant settings.... it hasn't stopped the alarm yet.  below are all of my power settings:

```

$ gsettings list-recursively org.gnome.settings-daemon.plugins.power
org.gnome.settings-daemon.plugins.power button-power 'interactive'
org.gnome.settings-daemon.plugins.power critical-battery-action 'nothing'
org.gnome.settings-daemon.plugins.power percentage-low 1
org.gnome.settings-daemon.plugins.power priority 0
org.gnome.settings-daemon.plugins.power lid-close-suspend-with-external-monitor false
org.gnome.settings-daemon.plugins.power idle-dim false
org.gnome.settings-daemon.plugins.power button-hibernate 'hibernate'
org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 'suspend'
org.gnome.settings-daemon.plugins.power button-sleep 'suspend'
org.gnome.settings-daemon.plugins.power button-suspend 'suspend'
org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout 0
org.gnome.settings-daemon.plugins.power time-low 1200
org.gnome.settings-daemon.plugins.power lid-close-ac-action 'nothing'
org.gnome.settings-daemon.plugins.power notify-perhaps-recall true
org.gnome.settings-daemon.plugins.power percentage-critical 1
org.gnome.settings-daemon.plugins.power percentage-action 1
org.gnome.settings-daemon.plugins.power sleep-inactive-battery-type 'suspend'
org.gnome.settings-daemon.plugins.power time-action 120
org.gnome.settings-daemon.plugins.power lid-close-battery-action 'nothing'
org.gnome.settings-daemon.plugins.power idle-brightness 30
org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
org.gnome.settings-daemon.plugins.power time-critical 300
org.gnome.settings-daemon.plugins.power active true
org.gnome.settings-daemon.plugins.power use-time-for-policy false
$ 
```

---

### Post by Geoffrey_Arndt on 2015-11-23
Well, there is always dconf editor, but we're getting into territory that I haven't worked with personally so I'm not confident in the risks of these edits.   I really don't understand . . . personally, I would NEVER run a laptop past the critical alarm point.   Couldn't pay me to do it.   But, each to their own.

---

### Post by scar3 on 2015-11-23
> **Geoffrey_Arndt said:**
> Well, there is always dconf editor, but we're getting into territory that I haven't worked with personally so I'm not confident in the risks of these edits.   I really don't understand . . . personally, I would NEVER run a laptop past the critical alarm point.   Couldn't pay me to do it.   But, each to their own.  well you could pay me to do it, about $125, because that's what a new battery from system76 is.  unless you know of a reputable "aftermarket" brand/company that can offer a decent warranty and guarantee the battery won't explode?  otherwise i'll take my 20+ extra minutes of battery life while i still can.... and i'll see if askubuntu can be any help.

---

