---
title: "HOW-TO: Build Unity with 'Dodge Windows' and minimize/unminimize behavior"
date: 2012-04-28
forum: Tutorials
---

### Post by isaacj87 on 2012-04-28
The information in this thread has been moved to [https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior](https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior)

A thread for discussion of the wiki page only can be found here 
[http://ubuntuforums.org/showthread.php?t=2012412](http://ubuntuforums.org/showthread.php?t=2012412)

Thread closed.


So, I've been running 12.04 since around Beta 1, and one thing that really bothered me was the missing 'Dodge Windows' behavior. I had gotten so particular and used to the behavior that it completely disrupted my workflow when I migrated over to 12.04.

There has been a valiant effort to recreate this behavior: [http://ubuntuforums.org/showthread.php?t=1936037]("http://ubuntuforums.org/showthread.php?t=1936037"). For the most part, the script works pretty well, but I wanted the "real" option back. In this [bug report #930148]("https://bugs.launchpad.net/unity/+bug/930148"), one user, damianatorrpm (around comment #141), has created a couple patches that will revert the Canonical changes and re-add the behavior back to the source. I applied the patch to latest release of Unity (at this time, it's 5.12.0) and it works! Not only the behavior work as expected, the option is back in CCSM and has no nasty side-effects.

Another feature I really like is the ability to be able to click a program's icon on the Launcher and minimize/unminimize that window. Jonathan French (ojno), the developer behind this patch, has not only made this a reality, but also got this to work in conjunction with the 'Spread Windows' functionality. He's even set up a PPA which contains the latest Unity and his patch to make it easier for end-users to get it.

To make things easier, I've gone ahead and patched the vanilla Unity source to incorporate both of these behaviors. Furthermore, I've uploaded the changes to my Github. You can see this here: [https://github.com/isaacj87/unity]("https://github.com/isaacj87/unity")

The relevant commits are here:

[LIST]
[*][https://github.com/isaacj87/unity/commit/47322969522c093386616ba5b93ed4d56620a84a]("https://github.com/isaacj87/unity/commit/47322969522c093386616ba5b93ed4d56620a84a")
[*][https://github.com/isaacj87/unity/commit/cc6bad164588d38fb57aa0cb8178772fd57b7830]("https://github.com/isaacj87/unity/commit/cc6bad164588d38fb57aa0cb8178772fd57b7830")
[/LIST]

So, without futher ado, let's get started. Open up a Terminal window and follow the steps below.

**UPDATED: New PPA installation method!** Choose one method or the other, but **NOT** both.

[SIZE="3"]**PPA Method (Recommended)**:[/SIZE]

Alright, guys...

Now, I realize that for novice users (or even those who abhor the terminal), building Unity just for a couple features seems kind of silly. So, I decided to sit down last night and try to figure out packaging and PPAs...

So, if you were hesitant about trying this before, you can now add my PPA if you feel more comfortable doing that.

**NOTE**: Since I'm running 32-bit, I've only tested the i386 packages. I'll need someone running 64-bit to let me know if it works okay.

**NOTE**: If you followed the tutorial originally, please remove ~/.compiz-1 and the 'staging' folder before you do this.

Add my PPA by doing this:

```
sudo apt-add-repository ppa:ikarosdev/unity-revamped
```

...then, simply run an update:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

...That's it!

**[SIZE="2"]Removal[/SIZE]**:

If you'd like to revert back to the offical Ubuntu packages, simply use PPA-purge. First, ensure it is installed:

```
sudo apt-get install ppa-purge
```

...then, remove my PPA:

```
sudo ppa-purge ppa:ikarosdev/unity-revamped
```

I attempted my best to make "proper" packages, but I'm no expert. *Use my PPA at your own peril!*

I'll try my best to keep these builds up-to-date with the official Unity packages, but I can't make any promises. Good luck, guys!

[SIZE="3"]**Alternative Method (Compile from Source)**:[/SIZE]

**NOTE**: I tried this on a fresh installed of Ubuntu 12.04 32-bit. I can't say for sure if it'll work on older or other versions.

The first thing to do is to install all the dependencies needed to grab the source (from my Github) and build Unity:

```
sudo apt-get install git git-core
```

```
sudo apt-get build-dep unity
```

Now, we'll need a place to compile Unity. I usually like to create a folder called 'staging' and dump everything in there. You're welcome to put the source wherever you like, but just remember to change it accordingly for the tutorial:

```
mkdir ~/staging
```

...Now, we move into the directory:

```
cd ~/staging
```

Okay, the next step is to grab the modified source from my Github. While still in the 'staging' directory, run this command:

```
git clone git://github.com/isaacj87/unity.git
```

Once it's done pulling the source, we'll need to prepare our environment to build. We'll create a simple bash script and make it executable:

```
gedit unity.sh
```

...When the blank gedit window opens, copy and paste the following text into the file:

```
#!/bin/bash

PREFIX=/home/**YOURUSERNAMEHERE**/staging

export XDG_DATA_DIRS="$PREFIX/share:$XDG_DATA_DIRS"
export LD_LIBRARY_PATH="$PREFIX/lib/"
export PKG_CONFIG_PATH="$PREFIX/lib/pkgconfig/"
```

Notice the bolded text? You'll need to change that to your username (remove any forum syntax!). Once you've done that, save the file and close the window. Let's make the file executable and run it:

```
chmod +x unity.sh
```
```
./unity.sh
```

Okay, now let's build Unity! We'll need to create a build folder for the compile. Let's move into the Unity source directory and create that folder and move into it:
```
cd unity
```
```
mkdir build && cd build
```

Now, we'll prepare the build, compile and install:
```
cmake .. -DCMAKE_INSTALL_PREFIX=/home/**YOURUSERNAME**/staging/ -DCMAKE_BUILD_TYPE=Debug -DCOMPIZ_PLUGIN_INSTALL_TYPE=local -DGSETTINGS_LOCALINSTALL=ON
```(Remember to change the bolded text to your username! Also, remove any forum syntax!)
```
make -j4
```
```
make install
```

All done? Once that's finished, go ahead and log out and back in. Ensure that CCSM is installed and go into the Unity plugin configuration. Turn on the 'Dodge Windows' effect and it should work. Minimize an application to the launcher and click its icon again to unminimize it. If multiple windows of the same program are opened, the spread function should work as usual.

**Warning!**: When using this, do **not** delete anything in the staging folder. More specifically, do **not** delete the *bin*, *include*, *lib*, and *share* folders. You will have unwanted side-effects (i.e. Compiz/Unity will keep crashing)!

**[SIZE="2"]Removal[/SIZE]**:

If you'd like to revert back to "stock" Unity, simply remove ~/.compiz-1 folder and you should be back to normal. 

Feel free to leave any questions, comments or concerns.

**Credits**: *damianatorrpm* for the patch and *Jonathan French (ojno)* for the wonderful minimize behavior code.

---

### Post by isaacj87 on 2012-04-28
With the help of our friendly UbuntuForums admins and moderators, I've gone ahead an added this to the Ubuntu Help Wiki.

Link: [https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior]("https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior")

I've had a Launchpad account for years now, but I haven't done much with it. Later on, I'll see if I can figure out how to get a PPA up and running to make this an easier process.

---

### Post by cogadh on 2012-04-28
You, my friend, are full of awesome! The loss of the dodge function also threw my workflow into a tailspin and you just pulled me out of it. Thank you so much for this!

---

### Post by mgt2000 on 2012-04-28
You are greeeeeeeeeeeeeeeeat, Thaaaaaaaaaaanks :D

---

### Post by isaacj87 on 2012-04-28
Glad I could help, guys! 

I need to put a warning on the thread and wiki that anything in the staging folder (specifically the bin, include, lib, and share folders) **should not** be removed! I deleted them and was wondering why Compiz kept crashing!

---

### Post by mc4man on 2012-04-28
nice job putting together, always liked the min. on launcher icon from back in natty when it was available from the rejected branch

probably there will be another decent upgrade or 2 to unity in 12.04, expect one when compiz-0.9.8.X releases

(converted your changes here to patches so i could build as packages but the method you've described is certainly easier for users to revert back if need be.

---

### Post by isaacj87 on 2012-04-28
> **mc4man said:**
> nice job putting together, always liked the min. on launcher icon from back in natty when it was available from the rejected branch

probably there will be another decent upgrade or 2 to unity in 12.04, expect one when compiz-0.9.8.X releases

(converted your changes here to patches so i could build as packages but the method you've described is certainly easier for users to revert back if need be.

Thanks for the kind words. I'm actually in the process of building and testing some packages. Hopefully, I can get them working as updating would be kind of cumbersome for new users...

---

### Post by mc4man on 2012-04-28
I've noticed one little anomaly here, not that important & could be just here as I have a patched compiz to fix flashing & a patched scale to allow spread from all workspaces, either all windows or all from a window group

To check  - 
open 3 different windows on 1 workspace, say Firefox, nautilus, a terminal.
Minimize all 3 by clicking on the their icons
Go to spread (Super+W), pick one window
Back on desktop expose the remaining min'ed windows by clicking on icon.

Here they come up empty, re-minimizing & opening fixes.
Again _may be just here_, doesn't bother me

---

### Post by isaacj87 on 2012-04-28
> **mc4man said:**
> I've noticed one little anomaly here, not that important & could be just here as I have a patched compiz to fix flashing & a patched scale to allow spread from all workspaces, either all windows or all from a window group

To check  - 
open 3 different windows on 1 workspace, say Firefox, nautilus, a terminal.
Minimize all 3 by clicking on the their icons
Go to spread (Super+W), pick one window
Back on desktop expose the remaining min'ed windows by clicking on icon.

Here they come up empty, re-minimizing & opening fixes.
Again _may be just here_, doesn't bother me

I noticed something like this too, but I'm pretty I was experiencing 'blank' windows before I applied these patches. I *think* this is an upstream Compiz problem. I think the minimize/unminimize behavior might be aggravating the issue further though...

---

### Post by mc4man on 2012-04-28
Yeah - i just went to another install & see it there  _so not because of the min patch._
Hadn't noticed before, going to check against unity-5.10
edit: happens in 5.10 so something I hadn't noticed before - sorry to bring up here...

---

### Post by isaacj87 on 2012-04-29
Since this isn't the most user-friendly tutorial, I've decided to figure out how to setup and start a PPA (I didn't realize it was so complicated). In any case, I've tried my best to create "proper" packages and I'm awaiting the build farm to complete the builds.

I'll test the packages and make sure there aren't any harmful side-effects before I publish them. Hopefully, they'll turn out okay so others can go ahead take advantage of the PPA.

---

### Post by isaacj87 on 2012-04-29
Alright, guys...

Now, I realize that for novice users (or even those who abhor the terminal), building Unity just for a couple features seems kind of silly. So, I decided to sit down last night and try to figure out packaging and PPAs...

So, if you were hesitant about trying this before, you can now add my PPA if you feel more comfortable doing that.

**NOTE**: Since I'm running 32-bit, I've only tested the i386 packages. I'll need someone running 64-bit to let me know if it works okay.

**NOTE**: If you followed the tutorial originally, please remove ~/.compiz-1 and the 'staging' folder before you do this.

Add my PPA by doing this:

```
sudo apt-add-repository ppa:ikarosdev/unity-revamped
```

...then, simply run an update:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

...That's it!

If you'd like to revert back to the offical Ubuntu packages, simply use PPA-purge. First, ensure it is installed:

```
sudo apt-get install ppa-purge
```

...then, remove my PPA:

```
sudo ppa-purge ppa:ikarosdev/unity-revamped
```

I've tried this on a fresh install of Ubuntu 12.04 32-bit. Like I said, my PPA contains 64-bit packages, but they have not been tested. I attempted my best to make "proper" packages, but I'm no expert. Use my PPA at your own peril!

I'll try my best to keep these builds up-to-date with the official Unity packages, but I can't make any promises. Good luck, guys!

---

### Post by mgt2000 on 2012-04-29
It works perfect on 64 bit too. Thanks :)

---

### Post by Jack' on 2012-04-29
Ack, it works on 64 bit :P

---

### Post by isaacj87 on 2012-04-29
Thanks for testing it for me, guys. I'm glad that it's working. :)

---

### Post by fooman on 2012-04-29
oh man,  works perfectly on 64bit!!   :guitar:

thanks so much,  i really was missing this!

---

### Post by isaacj87 on 2012-04-29
Thanks for reporting back. The original post has been updated to recommend the PPA installation method.

---

### Post by LividLindy on 2012-04-29
Has anyone tried this in VirtualBox? I haven't been able to get it to work. The scripts for the dodge window feature didn't work either, but then it also didn't work on my Netbook.

You can see [here]("http://i.imgur.com/a1Rfg.png") it's not working. Also the minimize from clicking the launcher icon didn't work either.

I'm using the 12.04 desktop 64 bit version in VirtualBox.

---

### Post by isaacj87 on 2012-04-29
> **LividLindy said:**
> Has anyone tried this in VirtualBox? I haven't been able to get it to work. The scripts for the dodge window feature didn't work either, but then it also didn't work on my Netbook.

You can see [here]("http://i.imgur.com/a1Rfg.png") it's not working. Also the minimize from clicking the launcher icon didn't work either.

I'm using the 12.04 desktop 64 bit version in VirtualBox.

From what I can tell, you're not using Unity-3D in that picture; it looks like Unity-2D is running. This is probably because 3D acceleration isn't enabled for your virtual machine.

AFAIK, 'dodge windows' only works on Unity-3D.

---

### Post by mc4man on 2012-04-30
unity-2d does still have it's own version of dodge that works quite poorly at times (new windows on a empty workspace always open under the launcher which doesn't dodge them

It does appear that LividLindy is on unity-2d, in unity 3d the launcher would be colored among other things

This would show plainly 
```
echo $DESKTOP_SESSION
```

(- 12.10 will display quite plainly whether on unity (3d) or unity-2d, made a suggestion for 12.04 that involved a simple  3 character source edit to unity-2d but was rejected - wanted a unity-2d to show ubuntu-2d in the left corner of the panel panel instead of ubuntu like unity 3d

---

### Post by LividLindy on 2012-04-30
You were both correct I was in unity-2d, I knew I forgot to do something while setting up the new box to test this heh. 

Though I suppose it's good to know that this only works for unity not unity-2d so my mistake wasn't all in vain.

Anyways, it did work and I've now installed it on my main Ubuntu computer and worked fine there as well. Thank you very much for this, I was immensely disappointed to lose this feature.

---

### Post by jsevi83 on 2012-04-30
I'm testing it and dodge windows behaviour is working perfect, but there is no minimize on click. Also, if I open three terminals and click on the icon I don't get the spread behaviour to choose between the three, just the last one used gets activated.

I tried deleting .compiz-1 and restarting the session, with no luck. Am I doing something wrong?


Edit: Ubuntu 64bit

---

### Post by nilarimogard on 2012-04-30
Like jsevi83 said above, it seems there's a bug with minimize when there's more than one window for the same application (but minimize with a single window works fine for me). This is how it's supposed to work:

1. If there is no opened window for that app
1.a. Open a new window
2. If there is only one opened window for that app
2.a. Focus the window, if not focused
2.b. Minimize the window
2.c. Restore the window
2.d. Goto 2.a
3. If there is more than one opened window for that app
3.a. Focus the latest used window, if not focused
3.b. Open spread view
** 3.c. Close spread view and minimize all windows of that app**
3.d. Restore the latest used window
3.e. Goto 3.a

But step 3.c doesn't... it just opens the spread view but doesn't minimize the app.

---

### Post by isaacj87 on 2012-04-30
> **nilarimogard said:**
> Like jsevi83 said above, it seems there's a bug with minimize when there's more than one window for the same application (but minimize with a single window works fine for me). This is how it's supposed to work:

1. If there is no opened window for that app
1.a. Open a new window
2. If there is only one opened window for that app
2.a. Focus the window, if not focused
2.b. Minimize the window
2.c. Restore the window
2.d. Goto 2.a
3. If there is more than one opened window for that app
3.a. Focus the latest used window, if not focused
3.b. Open spread view
** 3.c. Close spread view and minimize all windows of that app**
3.d. Restore the latest used window
3.e. Goto 3.a

But step 3.c doesn't... it just opens the spread view but doesn't minimize the app.

This is how it's working for me:

No window opened:

- Open a new window of the program

One window opened (focused):

- Program will minimize on-click
- Program will unminimize on-click

One window opened (unfocused):

- Program will come into focus

Multiple windows opened (focused):

- Spread behavior will occur on-click
- Spread behavior will stop on-click returning both windows in view with the last one focused

Multiple windows opened (all but one minimized, focused):

- Spread behavior occurs on-click
- Spread behavior stops on-click returning only one visible window

Multiple windows opened (all minimized, focused):

- On-click will unminimize last window in focus
- Spread behavior occurs on-click

AFAIK, the minimize/unminimize patch (in its current form) doesn't minimize all opened instances after the spread view. I believe your expecting the behavior found in this comment: [https://bugs.launchpad.net/ayatana-design/+bug/733349/comments/58]("https://bugs.launchpad.net/ayatana-design/+bug/733349/comments/58")

However, I made some personal changes in order to get the patch to compile against Unity 5.12.0. I'll revert back to 5.10.0 and try ojno's PPA to see if I altered the intended behavior.

---

### Post by nilarimogard on 2012-04-30
I've found another bug: if you select "hide launcher - never" in CCSM, then log out, when you log back in, Window Dodge is active. So basically, the window dodge behaviour is restored each time you log in and can only be temporarily disabled.

---

### Post by jsevi83 on 2012-04-30
I found why it was not working. I don't use four desktops, so I only had one desktop enabled in compiz general options. When I added a second desktop (two horizontal desktops) it started working as expected.

---

### Post by nilarimogard on 2012-04-30
> **isaacj87 said:**
> This is how it's working for me:

No window opened:

- Open a new window of the program

One window opened (focused):

- Program will minimize on-click
- Program will unminimize on-click

One window opened (unfocused):

- Program will come into focus

Multiple windows opened (focused):

- Spread behavior will occur on-click
- Spread behavior will stop on-click returning both windows in view with the last one focused

Multiple windows opened (all but one minimized, focused):

- Spread behavior occurs on-click
- Spread behavior stops on-click returning only one visible window

Multiple windows opened (all minimized, focused):

- On-click will unminimize last window in focus
- Spread behavior occurs on-click

AFAIK, the minimize/unminimize patch (in its current form) doesn't minimize all opened instances after the spread view. I believe your expecting the behavior found in this comment: [https://bugs.launchpad.net/ayatana-design/+bug/733349/comments/58](https://bugs.launchpad.net/ayatana-design/+bug/733349/comments/58)

However, I made some personal changes in order to get the patch to compile against Unity 5.12.0. I'll revert back to 5.10.0 and try ojno's PPA to see if I altered the intended behavior.

You can see how the patched worked with Unity 5.10 in this video: [http://www.youtube.com/watch?v=h_bkPbbJlUk](http://www.youtube.com/watch?v=h_bkPbbJlUk)

---

### Post by isaacj87 on 2012-04-30
> **nilarimogard said:**
> You can see how the patched worked with Unity 5.10 in this video: [http://www.youtube.com/watch?v=h_bkPbbJlUk](http://www.youtube.com/watch?v=h_bkPbbJlUk)

Hmmm, that's odd. I just installed ojno's (patch developer) packages from his PPA and it doesn't work like that (i.e. no minimize all windows after spread). I'll send him a message and/or file a bug report to see what his thoughts are.

Concerning the other bug, I'm currently in the last 2 weeks of classes, but I'll have a crack at it when I find some time, but I'm currently experiencing the problem as well.

EDIT: I think I may found the problem to the options bug, I'll try a fix later on tonight and see if it works.

---

### Post by Enigmapond on 2012-04-30
Thank you for this!

---

### Post by isaacj87 on 2012-04-30
> **nilarimogard said:**
> I've found another bug: if you select "hide launcher - never" in CCSM, then log out, when you log back in, Window Dodge is active. So basically, the window dodge behaviour is restored each time you log in and can only be temporarily disabled.

So, I've figured out and implemented a quick fix for this problem. It seems to be working just find for me, but shouldn't be the end-all solution.

From what I can tell, it wasn't the best idea to simply drop in the original dodge windows code into the current Unity as the way options are set has changed dramatically. However, I see no harm in how things are working currently other than it being sloppy.

---

### Post by isaacj87 on 2012-04-30
> **nilarimogard said:**
> Like jsevi83 said above, it seems there's a bug with minimize when there's more than one window for the same application (but minimize with a single window works fine for me). This is how it's supposed to work:

1. If there is no opened window for that app
1.a. Open a new window
2. If there is only one opened window for that app
2.a. Focus the window, if not focused
2.b. Minimize the window
2.c. Restore the window
2.d. Goto 2.a
3. If there is more than one opened window for that app
3.a. Focus the latest used window, if not focused
3.b. Open spread view
** 3.c. Close spread view and minimize all windows of that app**
3.d. Restore the latest used window
3.e. Goto 3.a

But step 3.c doesn't... it just opens the spread view but doesn't minimize the app.

I've fixed the behavior to act like you described. While it works, the bug discussed earlier in this thread (blank after unminimizing) is very noticeable.

However, the behavior now works like this:

Multiple windows are opened -> Spread occurs on-click -> All windows are minimized on-click -> Last windows in focus will appear individually on-click.

For now, until the 'blank window issue' is fixed upstream, I'll leave the current behavior as is. However, I'll push the changes to my Github so you can pull them if you want.

---

### Post by mc4man on 2012-04-30
Filed the other day on the blank windows, actually many ways to cause
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/990867](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/990867)

Edit: I noticed in BamfLauncherIcon.cpp you changed windows to windowList in 2(?) places, wondering why?

---

### Post by jsevi83 on 2012-04-30
The spread windows behaviour and minimize on click is not working when there is only one workspace set in compiz preferences. When two or more worspaces are set it works perfectly. I don't know if that is a bug or if there is a reason why it happens.

---

### Post by isaacj87 on 2012-05-01
> **mc4man said:**
> Filed the other day on the blank windows, actually many ways to cause
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/990867](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/990867)

Edit: I noticed in BamfLauncherIcon.cpp you changed windows to windowList in 2(?) places, wondering why?

I'll admit, I'm not the strongest C++ programmer. Where should I put the windowList variable? Is there something wrong with the way I'm using the vector?

FWIW, I basically just went along with what ojno did for the original patch.

---

### Post by x-shaney-x on 2012-05-01
Just wondering if you would be willing to implement the patch/hack submitted in this mailing list discussion? [https://lists.launchpad.net/unity-design/msg09055.html](https://lists.launchpad.net/unity-design/msg09055.html)

If it wouldn't create more headaches, of course :)

And this is the patch itself: ```
=== modified file 'plugins/unityshell/src/PanelMenuView.cpp'
--- plugins/unityshell/src/PanelMenuView.cpp	2012-04-11 00:37:25 +0000
+++ plugins/unityshell/src/PanelMenuView.cpp	2012-04-15 14:43:24 +0000
@@ -352,6 +352,7 @@
 
 bool PanelMenuView::DrawWindowButtons() const
 {
+
   auto wm = WindowManager::Default();
   bool screen_grabbed = (wm->IsExpoActive() || wm->IsScaleActive());
 
@@ -361,10 +362,7 @@
   if (_we_control_active && _is_maximized && !screen_grabbed &&
       !_launcher_keynav && !_switcher_showing)
   {
-    if (_is_inside || _show_now_activated || _new_application)
-    {
-      return true;
-    }
+    return true;
   }
 
   return false;
@@ -528,8 +526,7 @@
     {
       double title_opacity = 0.0f;
 
-      if (_we_control_active && _window_buttons->GetOpacity() == 0.0 &&
-          (!has_menu || (has_menu && GetOpacity() == 0.0)))
+      if (_we_control_active && (!has_menu || (has_menu && GetOpacity() == 0.0)))
       {
         title_opacity = 1.0f;
       }
@@ -538,11 +535,11 @@
         title_opacity = 1.0f;
 
         if (has_menu)
-          title_opacity -= MAX(GetOpacity(), _window_buttons->GetOpacity());
+          title_opacity -= MAX(GetOpacity(), GetOpacity());
         else
-          title_opacity -= _window_buttons->GetOpacity();
+          title_opacity -= GetOpacity();
 
-        if (!draw_window_buttons && !draw_menus)
+        if (!draw_menus)
         {
           // If we're fading-out the buttons/menus, let's fade-in quickly the title
           title_opacity = CLAMP(title_opacity + 0.1f, 0.0f, 1.0f);
@@ -720,6 +717,9 @@
   int x = MAIN_LEFT_PADDING + TITLE_PADDING + geo.x;
   int y = geo.y;
 
+  if (DrawWindowButtons())
+    x += _window_buttons->GetContentWidth();
+
   int text_width = 0;
   int text_height = 0;
   int text_space = 0;
```

It makes the close buttons visible on the menubar always with the window title so only the menu itself is hidden til mouseover.

---

### Post by isaacj87 on 2012-05-01
> **x-shaney-x said:**
> Just wondering if you would be willing to implement the patch/hack submitted in this mailing list discussion? [https://lists.launchpad.net/unity-design/msg09055.html](https://lists.launchpad.net/unity-design/msg09055.html)

If it wouldn't create more headaches, of course :)

It makes the close buttons visible on the menubar always with the window title so only the menu itself is hidden til mouseover.

I like it, and for the most part, it works pretty well. Unfortunately, the patch seems to have an overlapping issue. Check out the attached screenshot.

---

### Post by x-shaney-x on 2012-05-01
Aw that's a shame.  Maybe something changed in unity since the patch was submitted?

---

### Post by isaacj87 on 2012-05-01
> **x-shaney-x said:**
> Aw that's a shame.  Maybe something changed in unity since the patch was submitted?

From what I can tell, it looks like the dodge window behavior seems to screw it up. It's something about launcher position that tells where the window controls should be at any given time.

With the "official" launcher hide behavior (never and auto-hide), the patch probably works just fine.

---

### Post by x-shaney-x on 2012-05-01
Yes, that does make sense.
I may have a poke around with it when I get some time and experiment.
See if I can find the bit that deals with placement and see if I can alter it to keep a constant position.

---

### Post by mackuz on 2012-05-04
This is really great! It brought back my interest in life :)

But what will happen when Unity team will release an update or a new version?
And what will happen if only patch is installed from GIT?

---

### Post by isaacj87 on 2012-05-04
> **mackuz said:**
> This is really great! It brought back my interest in life :)

But what will happen when Unity team will release an update or a new version?
And what will happen if only patch is installed from GIT?

If you're building and installing this from my Github, I believe the local install will overtake any version of Unity.

If you're using the PPA, I'll attempt to patch the latest stable release of Unity and put packages up on the PPA.

EDIT: I have some updates coming soon. Unfortunately, it's finals week, so I'm preparing for those. There were some bugs mentioned in this thread that I have fixed. For those using the "compile from source" method, you should already have those fixes.

---

### Post by mackuz on 2012-05-04
So the better way is installing from Github, and Unity will be updating and the patch will work.
Is it right?

---

### Post by isaacj87 on 2012-05-06
> **mackuz said:**
> So the better way is installing from Github, and Unity will be updating and the patch will work.
Is it right?

You'll get the same results either way. Building and installing from Github would technically be faster, but the changes will make it to my PPA too.

I've gone ahead and sent up the changes to be built. The new packages should be available soon. Here's the relevant changelog:

```
unity (5.12.0-0ubuntu2+ikarosdev1) precise; urgency=low

  * Bug-fix release.
    - Cleanup after merging original 'dodge windows' code into 5.12.0
    - Fix bug which "forgets" hiding behvavior settings when user logs-out or reboots
    - Fix bug which doesn't minimize all windows after spread function
```

EDIT: My build was rejected. I noticed I forgot to clean up files in my orig.tar.gz, so I attempted to upload a new one. Unfortunately, LP will reject these. I'm having to delete the already existing package and start fresh. I'm awaiting my package deleting and I'll upload the new changes. This shouldn't have any effect on existing PPA users. I'm still learning how to use my PPA. Thank you for your patience.

EDIT2: I think I sorted the issues out. 32 and 64-bit packages are available for update.

---

### Post by WorLord on 2012-05-08
> **jsevi83 said:**
> The spread windows behaviour and minimize on click is not working when there is only one workspace set in compiz preferences. When two or more worspaces are set it works perfectly. I don't know if that is a bug or if there is a reason why it happens.

It's a bug [NOW (996604)]("https://bugs.launchpad.net/unity/+bug/996604"), I can tell you that.  Please mark it as affecting you as well.

---

### Post by jsevi83 on 2012-05-09
I just marked the bug as affecting me too. Same as you, I don't use multiple workspaces and dislike having the worspace switcher icon in the launcher.

---

### Post by Jack' on 2012-06-08
There was an unity update a few days ago. 

[https://launchpad.net/ubuntu/+source/unity/5.12-0ubuntu1.1/+changelog](https://launchpad.net/ubuntu/+source/unity/5.12-0ubuntu1.1/+changelog)

> unity (5.12-0ubuntu1.1) precise-proposed; urgency=low    
* Cherry pick upstream fixes.     
     - Fix UnityViewWindow background when blur is disabled (LP: [#989291]("https://launchpad.net/bugs/989291"))     
     - App icon on the Unity Launcher lost track of running       instance (LP: [#772063]("https://launchpad.net/bugs/772063")) 
     - No launcher icon or Alt+Tab entry for Gimp windows (LP: [#995916]("https://launchpad.net/bugs/995916")) 
     - Locked smuxi launcher icon does not indicate smuxi running       status (LP: [#999820]("https://launchpad.net/bugs/999820")) 
     - Fix dash search field hidden by tooltips (LP: [#978030]("https://launchpad.net/bugs/978030"))     
     - Launcher is silent to screen reader users (LP: [#949448]("https://launchpad.net/bugs/949448"))     
     - Fix 3D apps running much slower under Unity (LP: [#987304]("https://launchpad.net/bugs/987304"))     
     - Reduced number of calls to ResultViewGrid::QueueDraw     
     - Reduced number of calls to BGHash::RefreshColor  -- Alan Pope <[popey@ubuntu.com]("https://launchpad.net/%7Epopey")>   Wed, 23 May 2012 18:10:49 +0100Just to let you know ;-)

---

### Post by isaacj87 on 2012-06-10
> **Jack' said:**
> There was an unity update a few days ago. 

[https://launchpad.net/ubuntu/+source/unity/5.12-0ubuntu1.1/+changelog](https://launchpad.net/ubuntu/+source/unity/5.12-0ubuntu1.1/+changelog)

Just to let you know ;-)

Hmmm, those are some good fixes (especially the GIMP no alt-tab icon bug). Unfortunately, I'm hosting my stuff on Github and I can't directly cherry pick those fixes (unless someone else can tell me how). The best solution would be to host the Unity source on LP like I should of done.

Currently, I'm only building packages from stable releases. I wasn't planning on building anything from trunk. If time permits, maybe I will. As it stands now, I don't have a lot of free time. :(

---

### Post by x-shaney-x on 2012-06-16
I decided to give up on dodge and just get on with using autohide or always show because I don't want to mess around with PPA's, it's more things to have to do after an installation.
Alas, I just miss it so much and have problems with the other two solutions so have gone ahead and used this PPA and it's brilliant :)

It's quite frustrating that Chrome OS has now adopted a dodge style taskbar (or more like KDE's "windows can cover") behaviour.

Shame it's too confusing for ubuntu users.

---

### Post by isaacj87 on 2012-06-17
> **Jack' said:**
> There was an unity update a few days ago. 

[https://launchpad.net/ubuntu/+source/unity/5.12-0ubuntu1.1/+changelog](https://launchpad.net/ubuntu/+source/unity/5.12-0ubuntu1.1/+changelog)

Just to let you know ;-)

I've gone ahead and created a new branch for unity-revamped on LP. You can see this here: [https://code.launchpad.net/~ikarosdev/unity/5.0_unity-revamped]("https://code.launchpad.net/~ikarosdev/unity/5.0_unity-revamped")

I haven't added ojno's minimize/unminimize feature, but I have re-added the dodge windows feature. After I'm finished adding everything back to the updated 5.0 branch, I'll build some new packages with the fixes you described.

EDIT: If you guys are comfortable with building Unity yourself, you can go ahead and pull a copy and make sure everything works. I'm currently testing the changes right now and everything seems okay.

EDIT2: Everything has been re-added to my branch on LP. Updated packages will be coming soon after I make sure everything is working nicely.

EDIT3: Packages are building...

```
unity (5.12.0-0ubuntu2+ikarosdev2) precise; urgency=low

  * Cherry pick upstream fixes.
    - Fix UnityViewWindow background when blur is disabled (LP: #989291)
    - App icon on the Unity Launcher lost track of running instance (LP: #772063)
    - No launcher icon or Alt+Tab entry for Gimp windows (LP: #995916)
    - Locked smuxi launcher icon does not indicate smuxi running status (LP: #999820)
    - Fix dash search field hidden by tooltips (LP: #978030)
    - Launcher is silent to screen reader users (LP: #949448)
    - Fix 3D apps running much slower under Unity (LP: #987304)
    - Reduced number of calls to ResultViewGrid::QueueDraw
    - Reduced number of calls to BGHash::RefreshColor
    - Properly fix spread when minimizing all windows
 -- Isaac Joseph <ikarosdev@gmail.com>   Sun, 17 Jun 2012 19:56:11 -0500
```

---

### Post by isaacj87 on 2012-06-19
Can anyone confirm that they received updated packages? I'm pretty sure it worked for my other laptop, but ppastats aren't registering any downloads for the new packages...

---

### Post by x-shaney-x on 2012-06-19
Yes, I got the updates yesterday and everything working fine as far as I can tell :)

---

### Post by isaacj87 on 2012-06-19
> **x-shaney-x said:**
> Yes, I got the updates yesterday and everything working fine as far as I can tell :)

Thanks for reporting back! This is definitely good news. Now that everything is on LP, I have everything synced with the Unity 5.0 series! So when 5.14.0 is released, there shouldn't be any problems. :)

Long live dodge windows! :twisted:

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior](https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012412](http://ubuntuforums.org/showthread.php?t=2012412)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

