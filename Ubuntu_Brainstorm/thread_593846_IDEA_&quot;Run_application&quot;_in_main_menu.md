---
title: "IDEA: &quot;Run application&quot; in main menu"
date: 2007-10-27
forum: Ubuntu Brainstorm
---

### Post by tomplast on 2007-10-27
I don't want to say "in Windows there is..." but I must in this case. In windows you can easily find the "Run application" in the main menu. I use it quite often in Ubuntu and I know a few who do that as well, so my suggestion is that we put the "Run application" into the main menu in Ubuntu so it's easily reachable.

What do you think?

EDIT: YES, ALT+F2 is the shortcut for "Run application" but this should ease things up a bit, even for me who uses the terminal every day.

---

### Post by kellemes on 2007-10-27
Doesn't ALT-F2 work in Gnome?

---

### Post by Can+~ on 2007-10-27
Alt+F2 does the same thing, but I guess it would help newcomers.

I like it. :)

---

### Post by smartboyathome on 2007-10-27
What is the command for it, anyway?

---

### Post by kellemes on 2007-10-27
By the way, isn't there a run-command applet for the Gnome-taskbar?
I'm on KDE and for me it's available.

---

### Post by smartboyathome on 2007-10-27
> **kellemes said:**
> By the way, isn't there a run-command applet for the Gnome-taskbar?
I'm on KDE and for me it's available.

There is, but I would still like to know the command.

---

### Post by tomplast on 2007-10-27
> **smartboyathome said:**
> There is, but I would still like to know the command.

Maybe it's just me but from the looks it's integrated into gnome-panel. When I kill gnome-panel the run-dialog also dies.

---

### Post by smartboyathome on 2007-10-27
> **tomplast said:**
> Maybe it's just me but from the looks it's integrated into gnome-panel. When I kill gnome-panel the run-dialog also dies.

In that case, I don't know if there is a way to add it to the menu. It requires commands to run certain items, so this would have to be separated from GNOME panel in order to add it. :(

---

### Post by Sand Lee on 2007-10-27
I don't see the point in having it in the main menu. If you are going to use a run application, you have the intention of typing in a command to accomplish a certain task. Why use a mouse to get this process started when you can just use the existing Alt+F2 on the keyboard and continue using the keyboard to type your command afterwards?

---

### Post by 23meg on 2007-10-28
The point is discoverability. The counterarguments would be
[list]
[*]that Alt + F2 is one of the best known keyboard shortcuts
[*]that Deskbar is on the panel by default and can serve the same function
[*]that the benefit doesn't justify cluttering up the menus 
[/list]

---

### Post by nooblot on 2008-07-04
Resurrection time

So this is still impossible - adding "Run Application" to Menu - in Hardy ?????

I'm just afraid I get amnesia one day and forget about "Alt+F2".....:)

---

### Post by mc4100 on 2008-07-04
> **23meg said:**
> 
[list]
[*]that Alt + F2 is one of the best known keyboard shortcuts
[/list]
True, this was the first one I memorized after switching to Ubuntu; is just so damn useful. ;)

---

### Post by tomplast on 2008-07-07
You shouldn't have to learn something that should be obvious, ALT+F2 isn't that! I can't remember that I got an epiphany that told me to use ALT+F2 when I installed Ubuntu for the first time :/.

If not anyone fixes this soon then I'll patch the menu myself...

---

### Post by iansyngin on 2008-07-08
what is the command for the Run Command anyway so i can put a launcher in my menu anyway

---

### Post by smartboyathome on 2008-07-08
> **iansyngin said:**
> what is the command for the Run Command anyway so i can put a launcher in my menu anyway

There isn't a command, it is built into the panel itself.

---

### Post by iansyngin on 2008-07-08
are there any other funky shortcuts built into the panel then? i quite like Alt + F2

---

### Post by smartboyathome on 2008-07-08
> **iansyngin said:**
> are there any other funky shortcuts built into the panel then? i quite like Alt + F2

Not a shortcut, but a fun little program, use Alt + F2 then type:

freethefish
:)

---

### Post by tomplast on 2008-07-10
> **smartboyathome said:**
> Not a shortcut, but a fun little program, use Alt + F2 then type:

freethefish
:)

Another thing that is bugging me is that before I could open a folder my writing something like ~/Desktop/ , but not anymore :/. Do you know why this is removed?

---

### Post by iansyngin on 2008-07-10
> **tomplast said:**
> Another thing that is bugging me is that before I could open a folder my writing something like ~/Desktop/ , but not anymore :/. Do you know why this is removed?

where are you writing this, in nautilus?
typing this in the terminal is ok
-
sorry, obviously this is Run.. silly me

---

### Post by iansyngin on 2008-07-10
> **tomplast said:**
> Another thing that is bugging me is that before I could open a folder my writing something like ~/Desktop/ , but not anymore :/. Do you know why this is removed?

think you might need to put "nautilus ~/Desktop"
perhaps it's not using this by default anymore. it maybe an option somewhere

should do the trick

---

### Post by tomplast on 2008-07-14
> **iansyngin said:**
> think you might need to put "nautilus ~/Desktop"
perhaps it's not using this by default anymore. it maybe an option somewhere

should do the trick

Your solution works but I can't understand why any sane person could remove/disable such a useful feature (IMHO).

---

### Post by ckraimer on 2008-09-20
I know this is an old thread, but I tried for quite a while to figure this out - AND I DID!

I used the xte function from xautomation to send key strokes:
xte "keydown Alt_L" "key F2" "keyup Alt_L"

I made that into a script (saved that one line in a text file as .sh), then created a Launcher with the script as the target.  Now the run box can be added everywhere - menus, xfce4-panel, panels, quick-lounge-applet (which is why I did this), etc.

---

### Post by UbuWu on 2008-09-21
It was removed several ubuntu releases ago, before that it was included in the applications menu. There is probably still a gconf key that allows you to re-enable it.

---

### Post by meastp on 2008-09-21
For shortcuts, have a look in preferences->keyboard shortcuts.

ctrl+alt+T opens a terminal, which is useful.

---

### Post by gnomeuser on 2008-09-21
As I recall GNOME2 used to have this feature in the early days, but I can't remember the reasoning behind it's removal. Aside that we might want to replace it with something better than a simple run command, something akin to Spotlight in Mac OS X, a reworked gnome-do maybe?

---

