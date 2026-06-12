---
title: "mouse warp override"
date: 2010-10-22
forum: Wine
---

### Post by gufide on 2010-10-22
How do I force the mouse warping? I didn't see it in wine regedit:

[ATTACH]173172[/ATTACH]

I'm in wine 1.3.5

---

### Post by bobwyajnr on 2010-10-22
> **gufide said:**
> How do I force the mouse warping? I didn't see it in wine regedit:

[ATTACH]173172[/ATTACH]

I'm in wine 1.3.5

@OP

I would do the mouse warp override as:
```

REGEDIT4

[\HKEY_CURRENT_USER\Software\Wine\AppDefaults\*executable name*\DirectInput]
"MouseWarpOverride"="force"
```


Where .exe is the main executable of the program (e.g. *Bioshock.exe* - note: not the full path) that you to want to have mouse warping. I did a global mouse warping (to fix the problem of not being able to turn 360 degrees in Bioshock) however this ended up breaking other games...

Global mouse warping is the key ( at your own risk :P ):
```

REGEDIT4

[\HKEY_CURRENT_USER\Software\Wine\DirectInput]
"MouseWarpOverride"="force"
```

There are 3 values for the value:
enable : (default) warp pointer when mouse exclusively acquired
disable : never warp the mouse pointer
force : always warp the mouse pointer

Symptoms of an application not liking the "force"ed mouse warping include the mouse pointer bouncing around erratically in the middle of the screen and 'elastically' returning immediately to the middle of the screen... :oops:

BTW I am using WINE 1.3.5 as well - so you should be good to go!!
:popcorn:

Bob

---

### Post by gufide on 2010-10-22
but... I can't find it in my wine regedit, what should I do?

[ATTACH]173221[/ATTACH]

I can see AppDefaults or DirectInput in "\HKEY_CURRENT_USER\Software\Wine"

---

### Post by bobwyajnr on 2010-10-22
> **gufide said:**
> but... I can't find it in my wine regedit, what should I do?

[ATTACH]173221[/ATTACH]

I can see AppDefaults or DirectInput in "\HKEY_CURRENT_USER\Software\Wine"

Sorry my bad...

You want to select one of the two options I gave you (an application specific override or a global override).

[LIST=1]
[*]Go into your home folder (in Nautilus).
[*]Create a blank document. Call this something like **WINE_mouse_override.reg**.
[*]Copy the information from one of the code windows in my post (beginning **REGEDIT4**).
[*]Paste this information into your newly created blank document - currently open in **Gedit**(I presume).
[*]Remember to insert in the executable name of your application (if using an application specific override)
[*]Open a terminal window (**Gnome Menu** - **Accessories** - **Terminal**).
[*]type or copy/paste into the terminal window:
```

cd ~
wine regedit WINE_mouse_override.reg
```
[/LIST]

Then check in your WINE registry editor that the new key has been created...

Bob

[U]
A bit off topic...[/U]
NB if you are not sure what the applications executable name is... Try typing the following a console while the game/program is running in WINE:
```

ps aux | grep '.exe '

```
If you are running it fullscreen you can access a TTY terminal by type **CTRL+ALT+F1**. Remember that **CTRL+ALT+F7** will take you back to your X-Session!! The TTY console are really useful if your system goes a bit **** up... No need to reboot like windows just use some like the following in TTY1:
```

sudo pkill gdm
startx

```
Kills the Gnome desktop manager process (as root). Then restart your X session!!

---

### Post by gufide on 2010-10-23
Thank you very much, I was able to put that in my wine regedit.

---

### Post by bobwyajnr on 2010-10-23
np :popcorn:

---

### Post by jfgencarnacao on 2010-11-01
Hello everyone.

I followed the steps bobwyajnr posted, but im given this error: 

regedit: setValue failed to open key \HKEY_CURRENT_USER\Software\Wine\DirectInput

any idea on what might be going on?

I also tried adding the key manually through regedit, but i still can't turn 360 degrees :(

---

### Post by jfgencarnacao on 2010-11-01
I rebooted the computer and added manually through regedit and it worked. Thought it may help other people with problems out there.

---

