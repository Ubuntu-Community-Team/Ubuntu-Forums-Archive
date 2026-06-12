---
title: "Bug Check: Compiz &quot;Place Windows&quot; Plugin"
date: 2011-11-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-09
I need help confirming one bug:

**Behavior:** Place Windows rules are not respected after "unity --replace&"

**To Reproduce:** 

[LIST]
[*]Go to ccsm/PlaceWindows/Fixed Window Placement
[*]Go to Windows with Fixed Viewport / New
[*]Add a couple rule for programs you use to place their windows AWAY FROM viewport X=1,Y=1. (e.g. class=Gnome-terminal on x=1, y=2 class=Thunderbird on x=2 y=2)
[*]At a gnome-terminal, run unity --replace&
[/LIST]
**Results:** All windows will be thrown at Viewport 1/1. Also, their Top-Left corners will be under Unity Launcher and Panel, demanding that you use left-shift and mouse to move them. New instances are placed correctly (the plugin is active and working, only fails after a reload). System is stable nonetheless.

**Expected Results:** Default / expected plugin behavior. Windows should be auto-placed at pre-defined viewports, even after a reload of Unity/Compiz. 
 
 
Thanks,
Effenberg

---

### Post by ventrical on 2011-11-09
Not sure if this is what you are looking for .You have to be patient with these videos because of the ...long... reset of compiz!!



[http://www.youtube.com/watch?v=_FBeJzajOY4](http://www.youtube.com/watch?v=_FBeJzajOY4)


[http://www.youtube.com/watch?v=oA5jk-3vEmo](http://www.youtube.com/watch?v=oA5jk-3vEmo)

---

### Post by effenberg0x0 on 2011-11-09
@ventrical Hey, you do have a lot of patience to make videos and stuff! Thanks man.

I think your first video confirmed it. You added Class=Gnome-Terminal to PlaceWindows  ccsm plugin, made a rule to pin it to Viewport 1/2. As you reloaded Unity, it reappeared at Viewport 1/1, in disregard of the existing/set rule.

It's weird because, at boot, PlaceWindows rules are respected. It works perfectly during a normal session too - windows are launched to correct Viewports. It's rules are only disregarded if you reload Unity. But, as you could see in the terminal window, it outputs no error/warn/relevant bug message about it.

I think it's worth a bug report.

---

### Post by ventrical on 2011-11-09
> **effenberg0x0 said:**
> @ventrical Hey, you do have a lot of patience to make videos and stuff! Thanks man.

I think your first video confirmed it. You added Class=Gnome-Terminal to PlaceWindows  ccsm plugin, made a rule to pin it to Viewport 1/2. As you reloaded Unity, it reappeared at Viewport 1/1, in disregard of the existing/set rule.

It's weird because, at boot, PlaceWindows rules are respected. It works perfectly during a normal session too - windows are launched to correct Viewports. It's rules are only disregarded if you reload Unity. But, as you could see in the terminal window, it outputs no error/warn/relevant bug message about it.

I think it's worth a bug report.

  It only appeared after I cliked on it in desktop 5. Remember I have  96 desktops running Cairo also. So, 1(x)2  rows&colums would be 5.

The last screenshot  shows after I use 1(x)2 that the desktop is #5 where the GNOME Terminal is so I do not think I emulated your bug correctly.

---

### Post by effenberg0x0 on 2011-11-10
> **ventrical said:**
> ...
Remember I have  96 desktops running Cairo also.
---


I was wondering about it! Is this your default setup? Or you created that just for this test?

---

### Post by effenberg0x0 on 2011-11-10
To make things clearer for people that want to test it. See the screenshot.
[ATTACH]206834[/ATTACH]

My PlaceWindows rules leave nothing at Viewport 1,1. All apps should always open in other Viewports. Immediately after running **unity --replace&**, all of these apps, if previously opened, are auto moved to Viewport 1,1, in disregard of these rules.

---

### Post by ventrical on 2011-11-10
> **effenberg0x0 said:**
> To make things clearer for people that want to test it. See the screenshot.
[ATTACH]206834[/ATTACH]

My PlaceWindows rules leave nothing at Viewport 1,1. All apps should always open in other Viewports. Immediately after running **unity --replace&**, all of these apps, if previously opened, are auto moved to Viewport 1,1, in disregard of these rules.


 Ok .. I'll try this later today.  I didn't understand your first message.

Thanks.

---

### Post by ventrical on 2011-11-10
> **effenberg0x0 said:**
> I was wondering about it! Is this your default setup? Or you created that just for this test?

 Default.  I'm playing around  with compiz/unity & General Options.  The maximum # of desktops allowed is 1260 (set in ccsm). I'm trying to build a 3D cascading/shuffling  style fashcard system where  compiz will serial grab off the HDD .png, jpg and other pics, place them as a window or background on each window and then be able to shuffle through them like a virtual roll-o-dex.

 It would be a great memory -peg /educational tool.  I know that a lot of features currently can emulate such a feature , but only to a small degree.

---

### Post by ventrical on 2011-11-10
> **effenberg0x0 said:**
> I need help confirming one bug:

**Behavior:** Place Windows rules are not respected after "unity --replace&"

**To Reproduce:** 

[LIST]
[*]Go to ccsm/PlaceWindows/Fixed Window Placement
[*]Go to Windows with Fixed Viewport / New
[*]Add a couple rule for programs you use to place their windows AWAY FROM viewport X=1,Y=1. (e.g. class=Gnome-terminal on x=1, y=2 class=Thunderbird on x=2 y=2)
[*]At a gnome-terminal, run unity --replace&
[/LIST]
**Results:** All windows will be thrown at Viewport 1/1. Also, their Top-Left corners will be under Unity Launcher and Panel, demanding that you use left-shift and mouse to move them. New instances are placed correctly (the plugin is active and working, only fails after a reload). System is stable nonetheless.

**Expected Results:** Default / expected plugin behavior. Windows should be auto-placed at pre-defined viewports, even after a reload of Unity/Compiz. 
 
 
Thanks,
Effenberg

Yes.. I can confirm this bug. However, after log-out , log -on the windows are properly placed.

---

### Post by edgue on 2011-11-30
Just wondering: I just installed 11.10; and I found "place windows" to be pretty helpful ... but with "place windows" enabled, "super" wont work as expected any more:

having a workspace with a maximized window, i can see that pressing super will do something (menu bar is changing color from gray to dash-black) ...
but the actual "dash window" stays hidden (or maybe it stays below my
maximized window).

Any idea anybody?

---

### Post by effenberg0x0 on 2011-11-30
There's no change to this from OO to current PP, so this is not a question about U+1.

Yet, notice how inside Compiz Config Settings Manager (ccsm) you can set "Bindings" for each plugin to different keys. In my case, for example, I have set "super" to the expo plugin, Super + F12 to static switcher, etc. There's no default or better way. You have to check the bindings for each plugin, and that includes the Ubuntu Unity Plugin, to make sure things are the way you want and don't conflict with each other.

---

### Post by cariboo on 2011-11-30
> **edgue said:**
> Just wondering: I just installed 11.10; and I found "place windows" to be pretty helpful ... but with "place windows" enabled, "super" wont work as expected any more:

having a workspace with a maximized window, i can see that pressing super will do something (menu bar is changing color from gray to dash-black) ...
but the actual "dash window" stays hidden (or maybe it stays below my
maximized window).

Any idea anybody?

This is the Precise Pangolin (12.04) Testing & Discussion sub-forum unless your question concerns Precise, you will be better off asking your question in [Desktop Environments]("http://ubuntuforums.org/forumdisplay.php?f=329")

---

### Post by amias on 2012-01-25
i'm using 11.10 and i've found that the place windows options are totally ignored. I defined my window (Ssvnc) by using all of the Match types and the grab button but none work for me , the window just appears on the currently selected desktop. This is regardless of whether i compiz --restart or not.

my xsession errors contains these errors :

WARN  2012-01-25 13:58:05 glib <unknown>:0 Attempted to register a quicklist that was previously registered
WARN  2012-01-25 13:58:15 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

any suggestions or workarounds welcome.

---

### Post by effenberg0x0 on 2012-01-26
> **amias said:**
> i'm using 11.10 and i've found that the place windows options are totally ignored. I defined my window (Ssvnc) by using all of the Match types and the grab button but none work for me , the window just appears on the currently selected desktop. This is regardless of whether i compiz --restart or not.

my xsession errors contains these errors :

WARN  2012-01-25 13:58:05 glib <unknown>:0 Attempted to register a quicklist that was previously registered
WARN  2012-01-25 13:58:15 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

any suggestions or workarounds welcome.

I can't say the plugin is ignored in my case: Windows are started in the correct viewport for me when a Unity session starts. My problem is when the Unity/Compiz session is restarted (via unity --replace / compiz --replace). In this specific case, all open windows are moved to viewport 1,1 at coordinates 0,0 (so their top-left corners are partially covered by the launcher and the global panel). However, new instances of programs are opened at the correct viewport.

Regards,
Effenberg

---

