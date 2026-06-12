---
title: "Workspace Switching"
date: 2013-07-14
forum: Ubuntu Development Version
---

### Post by PJs Ronin on 2013-07-14
I think this started with the change with Gnome (3.6 and 3.8 effected) going to vertical, as against horizontal, workspaces.   Now, when I make a move from one workspace to another I get this not too subtle indicator.

[ATTACH=CONFIG]244732[/ATTACH]

Anyone know how to reduce the size or make it less intrusive?

---

### Post by SPK201 on 2013-07-15
Now that you mention it, on Unity only switching horizontally works (CTRL + ALT + Arrow).

---

### Post by monkeybrain2012 on 2013-07-15
ctrr+ alt+up or down would work.

---

### Post by zika on 2013-07-15
> **SPK201 said:**
> Now that you mention it, on Unity only switching horizontally works (CTRL + ALT + Arrow).
That depends how You've selected Your work-spaces to be arranged... I think that 1x4 (#_in_Vx#_in_H) is default arrangement...
If You have default arrangement You can not go Up/Down...

---

### Post by SPK201 on 2013-07-15
I just ticked the box for Workspaces in the system settings. < 13.10 it worked for both directions. Thus I don't understand what you mean with default arrangement, ain't there just one default option?

---

### Post by zika on 2013-07-15
> **SPK201 said:**
> I just ticked the box for Workspaces in the system settings. < 13.10 it worked for both directions. Thus I don't understand what you mean with default arrangement, ain't there just one default option?
I do not have default now... I always change it to 4x4... (I've corrected my mistake in my previous post...)
As far as I remember default was always 1 level (vertically)  and 4 WS in horizontal line...

To read current state:
0. ```
gconftool --get /apps/compiz-1/general/screen0/options/hsize
gconftool --get /apps/compiz-1/general/screen0/options/vsize
```

To change current state:
1. CCSM>GeneralOptions>DesktopSize...
or
2. Unity-Tweak-Tool>WorkspaceSettings... (yes, default is 1x4)
or 
3. ```
gconftool --set /apps/compiz-1/general/screen0/options/hsize --type=int some_number_for_example_1234
gconftool --set /apps/compiz-1/general/screen0/options/vsize --type=int some_number_for_example_4321
```

(writing from memory which is old as me...)

---

### Post by mc4man on 2013-07-15
> **PJs Ronin said:**
> I think this started with the change with Gnome (3.6 and 3.8 effected) going to vertical, as against horizontal, workspaces.   Now, when I make a move from one workspace to another I get this not too subtle indicator.

Anyone know how to reduce the size or make it less intrusive?
Don't see any available settings to alter it, maybe some extension somewhere, don't know
(looks a little better here as is more like the notifications

---

### Post by mc4man on 2013-07-15
> **SPK201 said:**
> Now that you mention it, on Unity only switching horizontally works (CTRL + ALT + Arrow).

To note: the default when enabling workspaces is 2x2
It appears the default wall bindings are not setting correctly
So up & down are now super+prior & super+next which translates here to super+page up/down
You can open ccsm > wall > bindings > move within a wall & set back for "move up & move down" to ctrl+alt+arrow_key_up/down

Edit: the defaults are the same as old so in ccsm just click on the button to far right to reset
screen attached to show how it looks by default with incorrect bindings

---

### Post by PJs Ronin on 2013-07-15
> **mc4man said:**
> Don't see any available settings to alter it, maybe some extension somewhere, don't know
(looks a little better here as is more like the notifications

Thank you.   I was beginning to wonder if anyone else had actually read the OP.   I was not questioning how many workspaces there were/are or their geometry, I was seeking advice on how to reduce the size of the popup that appears as shown in the image attached to the OP.   Simple, n'est-ce pas?

---

### Post by zika on 2013-07-16
> **PJs Ronin said:**
> Thank you.   I was beginning to wonder if anyone else had actually read the OP.   I was not questioning how many workspaces there were/are or their geometry, I was seeking advice on how to reduce the size of the popup that appears as shown in the image attached to the OP.   Simple, n'est-ce pas?Mea culpa, I reacted on thred-highjack from @SPK201... Sorry...

---

### Post by PJs Ronin on 2013-07-16
ty zika

---

### Post by mc4man on 2013-07-16
Edit: I don't believe I know if you settled on Gs or flashback with compiz - if the latter then below is irrelevant..

I guess if one knew about Gs/clutter & .js files it would be possible to make some changes to the switcher popup, myself do neither.
(it's /usr/share/gnome-shell/js/ui/workspaceSwitcherPopup.js

And just to note that Gs is quite picky about it's .js's, one little error in one .js & it won't start up, so messing with requires either one doesn't care or has a backup plan to fix. (those are both for me.

Anyway, maybe because I'm a lefty my focus on the display is pretty much the left 2/3's, the far right is sorta out of the way. 
So it was pretty easy move the pop up to the far right & lower the display time just a bit, the default is 600ms which is about right though I did lower to 400

---

