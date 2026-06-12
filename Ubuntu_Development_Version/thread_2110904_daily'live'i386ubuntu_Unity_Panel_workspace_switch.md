---
title: "daily'live'i386/ubuntu Unity Panel workspace switcher gone"
date: 2013-01-31
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-01-31
Workspace switcher in unity panel is gone.

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

---

### Post by danniel on 2013-01-31
Did you enable the multiple workspaces from the settings panel?

---

### Post by jbicha on 2013-01-31
The workspace switcher is [disabled]("http://pad.lv/868423") by default in Ubuntu 13.04.

Go to System Settings>Appearance>Behavior to re-enable it.
(If you don't have an Appearance panel, make sure you have gnome-control-center-unity installed).

---

### Post by mc4man on 2013-01-31
The current state is - 
By default workspaces is disabled so a 1x1 layout, no icon in launcher
If you enable Workspaces you'll get a 2x2 layout & launcher icon(s), which  depends on current Ws

If Workspaces is enabled & you use any layout other than 2x2 each time you open the Appearances panel you'll be auto switched back to 2x2 

Only the 2x2 layout will get the changing Ws icon, any other layout will just use the left-top icon (unless modified in source for a specific non 2x2 layout

---

### Post by ventrical on 2013-01-31
> **jbicha said:**
> The workspace switcher is [disabled]("http://pad.lv/868423") by default in Ubuntu 13.04.

Go to System Settings>Appearance>Behavior to re-enable it.
(If you don't have an Appearance panel, make sure you have gnome-control-center-unity installed).

Ok .. thanks .. works great. I am not sure why they removed that as default setting for 'live" as I used it as a sort of tool to get a live visual that my graphics were working.

The iso is working a lot better on intel graphics .. no more flickering and sporadic  flashing during bootup of live.

---

### Post by ventrical on 2013-01-31
> **mc4man said:**
> The current state is - 
By default workspaces is disabled so a 1x1 layout, no icon in launcher
If you enable Workspaces you'll get a 2x2 layout & launcher icon(s), which  depends on current Ws

If Workspaces is enabled & you use any layout other than 2x2 each time you open the Appearances panel you'll be auto switched back to 2x2 

Only the 2x2 layout will get the changing Ws icon, any other layout will just use the left-top icon (unless modified in source for a specific non 2x2 layout


 Yes .. thanks mac4man. You had mentioned this in another thread and I just forgot.

Long day ...:)

---

### Post by epikvision on 2013-02-08
Thank you for this thread!  I thought the workspace switcher was suddenly removed.

---

### Post by Simeo on 2013-02-17
> **epikvision said:**
> Thank you for this thread!  I thought the workspace switcher was suddenly removed.

+1 This was a complete fail for me. I almost switched back to 12.10 because of it.

---

### Post by ventrical on 2013-02-18
This is one of those things which cadence testing cannot provide statistics for. During the development of the Unity Interface I had learned to use the <workspace switcher> to edge test my graphics  adaptors (to see if the graphics drivers were working). Having the workspace switcher at hand it saved a lot of down time. I could usually tell if  an install was borked (or big changes were made) by the fail of the <workspace switcher>.

  Now it's gone and there is a little more fandangling that we have to do. Why?  I have no idea. I mean they could have removed that at final release but why make it more difficult for beta testers when they are trying to move along throughout the testing process?  Creating more down-time just totally impedes the whole testing process.

 At least thats my take on the whole matter .. and again .. this too came without warning. If I were a unity developer it probably would not matter to me. But unity developers have to start looking at these changes from the perspective view of beta testers and not Turing machines.

---

### Post by jinjorge on 2013-02-18
> **mc4man said:**
> The current state is - 

If Workspaces is enabled & you use any layout other than 2x2 each time you open the Appearances panel you'll be auto switched back to 2x2 



Why is this the case? I find it particularly annoying that each time Settings is launched the workspaces switches back to 2x2.  Is there any way to work around this issue?

---

### Post by ventrical on 2013-02-18
> **jinjorge said:**
> Why is this the case? I find it particularly annoying that each time Settings is launched the workspaces switches back to 2x2.  Is there any way to work around this issue?

  I am not totally sure about Unity Desktop but the last I was experimenting with cario-dock and ccsm it will display all workspaces. I am about to try this on raring now.

---

### Post by ventrical on 2013-02-18
cairo-dock succesfully dispays all workspaces while also allowing Unity Desktop to operate, however, then, the unity workspaceswitcher becomes a moot point so  one could just disable it. 

 I am not sure why the dev have not employed a patch or have solved this error as it is working very well with Kubuntu and cairo-dock.

  I am only assuming that the unity devs are stripping off features from unity/compiz so as to set up with new wayland/weston depends.

---

### Post by ventrical on 2013-02-18
Actually there is a major bug when staring cairo-dock with Unity Desktop also on. The work-space switcher will restore back to  2x2 spaces and if you disable it in appearances/behaviour it will also disable it in cairo-dock. However, if you log on to cairo-dock from lightdm greeter the number of worspaces will not be affected and I also assume that if you would enable ccsm and the Unity Plugin that that too may also fail. In Precise it worked just excellently.

@mac4man

Did you already file a bug on this concerning the workspace switcher? (I think you did).

---

### Post by cariboo on 2013-02-18
I haven't tried it personally, but you should be able to over-ride the default settings with ccsm. You can find the setting under General Options.

---

### Post by mc4man on 2013-02-19
> **jinjorge said:**
> Why is this the case? I find it particularly annoying that each time Settings is launched the workspaces switches back to 2x2.  Is there any way to work around this issue?

This was fixed in  - 
> gnome-control-center-unity (1.2daily13.02.15-0ubuntu1) raring; urgency=low

  [ Didier Roche ]
  * Opening 'Settings › Appareance' involves losing workspace size


---

### Post by jinjorge on 2013-02-19
> **mc4man said:**
> This was fixed in  -
havent opened settings since I run into the issue. I'll try it and report back.

Thanks for the follow up.

---

### Post by jinjorge on 2013-02-19
> **jinjorge said:**
> havent opened settings since I run into the issue. I'll try it and report back.

Thanks for the follow up.

confirming that this is fixed in the latest Raring daily.

@mc4man - Thanks for sharing the info.

---

### Post by meborc on 2013-02-21
Am I the only one who has trouble switching between workspaces? I have enabled them in the appearance settings and can switch by clicking the icon in the launcher, but ctrl+alt+right/left/up/down do not work any more. I did set them in the keyboard shortcut menu. Any ideas?

---

### Post by jinjorge on 2013-02-21
> **meborc said:**
> Am I the only one who has trouble switching between workspaces? I have enabled them in the appearance settings and can switch by clicking the icon in the launcher, but ctrl+alt+right/left/up/down do not work any more. I did set them in the keyboard shortcut menu. Any ideas?

Just tried it and it worked for me. I have a 2x3 workspace config and was able to go left, right, up and down.

---

### Post by meborc on 2013-02-21
> **jinjorge said:**
> Just tried it and it worked for me. I have a 2x3 workspace config and was able to go left, right, up and down.

you set it up using ccsm?

---

### Post by ventrical on 2013-02-21
I did on mine. Works great with ccsm.. but Unity Workspace Switcher still only shows 4 spaces on the panel. Definitely not in synchronicity.

---

### Post by mc4man on 2013-02-21
> **ventrical said:**
> I did on mine. Works great with ccsm.. but Unity Workspace Switcher still only shows 4 spaces on the panel. Definitely not in synchronicity.
And for the moment (or ever), that's all it's going to show.

The launcher WS switcher is just an icon, there are 4 icons available if using 2x2, anything else will just use 1 icon - "workspace-switcher-top-left"

To use the other icons in a layout other than 2x2 would require editing the unity source & figuring out how to 'map' to your layout.

As I only use 1x4 I've changed like this to produce 
12
34

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
@@ -77,12 +77,12 @@
 
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

I guess if one was using some other layout & wanted to spend the time to figure out they could do so.
Could be possible to have more than 4 available icons & if you could create add. or new icons & map then it could work out.

(easier to just use indicator-workspaces

---

### Post by ventrical on 2013-02-22
> **mc4man said:**
> And for the moment (or ever), that's all it's going to show.

The launcher WS switcher is just an icon, there are 4 icons available if using 2x2, anything else will just use 1 icon - "workspace-switcher-top-left"

To use the other icons in a layout other than 2x2 would require editing the unity source & figuring out how to 'map' to your layout.

As I only use 1x4 I've changed like this to produce 
12
34

```
--- launcher/ExpoLauncherIcon.cpp    2013-01-11 08:04:35.000000000 -0500
+++ launcher/ExpoLauncherIcon.cpp    2013-01-14 02:25:28.582100478 -0500
@@ -46,7 +46,7 @@
 
 void ExpoLauncherIcon::OnViewportLayoutChanged(int hsize, int vsize)
 {
-  if (hsize != 2 || vsize != 2)
+  if (hsize != 4 || vsize != 1)
   {
     icon_name = "workspace-switcher-top-left";
     screen_viewport_switch_ended_connection_.disconnect();
@@ -77,12 +77,12 @@
 
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
```I guess if one was using some other layout & wanted to spend the time to figure out they could do so.
Could be possible to have more than 4 available icons & if you could create add. or new icons & map then it could work out.

(easier to just use indicator-workspaces

Thanks for your input mac4man. 

What compiler do you use to enter that code or do you just enter that in terminal? or is that some  script that is run by another highlevel compiler?

---

### Post by jinjorge on 2013-02-22
> **meborc said:**
> you set it up using ccsm?

Set is up using [Ubuntu Tweak]("http://ubuntu-tweak.com/")

If you are running Unity, looks like you can also use [Unity Tweak tool]("https://launchpad.net/unity-tweak-tool")

---

### Post by mc4man on 2013-02-22
> **ventrical said:**
> Thanks for your input mac4man. 

What compiler do you use to enter that code or do you just enter that in terminal? or is that some  script that is run by another highlevel compiler?
Nothing out of ordinary - 
sudo apt-get build-deps unity
make a build folder, cd to it, apt-get source unity
cd to the source, patch, build the unity packages & install

---

