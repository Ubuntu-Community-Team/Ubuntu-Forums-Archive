---
title: "Windows Borders / Resizing Windows"
date: 2011-12-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-12-16
I have always received some complains of users about what most describe as some weirdness or difficulty in resizing windows / placing the mouse cursor exactly in the position in which it changes to the "resize arrow". This come from users that have just migrated from Windows.

In fact, it does work a little different in Ubuntu than in Windows. The mouse cursor turns into an arrow some pixels off the windows borders, but not a single pixel after the border and inside the window area. Some users simply can't put the mouse in the right place as it seems. Apparently (not sure) it has changed somehow in Precise Alpha and becoming more difficult for users (I really can't see the difference, just repeating what users are saying).

Does anyone know of a possible workaround to change / customise the way it works in Ubuntu, distance / sensitivity, etc?

---

### Post by jfernyhough on 2011-12-16
You can ALT+Middle-click and drag to resize the window. It's not obvious, though. Otherwise (without editing the theme) you'd need to change the window theme to one with a border (e.g. using gnome-tweak-tool).

---

### Post by kaldor on 2011-12-16
Borders really need to be much easier to grab. I've been using Linux for 90% of the last 4 years and still have trouble grabbing window borders.

---

### Post by arpanaut on 2011-12-16
The lower right corner has a much larger area of sensitivity.
I've become accustomed to grabbing there, not a solution...
But does make it easier to resize.

---

### Post by bluexrider on 2011-12-16
> **jfernyhough said:**
> You can ALT+Middle-click and drag to resize the window. It's not obvious, though. Otherwise (without editing the theme) you'd need to change the window theme to one with a border (e.g. using gnome-tweak-tool).
then add this 
Alt+F8   Start the resize operation.     arrow keys    Resize the window in the direction of the arrow key.       spacebar     Complete the resize operation, leaving the window at the current size.       Esc     Cancel the resize operation, restoring the window to its original size.

---

### Post by VinDSL on 2011-12-17
Am I the only one using "Love Handles"!?!?!?!  LoL!  :D

Linkage:  [http://www.omgubuntu.co.uk/2011/03/unity-love-handles-resizing-in-ubuntu-just-got-sexy/](http://www.omgubuntu.co.uk/2011/03/unity-love-handles-resizing-in-ubuntu-just-got-sexy/)

---

### Post by ventrical on 2011-12-17
> **jfernyhough said:**
> You can ALT+Middle-click and drag to resize the window. It's not obvious, though. Otherwise (without editing the theme) you'd need to change the window theme to one with a border (e.g. using gnome-tweak-tool).


That worked pretty good.

---

### Post by jerrylamos on 2011-12-18
> **bluexrider said:**
> then add this 
Alt+F8   Start the resize operation.     arrow keys    Resize the window in the direction of the arrow key.       spacebar     Complete the resize operation, leaving the window at the current size.       Esc     Cancel the resize operation, restoring the window to its original size.
Easiest yet!

Wonder why pecise developers decided to make window border movement so hard to do.

Jerry

---

### Post by Claus7 on 2011-12-18
Hello,

ehmm...I'm not exactly sure about what you are talking about, yet if I understood correctly you:
open a window (let's say terminal)
and you would like it to be(come) bigger/smaller.
(Am I correct?)

If affirmative, then from compiz you are able to configure the thickness of the "boards/borders" of the windows, so as not to trouble yourselves to try and find an accurate position for the mouse to resize the window.
Not remember where exactly you are doing this though...

Regards!

---

### Post by effenberg0x0 on 2011-12-18
> **Claus7 said:**
> Hello,

ehmm...I'm not exactly sure about what you are talking about, yet if I understood correctly you:
open a window (let's say terminal)
and you would like it to be(come) bigger/smaller.
(Am I correct?)

If affirmative, then from compiz you are able to configure the thickness of the "boards/borders" of the windows, so as not to trouble yourselves to try and find an accurate position for the mouse to resize the window.
Not remember where exactly you are doing this though...

Regards!

Well, I'm not sure who you're talking to since you quoted no one, but I'm the OP, so that probably is to me. Thank you for your tips. I've been trying very hard to learn how to use a computer for the last two weeks or so, and I think I'm getting there.

---

### Post by jfernyhough on 2011-12-18
> **Claus7 said:**
> If affirmative, then from compiz you are able to configure the thickness of the "boards/borders" of the windows,-snip-> Not remember where exactly you are doing this though...I've trawled through CCSM and can't find anything to configure the border thickness. I'm pretty sure this is theme property (e.g. the theme is "borderless"). Borderless themes became trendy in the last year or two (post-Clearlooks, I think).

---

### Post by mc4man on 2011-12-18
By default 'ambiance' no longer is borderless, it has a 1 px border, otherwise there would be issues with unity-2d.
For ambiance this is set in /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml, lines 14-16

Myself set it back to borderless to get rid of the white line that shows up on the left side of a terminal & with a modded dark sidebar I use for ambiance. I guess it could be increased to 2 or 3 px but it doesn't translate too well visually. The above mentioned keyboard methods seem better.

I've no trouble here resizing with either the default 1 px or 0 px borders

Way back in 11.04 dev I believe there was a padding (7px) that was useful for resizing but if so it was abandoned for issues

---

### Post by effenberg0x0 on 2011-12-18
> **mc4man said:**
> By default 'ambiance' no longer is borderless, it has a 1 px border, otherwise there would be issues with unity-2d.
For ambiance this is set in /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml, lines 14-16

Myself set it back to borderless to get rid of the white line that shows up on the left side of a terminal & with a modded dark sidebar I use for ambiance. I guess it could be increased to 2 or 3 px but it doesn't translate too well visually. The above mentioned keyboard methods seem better.

I've no trouble here resizing with either the default 1 px or 0 px borders

Way back in 11.04 dev I believe there was a padding (7px) that was useful for resizing but if so it was abandoned for issues
  
@mc4man 
Exactly... I found advice online pointing to this section of the theme and made the borders thicker. Maybe it can make things a little  easier for new users. It's not great aesthetically though. I would like to keep them borderless but with an area of about ±3px for resizing. I tested changing a lot of the sections inside the theme, but couldn't find an option in it to set  this. Do you remember if it was a keyword in the theme or just hardcoded? I have never played with theming.

---

### Post by mc4man on 2011-12-18
IIRC the line in that metacity .xml that 'used' to affect this was for example line 418. Now whatever it does do ?, doesn't seem to effect cursor grab.
Messing with it may actually produce some bad behavior or nothing at all.

What I'm remembering in 11.04 dev is that  editing that line did have an effect.
(The padding  was seen when moving a window up against the launcher in dodge mode & windows would open the padding distance away from the launcher. 

So I'm thinking (not knowing), that this was a change in unity itself and or whatever decorator it's using

---

### Post by effenberg0x0 on 2011-12-18
> **mc4man said:**
> IIRC the line in that metacity .xml that 'used' to affect this was for example line 418. Now whatever it does do ?, doesn't seem to effect cursor grab.
Messing with it may actually produce some bad behavior or nothing at all.

What I'm remembering in 11.04 dev is that  editing that line did have an effect.
(The padding  was seen when moving a window up against the launcher in dodge mode & windows would open the padding distance away from the launcher. 

So I'm thinking (not knowing), that this was a change in unity itself and or whatever decorator it's using

I think you're right. Just as a test, I have changed many lines (almost all of them, one by one... argh) to very high / potentially easily detectable values, like 15/30/45px and used the dodge method (smart one dude) to test the distance, but saw no difference at all. This is likely changed somewhere else. But thanks for all the help.

---

### Post by ventrical on 2011-12-19
I haven't adjusted any themes or settings and by default the windows borders will not expand from the left side- on this PC anyways.. Basically the best way is from the lower right corner.

edit..

Ok .. on this PC that is fixed with a reboot after update.

---

### Post by Claus7 on 2011-12-21
Hello,

> **effenberg0x0 said:**
> Well, I'm not sure who you're talking to since you quoted no one, but I'm the OP, so that probably is to me. Thank you for your tips. I've been trying very hard to learn how to use a computer for the last two weeks or so, and I think I'm getting there.
ehm...yes to you! Glad you are "almost" there!

> **jfernyhough said:**
> -snip-I've trawled through CCSM and can't find anything to configure the border thickness. I'm pretty sure this is theme property (e.g. the theme is "borderless"). Borderless themes became trendy in the last year or two (post-Clearlooks, I think).

System-> Preferences -> Emerald Theme Manager -> 
Themes Settings
Edit Themes
Frame/Shadows
Frame Borders (Size: top, bottom, left, right)

Regards!

---

