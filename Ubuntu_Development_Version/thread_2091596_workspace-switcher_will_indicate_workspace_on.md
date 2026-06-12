---
title: "workspace-switcher will indicate workspace on"
date: 2012-12-05
forum: Ubuntu Development Version
---

### Post by mc4man on 2012-12-05
The Ws will shortly show which Ws one is on But this will only work on the default 2X2 setting
Any other settings continue to use static icon, at least for now.
screen shows bottom right (ws 4

(myself use 1X4 & for the most part hide the launcher & use plank as ATM it's better featured than Unity launcher

---

### Post by ventrical on 2012-12-05
Very interesting.  I assume also that this is the first of the icon changes to come?

Note* You can also see the window switch in the actual icon.. nice effect.

---

### Post by fjgaude on 2012-12-05
Wow, the Workplace Switcher is about all the cool I can take for one day.

---

### Post by ventrical on 2012-12-05
hahahahaheaheha!

---

### Post by VinDSL on 2012-12-06
> **mc4man said:**
> The Ws will shortly show which Ws one is on But this will only work on the default 2X2 setting

(myself use 1X4 & for the most part hide the launcher & use plank as ATM it's better featured than Unity launcher

> **fjgaude said:**
> Wow, the Workplace Switcher is about all the cool I can take for one day.
Bwahahahaha!  Brilliant move!

I use 3x3 LoL!  :D

And, yes, I *need* them.  

I'm working 4 Ws, right now, and the icon is showing 1...

---

### Post by mc4man on 2012-12-06
> **VinDSL said:**
> Bwahahahaha!  Brilliant move!

I use 3x3 LoL!  :D

And, yes, I *need* them.  

I'm working 4 Ws, right now, and the icon is showing 1...
Things are done based on the default, after that chips fall where they may..
The Ws icon whatever is based on position (top left, ect.) rather than # & the icon only has 4 area's anyway.
(the not updated for a while 'indicator-workspace' (from a ppa) still works ok, needs a little help auto starting & not sure how it likes 3X3 though could be ok with wall.

Here I've now gone with plank instead until the unity launcher grows up, if ever.
(other than a built-in neutered spread it has all the UL has plus a fair bit more

---

### Post by VinDSL on 2012-12-07
Here's one for you...

Just got home from work -- gotta get up and go back in 3 hours.

Reading your posts (above), I wondered if the 4 corners of my 3x3 setup would display in the icon.  Soooo, I started going through the Ws in order, one-by-one, using the switcher.  I got to W-5 and Unity hard-locked.  LoL!

Fortunately, I could still shell-out to console and reboot.  Otherwise, I would have had to hit the power button, and risk the consequences -- haven't got time to fiddle around with Canonical nonsense, right now.

Yes, indeed... brilliant move!  :D

---

### Post by mc4man on 2012-12-07
> **VinDSL said:**
>  I wondered if the 4 corners of my 3x3 setup would display in the icon.  Soooo, I started going through the Ws in order, one-by-one, using the switcher.  I got to W-5 and Unity hard-locked.  LoL!

It's coded only to work with 2x2, little snippet


 if (hsize != 2 || vsize != 2)
  {
    icon_name = "workspace-switcher-top-left";
    screen_viewport_switch_ended_connection_.disconnect();
    terminate_expo_connection_.disconnect();
  }
  else
  {
    UpdateIcon();
ect.

From source test

TEST_F(TestExpoLauncherIcon, Icon2x2Layout)
{
  EXPECT_EQ(icon.icon_name, "workspace-switcher-top-left");
 
  wm->SetCurrentViewport(nux::Point(1, 0));
  wm->screen_viewport_switch_ended.emit();
  EXPECT_EQ(icon.icon_name, "workspace-switcher-right-top");

  wm->SetCurrentViewport(nux::Point(0, 1));
  wm->screen_viewport_switch_ended.emit();
  EXPECT_EQ(icon.icon_name, "workspace-switcher-left-bottom");
ect.ect.

(finally did a fresh install of raring, 1st overall - must be a bug but noticed if I shutdown/restart with vlc open the reboot/login has vlc open
(thought maybe some sort of session restore but so far only vlc...

---

### Post by zika on 2012-12-07
> **VinDSL said:**
> Here's one for you...

Just got home from work -- gotta get up and go back in 3 hours.

Reading your posts (above), I wondered if the 4 corners of my 3x3 setup would display in the icon.  Soooo, I started going through the Ws in order, one-by-one, using the switcher.  I got to W-5 and Unity hard-locked.  LoL!

Fortunately, I could still shell-out to console and **reboot**.  Otherwise, I would have had to hit the power button, and risk the consequences -- haven't got time to fiddle around with Canonical nonsense, right now.

Yes, indeed... brilliant move!  :DWasn't restart od LightDM enough?

---

### Post by VinDSL on 2012-12-07
> **zika said:**
> Wasn't restart od LightDM enough?
Yeah, probably, but I'm running on fumes, you know?

I just gave it the 3-finger salute, from console.

That way, I can catch a few seconds sleep, while it's rebooting.  LoL!  :D

---

### Post by cecilpierce on 2012-12-07
The side bar shows 2X2 but I have 1X4 setup, neat!

---

### Post by VinDSL on 2012-12-07
Putting a positive spin on things (using 3x3)...

It seems that I can go from any W, to any W, by clicking the open app icons, in the launcher panel, now.

Before, the (open) launcher icons would only go to open apps in adjoining Ws.

For instance, if I wanted to go from an app in W-1 to W-9, I had to use the switcher.  Clicking open apps, on the launcher, wouldn't take me from one W to another, if they didn't reside next to one another, in the switcher screen.

Does that make any sense? Don't have time for screenies, right now  :)

I'll have to check it out, more thoroughly, when I get home later.

---

### Post by fjgaude on 2012-12-07
> **VinDSL said:**
> Putting a positive spin on things (using 3x3)...

It seems that I can go from any W, to any W, by clicking the open app icons, in the launcher panel, now.

Before, the (open) launcher icons would only go to open apps in adjoining Ws.

For instance, if I wanted to go from an app in W-1 to W-9, I had to use the switcher.  Clicking open apps, on the launcher, wouldn't take me from one W to another, if they didn't reside next to one another, in the switcher screen.

Does that make any sense? Don't have time for screenies, right now  :)

I'll have to check it out, more thoroughly, when I get home later.

I think I understand. Only using 2x2 from the beginning, Ubuntu 11.10 worked by clicking the open app's icon on the launcher, going to the work space where it is. That's improved by workflow for my graphic design. I was then hooked onto Unity from then on. Attachment shows my normal work situation. <smile>

---

### Post by ventrical on 2012-12-08
Actually I think that is a compiz effect provided to the Unity Plugins (or to this effect).

---

### Post by mc4man on 2012-12-09
As far as with 1x4 - 
The source can be altered to work with, probably just in the 2  blocks of code below. (ExpoLauncherIcon.cpp, lines 49.. & 73.... 
Ws1, (top-left)  is already given & as it currently is  bottom-right is a freebie - anything wrong (not defined correctly) gets it.
```

void ExpoLauncherIcon::OnViewportLayoutChanged(int hsize, int vsize)
{
  if (hsize != 2 || vsize != 2)
```
```
if (vp.x == 0 and vp.y == 0)
    icon_name = "workspace-switcher-top-left";
  else if (vp.x == 0)
    icon_name = "workspace-switcher-left-bottom";
  else if (vp.y == 0)
    icon_name = "workspace-switcher-right-top";
  else
    icon_name = "workspace-switcher-right-bottom";
```
If you know or can figure how 'vp.x' & 'vp.x' relate to 4 linear Ws's then seems easy to alter to pattern desired

12
34
or 
12
43
or whatever
Not knowing what vp.x or vp.y mean was able in a couple of tries to get, attached quick vid
13
42

---

### Post by mc4man on 2013-01-16
fairly simple way to get a 
12
34
on a 1X4 layout

```
--- launcher/ExpoLauncherIcon.cpp	2013-01-11 08:04:35.000000000 -0500
+++ launcher/ExpoLauncherIcon.cpp	2013-01-14 02:25:28.582100478 -0500
@@ -46,7 +46,7 @@
 
 void ExpoLauncherIcon::OnViewportLayoutChanged(int hsize, int vsize)
 {
-  if (hsize != 2 || vsize != 2)
+  if (hsize != 4 || vsize != 1)
   {
     icon_name = "workspace-switcher-top-left";
     screen_viewport_switch_ended_connection_.disconnect();
@@ -72,12 +72,12 @@
 
   if (vp.x == 0 and vp.y == 0)
     icon_name = "workspace-switcher-top-left";
-  else if (vp.x == 0)
+  else if (vp.x == 3 and vp.y == 0)
+    icon_name = "workspace-switcher-right-bottom";
+  else if (vp.x == 2 and vp.y == 0)
     icon_name = "workspace-switcher-left-bottom";
-  else if (vp.y == 0)
+  else if (vp.x == 1 and vp.y == 0)
     icon_name = "workspace-switcher-right-top";
-  else
-    icon_name = "workspace-switcher-right-bottom";
 }
 
 void ExpoLauncherIcon::ActivateLauncherIcon(ActionArg arg)
```

---

### Post by frank75riz on 2013-04-06
I just updated to 13, and can't find a workplace switcher.   I guess they decided to layer each app as you use it?????

---

### Post by mc4man on 2013-04-06
> **frank75riz said:**
> I just updated to 13, and can't find a workplace switcher.   I guess they decided to layer each app as you use it?????
The default is now only 1 Ws, so you need to enable Ws's.
System Settings > Appearances > Behavior, you'll see.

---

