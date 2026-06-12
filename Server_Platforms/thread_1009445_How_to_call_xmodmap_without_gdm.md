---
title: "How to call xmodmap without gdm?"
date: 2008-12-12
forum: Server Platforms
---

### Post by gilgongo on 2008-12-12
I'm trying to start an X application automatically when my Ubuntu Hardy box starts up. To minimise system overhead, I'm not loading gdm though. I've got it all working OK (auto-login, X starts, so does the app).

However, I need to re-map some keys (the application is a strange one). For some reason, it's just not happening though. I've put some xmodmap commands in my home directory where I have my .xinitrc file. The ~/.xinitrc file looks like this:

#!/bin/sh
xmodmap ~/.xmodmap
xeroG --standalone

xeroG is my app - that starts up fine, but X seems to ignore ~/.xmodmap.

I've also tried:

1. Adding a call to ~/.xmodmap in /etc/X11/Xsession

2. Adding the same call to a file in /etc/X11/Xsession.d/

3. Trawling through the logs looking for any clues

4. Taking all my clothes off, covering myself in chocolate, then begging.

None of which has worked.

If I run startx from a terminal manually, the xmodmap file IS read though.

Anyone have any clues?

---

### Post by lykwydchykyn on 2008-12-12
Did the log files you checked include ~/.xsession-errors?  That's where I'd expect a problem to show up.

EDIT: I should add, when I've done similar things I usually put the commands in ~/.xsession rather than ~/.xinitrc.  I'm not completely sure what the difference is, but I have understood in the past that there is a difference in the way environment variables are handled and so forth, and that in debian (and thus Ubuntu) it is preferred to use .xsession.

---

### Post by kerry_s on 2008-12-12
strange, are you using ~/.profile to startx?

---

### Post by gilgongo on 2008-12-13
OK - I've tried changing .xinitrc to .xsession (and kept the permissions). That appears to make no difference.

If I try using ~/.profile or ~/.session instead of .xinitrc, I get this in my .xsession-errors file:

Xsession: X session started for tv at Sat Dec 13 11:49:34 GMT 2008
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ScreenSaver was not provided by any .service files
CRITSEC[0x8bcde24]: Trying to enter destroyed section.
CRITSEC[0x8bcde24]: Trying to leave destroyed section.
CRITSEC[0x8bcde24]: Trying to enter destroyed section.
CRITSEC[0x8bcde24]: Trying to leave destroyed section.
CRITSEC[0x8bcf320]: Trying to enter destroyed section.
CRITSEC[0x8bcf320]: Trying to leave destroyed section.
CRITSEC[0x8bcf320]: Trying to enter destroyed section.
CRITSEC[0x8bcf320]: Trying to leave destroyed section.
CRITSEC[0x8bcf320]: Trying to enter destroyed section.
CRITSEC[0x8bcf320]: Trying to leave destroyed section.
Xsession: X session started for tv at Sat Dec 13 11:52:01 GMT 2008
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ScreenSaver was not provided by any .service files
CRITSEC[0x8bcde24]: Trying to enter destroyed section.
CRITSEC[0x8bcde24]: Trying to leave destroyed section.
Xsession: X session started for tv at Sat Dec 13 11:56:09 GMT 2008
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/tv:/tmp/.ICE-unix/5987
** Message: another SSH agent is running at: /tmp/ssh-syghoz5961/agent.5961
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Window manager warning: Failed to read saved session file /home/tv/.metacity/sessions/default0.ms: Failed to open file '/home/tv/.metacity/sessions/default0.ms': No such file or directory

Also, none of my external drives are mapped any more, and various weird things happen like gdm starts up (I see a Gnome desktop) and complains that it can't find stuff like user switcher.

This is totally strange - can't Ubuntu start an X session properly without gdm running? 

BTW, the other modification I've made (apart from disabling gdm at startup using rcconf) is to changed /etc/events.d/tty1 to use "exec /sbin/mingetty --autologin myname tty1" instead of "exec /sbin/getty 38400 tty1" 

At this rate, I'm going to have to take the resource hit and load gdm and a bunch of usless Gnome stuff just to run one app!

---

### Post by olejorgen on 2008-12-13
That should work.. Have you checked /var/log/Xlog.X.log ?

---

### Post by gilgongo on 2008-12-13
I've had a look at /var/log/Xorg.0.log and there's no errors (nothing marked with EE or !!), no mention of xmodmap or anything.

It seems that X is either ignoring the xmodmap call in .xsession (or .xinitrc), or something else is stepping in and trashing the settings.

I'm going to try a completely clean command line install, install xorg only then try again.

---

### Post by gilgongo on 2008-12-13
..

---

### Post by kerry_s on 2008-12-13
that's try again.
how are you running the command for "startx".
most people put it in ~/.profile so when the autologin logs you in X automatically starts, .xinitrc is read and so on.

i have mine setup to skip startx and go straight to xinit.

---

### Post by gilgongo on 2008-12-13
I'm not running startx - the app is an X app, so I need X, but I don't need any windowing environment, so I'm not loading gdm.

Loading X isn't the problem - all that's fine, the app works, my environment is perfect but for the fact that xmodmap isn't able to do its stuff.

---

### Post by kerry_s on 2008-12-13
> **gilgongo said:**
> I'm not running startx - the app is an X app, so I need X, but I don't need any windowing environment, so I'm not loading gdm.

Loading X isn't the problem - all that's fine, the app works, my environment is perfect but for the fact that xmodmap isn't able to do its stuff.

in that case put 
**exec xmodmap $HOME/.xmodmaprc **
in to ~/.profile and when you log in it will get executed, just like if you were starting X from there.

put all your start up stuff there to be executed. i believe ~/.bashrc is also read as soon as your logged in, so that can be used as well, just so you know.

---

### Post by olejorgen on 2008-12-13
How are you running X? I didn't think any script got executed if you just ran vanilla X. ie. ```

$ X &
```
But I guess it is run if the app start. Maybe try adding export DISPLAY=:0 ?

---

### Post by gilgongo on 2008-12-14
> **kerry_s said:**
> in that case put 
**exec xmodmap $HOME/.xmodmaprc **
in to ~/.profile and when you log in it will get executed, just like if you were starting X from there.

Hmm. I tried that, but then various external drive mappings disappear, gdm appears to start up (I see a desktop before the app launches) and I get weird errors about not being able to find gnome applets and things.

I'm going to try various setups in virtual machines to see if I can solve this. There must be some strange property of xmodmap's interaction with X that makes keysyms revert to some default thing I can't override. Either that, or I've inadvertently set something in Gnome/gdm that does this (what, I have no clue).

At least the fact that everyone tells me things should work OK makes me hopeful it's just some glitch in my setup.

---

### Post by gilgongo on 2008-12-14
> **olejorgen said:**
> How are you running X? 

I wish I knew.

The way I think it's working is that on login (which is automatic), Ubuntu sees the .xsession file in my home dir, and starts the app which requires X, so it starts X in some way as part of starting the app. 

What I suppose I could try is some horrific hack like put an at job into .xsession to run the xmodmap call say, 5 seconds after the app launches. Whoa what a brain-dead hack *that* would be!

---

### Post by gilgongo on 2008-12-14
**Holy, screaming, baaaaaby Moses.**

It turns out that my problem DOES NOT have a solution do do with xmodmap:

[http://thomer.com/howtos/kxkb_xmodmap.html](http://thomer.com/howtos/kxkb_xmodmap.html)

I suspected there might be something up with xkb, and indeed there is.

So - now I'm off to get my head around porting my (not inconsiderable) xmodmap calls to a custom keyboard mapping for xkb.

Whoda thunk it? ):P

---

### Post by kerry_s on 2008-12-14
> **gilgongo said:**
> Hmm. I tried that, but then various external drive mappings disappear, gdm appears to start up (I see a desktop before the app launches) and I get weird errors about not being able to find gnome applets and things.

I'm going to try various setups in virtual machines to see if I can solve this. There must be some strange property of xmodmap's interaction with X that makes keysyms revert to some default thing I can't override. Either that, or I've inadvertently set something in Gnome/gdm that does this (what, I have no clue).

At least the fact that everyone tells me things should work OK makes me hopeful it's just some glitch in my setup.

that means you have gnome installed.
if you have a desktop/window manager it gets tied to the xsession automatically, in that case you run through that. if this is a desktop your converting, it means you didn't remove enough.
you should be using cli or server install instead than just adding X(sudo apt-get install xorg) that way you don't get what you don't want and things won't get in the way of what your trying to do.

---

### Post by gilgongo on 2008-12-16
> **kerry_s said:**
> that means you have gnome installed.
if you have a desktop/window manager it gets tied to the xsession automatically, in that case you run through that. if this is a desktop your converting, it means you didn't remove enough.
you should be using cli or server install instead than just adding X(sudo apt-get install xorg) that way you don't get what you don't want and things won't get in the way of what your trying to do.

That's what I thought too, so I tried a couple of different installs on some virtual machines. Even if I go for a cli install and then apt-get xorg on its own, it turns out that you cannot use xmodmap to configure the keyboard when X starts up. It'll simply ignore it and use xkbd instead. Xmodmap is in effect deprecated when starting X. You can only use it to re-write keysms after X has started - which is too late in my case.

So - I've started the long march into writing an xkbd file that ports my xmodmap calls. I'm gradually getting there, but the lack of sleep and food is beginning to take it's toll on my health. I fear I may never succeed.

---

### Post by kerry_s on 2008-12-16
i think that's tied to that auto xorg problem. i've seen a setting on the arch forum that disables the auto detection.
give that a read see if it can help. good luck
[http://wiki.archlinux.org/index.php/Xorg#Keyboard_Settings](http://wiki.archlinux.org/index.php/Xorg#Keyboard_Settings)

---

### Post by gilgongo on 2008-12-23
Thanks - I'll give that a go.

---

