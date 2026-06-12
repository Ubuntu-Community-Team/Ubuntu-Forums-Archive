---
title: "Windows are opening (slightly) outside the workspace."
date: 2012-06-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by VinDSL on 2012-06-03
I had this problem before, but it's been so long ago, I cannot remember the cure.

Example:  When I open a browser, it opens underneath the Launcher (left side) and above the Panel (top), e.g. windows are opening slightly outside the workspace, off the display, in the direction of the upper-left corner.

I drag the window back down to where it should be, resize it, et cetera, but it doesn't save the position when I close it.

Anyone else having this problem and/or remember how to fix it?!?!?  Very irritating!

BTW, this cropped up after doing daily upgrades, two nights ago.  Subsequent upgrades have not provided a solution.

---

### Post by VinDSL on 2012-06-03
Now, it's starting to come back to me...

SOURCE (3-years ago):   [https://bugs.launchpad.net/hundredpapercuts/+bug/391533?comments=all]("https://bugs.launchpad.net/hundredpapercuts/+bug/391533?comments=all")

> When you close an application window, and then reopen it at a later time, it does not restore to the previous location. This is the expected behaviour for anybody who is used to using Windows. **It has been reported multiple times in the past, and is always marked WONTFIX because everybody claims it is somebody else's problem.[...]**


SOURCE (7 months ago):  [http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm)

> **_Open Up a Window in Center_**
When running an application without maximized, Ubuntu always puts it in the left-top corner of the desktop by default, but you are allowed to set a program window to open up in the center of the desktop area.

Go to System > Preferences > CompizConfig Settings Manager
Select "Windows Management" from the left panel.
Click "Place Windows".
Change Placement Mode from "Smart" to "Centered", click "Back" and "Close".

**Ideally, [COLOR="DarkRed"]the window manager[/COLOR] in Ubuntu should restore the last known position of an application window, but it does not do that unless [COLOR="DarkRed"]an application[/COLOR] remembers its own window position.** (See reported bugs)


They might be right:
[LIST]
[*]"It is somebody else's problem", not mine. LoL!
[*]"Centered" works fine in CCSM, but not "Smart".
[*]It only affects *certain* proggies (Banshee, for instance, remembers its location, but not Chromium).
[/LIST]

Strange that nobody else is experiencing it...

Guess I'll wait it out (again).  :)

---

### Post by effenberg0x0 on 2012-06-03
Hi Vin, a couple comments, maybe related:

- Would you say they are misplaced a small amount of px? I was gonna suggest something with borders (wouldn't be new for us) or even shadows. 
- Some apps, like vmware-player, tilda, randomly restore at the wrong locations for me. This is since PP beta. I believe it is related to multi-monitor setup. Some times they even get placed between 2 workspaces (in which case, clicking on an active app on the launcher does not switch to the desired workspace until I manually limit all windows to it's exact workspace area). 
- When compiz crashes/respawns, PlaceWindows plugin rules are not respected. All applications get restored at workspace 1,1, and at X coordinates 0,0. The Unity plugin loads and places the launcher/panel over the launcher and panel. This is since Natty and fully reproducible in my installs.

I have reported all of these in the past and also wasted a good amount of time last cycle trying to fix it with compiz workarounds, windows rules, etc - never succeeded.

My opinion: When we load the desktop, there's a race condition between X 0,0 coordinates and the new 0,0 coordinates after Unity plugin is loaded (the inner intersection of Unity Launcher and Panel). The same logic was behind problems we had in the past with windows borders, shadows and decoration. Also, coordinates 0,0 on a second monitor change if Unity is set to display the Launcher/Panel only on main monitor/all monitors. 

That's just a guess, I never took the time to debug it.

Regards,
Effenberg

---

### Post by VinDSL on 2012-06-03
Hi Effenberg,

> **effenberg0x0 said:**
> Hi Vin, a couple comments, maybe related:

- Would you say they are misplaced a small amount of px? I was gonna suggest something with borders (wouldn't be new for us) or even shadows.

[COLOR="Navy"]**A: It's a considerable amount... probably 20-30 px.  It's enough that the window buttons are out of view.**[/COLOR]
 
- Some apps, like vmware-player, tilda, randomly restore at the wrong locations for me. This is since PP beta. I believe it is related to multi-monitor setup. Some times they even get placed between 2 workspaces (in which case, clicking on an active app on the launcher does not switch to the desired workspace until I manually limit all windows to it's exact workspace area).

[COLOR="Navy"][B]A: I'm logged into GS right now (haven't used it in ages - still works fine).  All the proggies that were giving me fits, in Unity, are working fine in GS.

Before I logged out of Unity, and logged into GS, I had Chromium running on workspace-1.  When I switched workspaces (2-9) and moused-over the panel, the Chromium menu(s) were at the top of every panel, not just workspace-1.  LoL!

Weird![/B][/COLOR]
 
- When compiz crashes/respawns, PlaceWindows plugin rules are not respected. All applications get restored at workspace 1,1, and at X coordinates 0,0. The Unity plugin loads and places the launcher/panel over the launcher and panel. This is since Natty and fully reproducible in my installs.

I have reported all of these in the past and also wasted a good amount of time last cycle trying to fix it with compiz workarounds, windows rules, etc - never succeeded.

[COLOR="DarkSlateBlue"][B]A: Resistance is futile!  I can see that, from reading through Launchpad this afternoon.  

I'm not even going to bother adding a "Me Too".  Heh![/B][/COLOR]

My opinion: When we load the desktop, there's a race condition between X 0,0 coordinates and the new 0,0 coordinates after Unity plugin is loaded (the inner intersection of Unity Launcher and Panel). The same logic was behind problems we had in the past with windows borders, shadows and decoration. Also, coordinates 0,0 on a second monitor change if Unity is set to display the Launcher/Panel only on main monitor/all monitors. 

That's just a guess, I never took the time to debug it.

[COLOR="Navy"][B]A: Thanks! for the feedback!  I'm not going to waste much time on it.  Nobody else is...

I'll install LXDE DE / OpenBox WM if it starts getting to me. Haha! :D[/B][/COLOR]

Regards,
Effenberg

**EDIT**

Okay, I'm back in Unity again (after a cold boot).

I opened Chromium in workspace-1.  All other workplaces contained the Chromium Global Menu on mouse-over.

Then, I opened Banshee in workspace-2.  All workspaces now contained the Banshee Global Menu, except for workspace-1... the Chromium workspace.

If I go to workspace-1 (Chromium), all other workspaces, except workspace-2 (Banshee) have the Chromium Global Menu.

If I go to workspace-2 (Banshee), all other workspaces, except workspace-1 (Chromium) have the Banshee Global Menu.

Something is definitely amiss...  :)

---

### Post by effenberg0x0 on 2012-06-03
> **VinDSL said:**
> Hi Effenberg,

**EDIT**

Okay, I'm back in Unity again (after a cold boot).

I opened Chromium in workspace-1.  All other workplaces contained the Chromium Global Menu on mouse-over.

Then, I opened Banshee in workspace-2.  All workspaces now contained the Banshee Global Menu, except for workspace-1... the Chromium workspace.

If I go to workspace-1 (Chromium), all other workspaces, except workspace-2 (Banshee) have the Chromium Global Menu.

If I go to workspace-2 (Banshee), all other workspaces, except workspace-1 (Chromium) have the Banshee Global Menu.

Something is definitely amiss...  :)

Yep, that happens sporadically with Chromium. I have also seen that also with X-Chat a couple times. 
I'm not skilled at all with GS (never used it much) but I'm seriously considering using it as my default on LTS stable machines and moving Unity to test VMs this cycle. I get a little lost with GS, there are lots of customizations, extensions, etc. There's a learning curve for me.

Regards,
Effenberg

---

### Post by VinDSL on 2012-06-03
> **effenberg0x0 said:**
> I'm not skilled at all with GS (never used it much) but I'm seriously considering using it as my default on LTS stable machines and moving Unity to test VMs this cycle.[...]
Only thing I use GS for is customizing Unity.  LoL!

Got my fallback in place - just need to do some more tweaking...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-jun-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-jun-2012-2.png")[/INDENT]


Spent a few minutes installing it.  Now I need to work on the theme and icon set.

Surprisingly, GiMP 2.8.0 and Nautilus work in LXDE.  Never tried that before.  Didn't know what I was missing...  :)

---

### Post by VinDSL on 2012-06-04
You know...

A lot of this "testing stuff" is cosmic and serendipitous and, in the end, leaves one scratching his head.

Instead of wasting a lot of time trying to patch a longstanding design flaw, I spent the remainder of the day n' night tweaking LXDE/Openbox on Ubu 12.10/Linux 3.5rc1.  

I'm smitten with LXDE, as of late, and could eat it with a spoon -- I love it so much.  One of these days, I'll have my fill and dispatch it with a belch, but for now LXDE/Openbox is fun and exciting, especially on a modern OS/Kernel.

Before shutting down my machine, last night, I thought I should log into Unity one last time; but I didn't.  I knew I'd forget I was running LXDE, before my first pot of coffee.  And, sure enough, this morning I forgot and booted into an LXDE session, instead of Unity 3D.

I logged out of LXDE and into Unity.  Guess what!?!?!?!  

Everything is working fine!  All windows are following the "Smart" Placement algos, resizing is sticking, and life is beautiful.

This most assuredly was an unexplainable 2-day anomaly, but I'd like to *fantasize* that Unity was jealous of LDXE.  They had a lover's quarrel during the night and fought for my affection, while I slumbered away upon my bed of roses. After all, it's a charmed life we testers lead.  LoL!

As good an explanation as any, yes?  :D

Marking this as [SOLVED]...

---

### Post by effenberg0x0 on 2012-06-04
> **VinDSL said:**
> You know...

A lot of this "testing stuff" is cosmic and serendipitous and, in the end, leaves one scratching his head.

Instead of wasting a lot of time trying to patch a longstanding design flaw, I spent the remainder of the day n' night tweaking LXDE/Openbox on Ubu 12.10/Linux 3.5rc1.  

I'm smitten with LXDE, as of late, and could eat it with a spoon -- I love it so much.  One of these days, I'll have my fill and dispatch it with a belch, but for now LXDE/Openbox is fun and exciting, especially on a modern OS/Kernel.

Before shutting down my machine, last night, I thought I should log into Unity one last time; but I didn't.  I knew I'd forget I was running LXDE, before my first pot of coffee.  And, sure enough, this morning I forgot and booted into an LXDE session, instead of Unity 3D.

I logged out of LXDE and into Unity.  Guess what!?!?!?!  

Everything is working fine!  All windows are following the "Smart" Placement algos, resizing is sticking, and life is beautiful.

This most assuredly was an unexplainable 2-day anomaly, but I'd like to *fantasize* that Unity was jealous of LDXE.  They had a lover's quarrel during the night and fought for my affection, while I slumbered away upon my bed of roses. After all, it's a charmed life we testers lead.  LoL!

As good an explanation as any, yes?  :D

Marking this as [SOLVED]...

Lol :) Well, Unity is strongly emotional, almost bipolar sometimes. I haven't looked at LP, but they probably merged a lot of things for the alpha release.

Regards,
Effenberg

---

