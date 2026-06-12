---
title: "Unlock GNOME Lock Screen with Command"
date: 2017-10-22
forum: Security
---

### Post by Jason_Hunter on 2017-10-22
I want to unlock the gnome lock screen with a command: 

loginctl unlock-sessions --no-ask-password

, but it says: 

Could not lock sessions: Interactive authentication required.

Is there any way I could unlock it non interactively?

I know I can script this, but I'd rather not. 

Is there some other way?


I mean, I should be able to unlock my own lock screen without password, if I'm already logged in as the same user.

---

### Post by Crafty Kisses on 2017-10-29
Are you running this from an SSH session? Some commands come to mind you can try 

```
DISPLAY=:0 gnome-screensaver-command -d
```

You can toggle DBus as well if need be, for example 

```

          export DISPLAY=:0
          dbus-send --session \
          --dest=org.gnome.ScreenSaver \
          --type=method_call \
          --print-reply \
          --reply-timeout=20000 \
          /org/gnome/ScreenSaver \
          org.gnome.ScreenSaver.SetActive \
          boolean:false
```

---

### Post by Jason_Hunter on 2017-10-29
actually, sudo [COLOR=#000000]loginctl unlock-sessions does work

would your dbus command work?

Don't you need some kind of authentication?

Also, is the lock screen of gnome handled by a screensaver?

[/COLOR]

---

