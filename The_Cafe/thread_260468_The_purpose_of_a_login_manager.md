---
title: "The purpose of a login manager"
date: 2006-09-18
forum: The Cafe
---

### Post by g4c9z on 2006-09-18
It seems to me that (on an interactive desktop system) a login manager should be the main program started by the window system, and should perform the following tasks:

1. Let users log in
2. Let users shut down, reboot, hibernate, standby, etc. the computer
3. Manage multiple users logged in at once, and the switching of users once one is logged in
4. When configured to do so, automatically log a user in at startup

This is in contrast to a window manager, whose purpose is to manage the viewing areas of multiple graphical applications started in a single login session, which is in contrast to a desktop environment, whose purpose is to install a collection of unrelated software which is like other software except that it sometimes doesn't work in other environments.

Now, first, is my understanding of the purpose of login managers correct?  If so, then you should be able to use any login manager with any window manager, right?  And if /that's/ true, then could someone please either tell me how I can do #3 above with gdm (the login manager installed by default on Ubuntu), or point me to a login manager with which I can?  In gnome, of course, there's a dialog that pops up when you click "Quit" from the panel, but this isn't there in other window managers.  It seems best to have a command you can run to inform the currently running instance of the login manager to do things, like switch to another user (leaving the current desktop session active, of course).  This would allow this functionality to be added to whatever menu/keyboard shortcut/etc. people prefer.  But "man gdm" didn't say anything about that.

Am I correctly understanding the way login managers should work, or am I completely off my rocker here?

---

### Post by Bloodfen Razormaw on 2006-09-18
You can manage different users being logged in at once by having more than one X display.  Each display will have its own display manager and a user can log into each.  You can do this with any login manager or desktop, but it is nicer to have it integrated into the desktop.  KDE has had this integrated into every part of its desktop, and the support is very mature.  GNOME's support for user switching is poor and quite new, but (mostly) works.

In the worst case, since each display is mapped to a vt, you can Ctrl+Alt+Fn (where n is the number for the vt) to switch users.  GNOME hides the info of what vty is assigned to which user, so you might have to guess if there are more than a couple.  By default, vt7 (Ctrl+Alt+F7) will be the first X display; adding a second user will result in an X display on vt8 (Ctrl+Alt+F8).

Also, login managers serve another vital purpose: security.  Without a login manager you normally let each user start his own X display.  To do this X must be suid root, which means a flaw in X potentially gives users a means of privilege escalation.  Login managers should always be used on multiuser systems.

---

### Post by darkhatter on 2006-09-18
users can already start x. just log on as a normal user type in startx done. KDM should do everything you need g4c9z. I have no idea how to remove gdm and make ubuntu use kdm, the only way I can tell you is hacking init, but that may be changed when ubuntu comes out with that new startup thing

---

### Post by TravisNewman on 2006-09-18
you can apt-get install kdm, and when you do so a box will come up asking which one you want to use

---

### Post by Wolki on 2006-09-18
> **g4c9z said:**
> Now, first, is my understanding of the purpose of login managers correct?  If so, then you should be able to use any login manager with any window manager, right?  And if /that's/ true, then could someone please either tell me how I can do #3 above with gdm (the login manager installed by default on Ubuntu), or point me to a login manager with which I can?  In gnome, of course, there's a dialog that pops up when you click "Quit" from the panel, but this isn't there in other window managers.  It seems best to have a command you can run to inform the currently running instance of the login manager to do things, like switch to another user (leaving the current desktop session active, of course).

Try "gdmflexiserver", it seems to do what you want.

---

### Post by g4c9z on 2006-09-23
> Try "gdmflexiserver", it seems to do what you want.

Thanks; I didn't know about that.  It almost does what I want.  If run from
gnome, it does exactly what I want; but if run in another environment (I tried
it from Ion), it gave an error "gnome-screensaver-Message: Screensaver is not
running!", entered a bunch of enter characters in my terminal, and most
importantly, didn't lock the screen, which, to some degree, defeats the purpose
of separate user logins.  Another example of a program that would
be very useful, if it worked in any environment; but in gnome, it's useless
anyway because you can already switch users from the "Quit" command.  But I
guess it will suit my purposes.

That command should be better documented, too, because it seems pretty useful.

As to the other comments:

Bloodfen - So you're saying that the proper way to do it is to have each virtual terminal start its own instance of a login manager?  I guess that seems pretty reasonable, and reduces the burden of each login manager needing to handle that functionality.  But how can I set that up?  I tried putting:

6:23:respawn:/sbin/getty -l /usr/sbin/gdm 38400 tty6

in /etc/inittab but Ctrl+Alt+F6 still gives me a console login.  Then when I try to login from that VT, it gives an error that GDM is already running.  Anyway, why wouldn't Ubuntu set that up already?

darkhatter - I tried startx, and it just said there's a server error because X windows is already running.

And why does everyone think I want to switch to KDM?  I'm speaking/asking in general about the way things should be.

---

### Post by Bloodfen Razormaw on 2006-09-23
> Bloodfen - So you're saying that the proper way to do it is to have each virtual terminal start its own instance of a login manager? I guess that seems pretty reasonable, and reduces the burden of each login manager needing to handle that functionality. But how can I set that up?
This is how it will work automatically.  To have two users logged in to a graphical environment at once you must have a separate X display for each, and each X display must go in its own vt (well, there is an Xnest, but that doesn't sound like what you want).  When you use gdmflexiserver or KDE's fast user switching it will automatically start a new X display on a new VT.  Since a single display manager will manage multiple X displays, you won't be able to manually start multiple display managers on multiple VTs by simple means.

We bring up KDM because KDM does exactly what you want. :P  In general things should be the way KDM does things.  GNOME was very late to the user switching game, so it doesn't do it very well yet.  Hence it doesn't work as well with GDM.  There is no "way things should be" separate from the display manager because the display manager is what should manage that.

And startx isn't what you want.  Startx is something to be used instead of a display manager.  It lets each user start their own X server, instead of a service (the display manager) spawning an X server for you.  This is a very bad solution, because X requires root to run.  Startx uses suid root, so you provide a possible security problem.

---

### Post by g4c9z on 2006-09-23
> This is how it will work automatically.

No it doesn't; what I described is to have multiple instances of a (graphical) login manager on each virtual terminal.  It gives me a console login.  It doesn't make sense to have every other terminal give me a console login; console sessions are only useful for installation/configuration and servers, not for everyday desktop use.

> There is no "way things should be" separate from the display manager because the display manager is what should manage that.

Actually, you've kind of got me convinced that there should be one display manager instance on each virtual terminal.  The only reason I can think of to not do that is efficiency - having multiple copies of X is expensive.  But it seems to be happening anyway, so that's not an issue.  Multiple copies of the display manager isn't an issue, because it is, or should be, a small program, as far as I can tell.

> We bring up KDM because KDM does exactly what you want. :P

Does it work normally in other environments?  I ask because I've had bad experiences with KDE - it taking over my sound system and stuff like that.  If it's just a normal login manager, I might install it and try that.  How can I use KDM to switch users when I'm not running KDE, like if I was running Ion or something?

By the way, any ideas why X has to be started by root?

---

### Post by g4c9z on 2006-09-23
> what I described is to have multiple instances of a (graphical) login manager on each virtual terminal

Whoops; I meant "an instance of a (graphical) login manager on each virtual terminal"

---

### Post by Bloodfen Razormaw on 2006-09-23
> No it doesn't; what I described is to have multiple instances of a (graphical) login manager on each virtual terminal. It gives me a console login. It doesn't make sense to have every other terminal give me a console login; console sessions are only useful for installation/configuration and servers, not for everyday desktop use.
You can tell your system not to start getty on those VTs by editing inittab, but there is no reason to.  With a display manager your display will be the X display on boot, and new X11 VTs will be started as needed.  You should *always* have at least one tty in case X fails to start for some reason.  If you remove the getty entries, at least leave tty1.

> Actually, you've kind of got me convinced that there should be one display manager instance on each virtual terminal. The only reason I can think of to not do that is efficiency - having multiple copies of X is expensive. But it seems to be happening anyway, so that's not an issue. Multiple copies of the display manager isn't an issue, because it is, or should be, a small program, as far as I can tell.
You must have a separate copy of X for each X server on each display, but it is not costly since most of that memory is shared.  The same goes for the display manager.  When a new display manager is started for a new user, very little new memory is needed.  You do have a separate display manager for each display, but it won't replace the console.

> Does it work normally in other environments? I ask because I've had bad experiences with KDE - it taking over my sound system and stuff like that. If it's just a normal login manager, I might install it and try that. How can I use KDM to switch users when I'm not running KDE, like if I was running Ion or something?
KDM will work with any desktop.  You just have to make a session file for it.  You can switch users from KDM without logging in.  By default (unless you theme it) the login display has a Menu button with a Switch User menu with these operations.  However, you lose integration with things like kscreensaver, which will let you switch users from a locked screen.  Fast user switching is only easy if both the desktop and display manager support it (it sounds like your only real problem with GDM is a lack of a menu for switching; Ctrl+Alt+F8 should take you to the second user).  I'm not sure if GNOME's fast user switching works generically or if it forces you to use gdmflexiserver.
 
> By the way, any ideas why X has to be started by root?
For fast use X requires direct access to your hardware.  There are other ways to run X, which might not require root (I'm not sure about that), but startx is suid by default, so you should avoid it unless it is necessary.

---

### Post by Bloodfen Razormaw on 2006-09-23
Also, if you want to have X servers start on a tty from boot, so you have multiple X displays from the start, kdm supports that.  If you install it, you can view the help files for it on that subject.  It can configured with a list of static X servers.  gdm can probably do that as well, but I don't have it installed so I can't tell you much on that.  You might try to view its man pages.

---

### Post by g4c9z on 2006-09-23
> You can tell your system not to start getty on those VTs by editing inittab, but there is no reason to.

That's not what I meant; I meant there's no reason for Ubuntu to not start a graphical login manager on the other terminals.  (I thought it starts a console login by default, but now that I think of it, maybe it doesn't; that may well be something I configured and then forgot about.)

> However, you lose integration with things like kscreensaver, which will let you switch users from a locked screen.

> You must have a separate copy of X for each X server on each display, but it is not costly since most of that memory is shared.

Then I'm confused as to why it shouldn't be the case that when my computer starts, there are multiple login managers started which I can switch between with Ctrl+Alt+Fn, or even some other means.  This would simplify the login managers and yield a common means of switching users no matter whether your login manager supports it or not, and render things like gdmflexiserver unnecessary.

> it sounds like your only real problem with GDM is a lack of a menu for switching; Ctrl+Alt+F8 should take you to the second user

Maybe that's my problem.  It doesn't.  It gives me a black screen with a cursor blinking in the top left.

> However, you lose integration with things like kscreensaver, which will let you switch users from a locked screen.

Ah, that seems to be another problem.  You're saying locking the screen is a function of the screensaver?  Surely that's a poor design choice.  Locking the screen is a user management issue, so should be performed by the login manager, I would think; it has nothing to do with screensavers.

---

### Post by Bloodfen Razormaw on 2006-09-23
> Then I'm confused as to why it shouldn't be the case that when my computer starts, there are multiple login managers started which I can switch between with Ctrl+Alt+Fn, or even some other means. This would simplify the login managers and yield a common means of switching users no matter whether your login manager supports it or not, and render things like gdmflexiserver unnecessary.
This is doable, but requires you configure the display manager, not inittab.  e.g. kdm has a StaticServers option in its configuration files that lets you list X displays to use.  You might also try using inittab if you use KDM, but make sure that your KDM entries take a specific tty as an argument so it won't try to open on vt7 every time.  gdm lacks the ability to take a tty argument IIRC, but may have something like StaticServers in its own configuration.

> Then I'm confused as to why it shouldn't be the case that when my computer starts, there are multiple login managers started which I can switch between with Ctrl+Alt+Fn, or even some other means.
This would be an unreasonable default, since it is not discoverable (how would average users know to use Ctrl+Alt+Fn?), and because the display manager/desktop can spawn new X displays as necessary.  The fast user switching features are just a dynamic way of doing the same thing.

> Ah, that seems to be another problem. You're saying locking the screen is a function of the screensaver? Surely that's a poor design choice. Locking the screen is a user management issue, so should be performed by the login manager, I would think; it has nothing to do with screensavers.
Desktops use screensavers for locking because they are more generalized (they don't require a specific display manager, or any at all), and they can have a simpler design that way, which means they are less prone to failure (and failure in a locking program means that your desktop becomes unlocked).

---

### Post by g4c9z on 2006-09-23
> This is doable, but requires you configure the display manager, not inittab. e.g. kdm has a StaticServers option in its configuration files that lets you list X displays to use. You might also try using inittab if you use KDM, but make sure that your KDM entries take a specific tty as an argument so it won't try to open on vt7 every time. gdm lacks the ability to take a tty argument IIRC, but may have something like StaticServers in its own configuration.

Thanks; and I intend to try that at some point.  But I'm still trying to think of what an ideal system configuration would be.  It still seems like a cleaner approach to remove the "switch users" functionality from login managers, and let user switching happen by switching virtual terminals.  This way X-Windows would support user switching without any new code.

> This would be an unreasonable default, since it is not discoverable (how would average users know to use Ctrl+Alt+Fn?)

That's why I added "or even some other means".  If KDE or GNOME want to be user friendly, they could provide a "switch user" command which switches to a new virtual terminal.  See man chvt.

I guess one potential problem here is that it's convenient to show on the "switch users" menu which users are logged in in other sessions, like KDE does.  I'm not sure this is easy without requiring each login manager to handle it (which seems unacceptable), or adding an extra parameter to the X-Windows interface so that programs can query which terminals have users logged in.

> because the display manager/desktop can spawn new X displays as necessary. The fast user switching features are just a dynamic way of doing the same thing.

Why not then have a command to X to start a new display if it's needed?  I.e. if there are already 99 X servers running, let chvt 100 start a 100th instance of X, and open some default login manager.

Overall, why not do both?  Statically create multiple instances of your favorite login manager, and dynamically let the login manager create new X-Windows instances on new virtual terminals when users choose to use a login manager that can do that?  I guess if Ubuntu wants to stick with a pure Gnome installation, it can't do that because gdm can't do multiple static instances.

---

### Post by g4c9z on 2006-09-23
I wrote this script, which works well enough for my purposes:

```
#!/bin/sh

#Switch users in a non-KDE or Gnome environment, using gdm, the Gnome login manager

#Run gnome-screensaver to allow the screen to be locked
gnome-screensaver

#Run gdmflexiserver to start a new login window and X session
gdmflexiserver

#You can switch between them with Ctrl+Alt+Fn.  New sessions usually get F8, F9, etc.

```

This way I can switch users from e.g. Ion by running this script, and it still locks my screen.

I still think GDM and/or Ubuntu could do a better job of setting this up by default, but anyway.

---

