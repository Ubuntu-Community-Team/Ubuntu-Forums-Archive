---
title: "CS:Source Non-Steam"
date: 2009-06-03
forum: Wine
---

### Post by tehkane on 2009-06-03
Program I'm trying to run is Counter-Strike: Source (Non-Steam). It opens up, but no text or dialogue boxes are visible. It requires a few alt+tabs to view them. Even then, I need to hover the mouse below what I'm trying to click in order to click it. 

Terminal output: [http://halpme.pastebin.com/m30284de4](http://halpme.pastebin.com/m30284de4)

 Wine version is 1.0.1 Running Ubuntu 8.10 64bit with nvidia-glx-180  Wine settings are all the defaults.

EDIT: My xorg.conf, in case it's needed: [http://halpme.pastebin.com/m6a803839](http://halpme.pastebin.com/m6a803839)

---

### Post by Bloemetjesgordijn on 2009-06-03
hi

why are you using an old wine version, I think currently wine is @ 1.1.22

cheerz

---

### Post by asdfoo on 2009-06-03
why are you using non-steam? The only people who use non-steam CSS are people who pirate the game?

---

### Post by tehkane on 2009-06-04
I've updated WINE to the newest build which seems to have fixed the no text/dialogues at startup. The mouse will still registering clicks too high up, but I fixed that by setting CS:S to use the same resolution as Gnome.

I'm still getting a few errors, though > [http://halpme.pastebin.com/m2993de6e](http://halpme.pastebin.com/m2993de6e)


[LIST=1]
[*]err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16B16A16_FLOAT
[*]err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
[*]err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
[*]err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1280x1024x32 @60! (XRandR)
[*]err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16B16A16_FLOAT
[*]err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16B16A16_FLOAT
[*]err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16B16A16_FLOAT
[*]err:d3d:getColorBits Unsupported format: WINED3DFMT_R16G16B16A16_FLOAT
[*]err:d3d:getColorBits Unsupported format: WINED3DFMT_R32_FLOAT
[*]err:d3d:getColorBits Unsupported format: WINED3DFMT_R32_FLOAT
[*]err:d3d:getColorBits Unsupported format: WINED3DFMT_R32G32B32A32_FLOAT
[*]err:d3d:getColorBits Unsupported format: WINED3DFMT_R32G32B32A32_FLOAT
[/LIST]
 I'm guessing those err:ole errors are due to a missing DDL or something... But I don't know which. The GUID says it's for WBEM Locato, but I'm not sure how to install that into WINE.

Those d3d errors look as if they're for setting colours on whatever. So I guess they're not overly important.

The X11 error is pretty obvious but I'm not sure how to fix that. My xorg.conf has no resolutions set in it. So would adding them fix that? If so, how do I do that?

And I do run the Steam version of CS:S. This is just so I can play with friends at LAN's on those rare occasions. So don't worry, I'm still paying for it.

EDIT: Disabling smilies >.<

---

### Post by asdfoo on 2009-06-04
ignore those, they are not something you can fix but just debug information for wine developers

---

### Post by tehkane on 2009-06-05
What about fixing a 'Visual C++ Runtime Error - Terminated in an unusual way' error.

That pops up when ever I try to move (in game). I've tried using winetricks to install various packages which I've seen in google searches, but still nothing. Any ideas?

---

### Post by tehkane on 2009-06-06
Never mind. The WINE update fixed all my problems.

Much love to the devs <3

---

### Post by jedihopeful on 2011-04-11
:-|[SIZE="4"]Why doesnt my css play? when i click new game, it just freezes at the message "Initializing game. Please help[-o<"[/SIZE]

---

