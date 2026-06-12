---
title: "Compiled WINE w Xinput2 (2xi) support-- grabs ALL input regardless of active window"
date: 2010-09-30
forum: Wine
---

### Post by teddyk on 2010-09-30
Hi,

In attempt to fix the mouse escape/boundary issues associated with infamous bug 6971, I have patched WINE with support for the new xinput2 (2xi). You can see the bug details and find the patch here:

[http://bugs.winehq.org/show_bug.cgi?id=6971](http://bugs.winehq.org/show_bug.cgi?id=6971)

THE GOOD NEWS: Mouse issues are fixed. Mouselook works like a charm and the pointer is no longer warping to the middle of the game screen in Everquest.

THE BAD NEWS: It looks like 2XI is grabbing *ALL* mouse/keyboard input. Meaning I can drag my game to a different view-port, minimize it and be working on another application in another view-port... and my game will still be grabbing input and doing stuff in the background. This is especially troublesome because I like to run 2 instances of EverQuest (and "play" with myself so to speak)... this is not possible with this issue because both EverQuest clients will be grabbing the same input simultaneously, regardless of the fact that they are running out of separate prefixes and such.

I am brainstorming possible fixes for this but my technical ability is quite limited...

One idea I have is possibly running the games in a separate X process? Would this work... and how the heck would I go about doing that effectively?

I am running Ubuntu 10.04 32-bit. Also I am using wine source 1.1.33 as it is the most recent version which will run Everquest titanium.

Many thanks for taking the time to read this and any efforts toward helping me solve this frustrating problem! I've come so far already, I hope this is not the end of the line!

teddy

---

### Post by Half-Left on 2010-09-30
This seems to happen in Halo as well but I set in Wine the Virtual Desktop to my screen resolution and it works ok.

---

### Post by teddyk on 2010-09-30
> **Half-Left said:**
> This seems to happen in Halo as well but I set in Wine the Virtual Desktop to my screen resolution and it works ok.

I did that initially, but no joy...

I wouldn't even notice the issue I think if I wasn't trying to run two copies of the game at the same time... but yeah when I'm playing on one character I see my other character running around and doing stuff from the input. :(

---

### Post by teddyk on 2010-09-30
> **teddyk said:**
> Hi,

In attempt to fix the mouse escape/boundary issues associated with infamous bug 6971, I have patched WINE with support for the new xinput2 (2xi). You can see the bug details and find the patch here:

[http://bugs.winehq.org/show_bug.cgi?id=6971](http://bugs.winehq.org/show_bug.cgi?id=6971)

THE GOOD NEWS: Mouse issues are fixed. Mouselook works like a charm and the pointer is no longer warping to the middle of the game screen in Everquest.

THE BAD NEWS: It looks like 2XI is grabbing *ALL* mouse/keyboard input. Meaning I can drag my game to a different view-port, minimize it and be working on another application in another view-port... and my game will still be grabbing input and doing stuff in the background. This is especially troublesome because I like to run 2 instances of EverQuest (and "play" with myself so to speak)... this is not possible with this issue because both EverQuest clients will be grabbing the same input simultaneously, regardless of the fact that they are running out of separate prefixes and such.

I am brainstorming possible fixes for this but my technical ability is quite limited...

One idea I have is possibly running the games in a separate X process? Would this work... and how the heck would I go about doing that effectively?

I am running Ubuntu 10.04 32-bit. Also I am using wine source 1.1.33 as it is the most recent version which will run Everquest titanium.

Many thanks for taking the time to read this and any efforts toward helping me solve this frustrating problem! I've come so far already, I hope this is not the end of the line!

teddy

I worked around this issue by launching the game process in it's own xsession via the "x.game" script found on this forum.

Now I just wish switching TTY was faster...

---

### Post by jehiva on 2010-11-16
Sorry if this bumps an older thread, but can someone explain exactly how to run that patch?

---

