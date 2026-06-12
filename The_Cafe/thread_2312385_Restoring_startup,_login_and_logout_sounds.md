---
title: "Restoring startup, login and logout sounds"
date: 2016-02-04
forum: The Cafe
---

### Post by seanos on 2016-02-04
For some reason (see proverb about cats & curiosity) I’ve been investigating how to make Ubuntu noisy again. This seems to be a little messy, which I guess is one of the reasons the devs dropped these in the first place, and I’m not sure I really understand how it used to be done anyway. I thought I’d share what I’ve figured out and see if anyone can add to it.

**[SIZE=3]Themes[/SIZE]**
There is a [freedesktop.org spec]("http://www.freedesktop.org/wiki/Specifications/sound-theme-spec/") for sound themes, but Ubuntu doesn’t really seem to have a (easily discoverable) mechanism for choosing a theme.

Themes are installed in folders under [FONT=courier new]/usr/share/sounds[/FONT] and can be selected using *dconf Editor* at [FONT=courier new]/org/gnome/desktop/sound/theme-name[/FONT] or on the command line:
```
gsettings set org.gnome.desktop.sound theme-name "ubuntu"
```

**[SIZE=3]Playing sounds[/SIZE]**
To use the freedesktop abstracted sound names (according to your theme) the command to use (at least in 14.04) is
```
canberra-gtk-play --id=<sound-name>
or
canberra-gtk-play -i <sound-name>

e.g.
canberra-gtk-play -i system-ready
canberra-gtk-play -i desktop-login
canberra-gtk-play -i desktop-logout
```

There are plenty of other options for playing sounds, but they will require a direct path to the file (e.g. paplay, aplay) and so ignore themes.

**[SIZE=3]Triggering the sounds[/SIZE]**
This is where things get messy.

**desktop-login**
There seem to be two options here. What I’m guessing is the original method still seems to work, but the one most commonly suggested (#2) might be a little easier to tweak.

Either…


[LIST=1]
[*][FONT=courier new]gksu gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop[/FONT] and change this line to true:

[FONT=courier new]X-GNOME-Autostart-enabled=true[/FONT]

(assumes [FONT=courier new]/org/gnome/desktop/sound/event-sounds[/FONT] is set to true in dconf)

OR 
[*]Create a new entry in Startup Applications that runs [FONT=courier new]canberra-gtk-play -i desktop-login[/FONT] (or a script running canberra-gtk-play) 
[/LIST]

Both of these work for me, but the start of the sound is cut off. I suppose this might be fixed by a script doing something like 
```
[FONT=courier new]canberra-gtk-play -f /home/you/silent.wav
[FONT=courier new]canberra-gtk-play -i desktop-login[/FONT][/FONT]
``` to wake up the system or maybe [FONT=courier new]sleep 1 && canberra-gtk-play -i desktop-login[/FONT]. if it’s just happening too early.

**desktop-logout**
I’ve read a lot of articles about these sounds in the last couple of days, but almost all of them are about a login sound (even ones that seem to be about a startup sound). The one method I’ve read for logout uses [FONT=courier new]lightdm.conf[/FONT].

You could just put a command directly into the file, but I prefer to call a script.

[FONT=courier new]gksu gedit /etc/lightdm/lightdm.conf[/FONT] and add a [FONT=courier new]session-cleanup-script[/FONT] under [FONT=courier new][SeatDefaults][/FONT] (if the file doesn’t exist you could just add the following)…
```
[SeatDefaults]
session-cleanup-script=/home/you/bin/lightdm-session-cleanup
```

Then create the /home/you/bin/lightdm-session-cleanup script…
```
#!/bin/bash

/usr/bin/canberra-gtk-play -i desktop-logout
```

This more or less works for me though, once again, the sound can be cut off early.

Inexplicably, one theme which uses different naming, refuses to acknowledge [FONT=courier new]desktop-logout[/FONT] no matter whether I link or copy the relevant file, but [FONT=courier new]canberra-gtk-play -i ending[/FONT] (not in the list of standard names) works.

**system-ready**
This used to be that familiar drum sound you heard when Ubuntu started up. I cannot figure out how to get this to play.

It looks like [FONT=courier new]canberra-gtk-play[/FONT] requires something that hasn’t started when the greeter appears (Pulseaudio?), but I haven’t had any luck using [FONT=courier new]aplay[/FONT] either. I’ve only tried running it from a [FONT=courier new]lightdm.conf greeter-setup-script[/FONT] but the result is that I end up in low graphics mode and can’t get any further without opening a console, editing files and rebooting.

I suppose there are other ways to achieve this, but I suspect there will be similar problems of what audio is available at the time.

Comments?

---

### Post by QIII on 2016-02-04
Moved to The Cafe.  Not a support request.

---

### Post by seanos on 2016-02-04
OK. I suppose that qualifies as a species of comment, though I&#8217;m really not sure this counts as &#8220;lighthearted and enjoyable discussions, such as you might find around a water cooler at work&#8221;&#8230;at least not anywhere I&#8217;ve worked.

---

