---
title: "Can someone tell me what these &quot;&gt;&quot; arrows are?"
date: 2012-03-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by blackplague1347 on 2012-03-26
When I open certain apps, to the left of them there will be a "less than" (>) symbol, as opposed to the usual solid triangle. When the ">" is there, I cannot alt-tab to the app in question. I don't know if this is a feature or a bug or what, but it's quite irritating when I'm trying to alt-tab between windows (which is how I prefer to do my actual work). 

Not sure if related, but most of the time when I open Pidgin, I can't see my buddy list, whether I click the app icon in the dock, or whether I use the envelope drop-down menu on the bar at the top of the screen. 

The only bug reports I know how to file are crashes, where the option to report them shows up automatically. So if these are bugs that I need to report, I am unsure of how to do so.

I took a screenshot, in case I poorly described the less than vs triangle issue. Pidgin and Chromium show the less than; nautilus has the triangle. If I press alt-tab right now, it will switch me to nautilus. If I then press alt-tab again, it will only allow me to switch to my desktop - Chromium and Pidgin are not on the alt-tab menu.

---

### Post by MG&amp;TL on 2012-03-26
The triangle arrows are *meant* to show apps open on a different workspace. Although by the sounds of things, you don't use workspaces...?

What happens if you click on them?

---

### Post by Procrustes on 2012-03-26
I think it means that the window is in a different workspace

---

### Post by blackplague1347 on 2012-03-26
I thought it might be a workspace thing. I forget what it was, but something led me to think that could be the case a couple of days ago. When I click the icon, it opens the app, as would be expected. Oddly enough, when I click the workspace switcher, every workspace except workspace 1 appears empty. 

Since this is apparently just a workspace issue, is there any setting I could change to have my apps open in the current workspace? I usually don't use them because it's faster for me to alt-tab a few times than it is for me to control-alt-arrow (I hit the wrong arrow key too often to be efficient =\ ).

One thing I've noticed is that if I click the Chromium icon and bring up the maximized window, I can click the top border of the window (the universal menu bar), drag it away (un-maximizing it), and then snap it back to the top (re-maximizing it) which will sometimes give me the triangle-arrow, rather than the less than arrow.

---

### Post by stinkeye on 2012-03-26
If you want to use the alt+tab switcher to show windows in all workspaces,
change the key in ccsm to "key to start switcher for all viewports".

---

### Post by grahammechanical on 2012-03-26
When you open an application a solid arrow appears on the left side of its launcher icon. Open additional windows for that application and two and then three solid arrows appear on the left side of the icon. Three is the maximum that you get.

When you have one of those windows focused a solid arrow appears on the right side of the icon.

Switch to another workspace and those solid arrows are replaced by an open arrow (which you are seeing) on the left side. It is an indication that there is an application open on another workspace.

When you are on a workspace with more than one application open and when the applications have more than one window open you can select them by pressing Alt-TAB and then you can use an arrow key to move through a sequence of icons. Pause over an icon for an application that has more than one window open and that icon will spread out to show you all the windows that are open for that application. You can move between them with an arrow key.

Have tried holding down the super key? You get an overlay of keyboard shortcuts.

Regards.

P.S. May I suggest something? In a few days Unity 5.8 will be released. We may get an opportunity to test it before it is put into 12.04. If you see an invitation, then take it. I have run three of these tests for Unity. It will teach you all about what you do do with Unity. It is a great way to learn.

---

### Post by Gregory Lee on 2012-03-26
> **blackplague1347 said:**
> 
Since this is apparently just a workspace issue, is there any setting I could change to have my apps open in the current workspace?
Just from observation (I haven't seen any instructions), if you're using Unity 3d, apps open in the workspace you're in.  The solid right-pointing triangle, &#9654;, at the left of the icon in the launcher, should appear as soon as the app which the icon is for has opened a window on your current workspace.  (The corresponding right-pointing arrow head, >, means that the app has a window open in another workspace.  If you always stay in the first workspace and open all your apps there, you should never see the > at the left of a launcher icon.)

The solid left-pointing triangle, &#9664;, at the right of an icon in the launcher, means that in the current workspace, the opened window of the corresponding app is in focus.  As you move your mouse from window to window and click, you should see the &#9664; move from icon to icon in the launcher bar.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-27
Also please take a look at [this thread here]("http://ubuntuforums.org/showthread.php?t=1927007").

---

