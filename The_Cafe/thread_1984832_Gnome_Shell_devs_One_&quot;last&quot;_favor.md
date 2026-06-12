---
title: "Gnome Shell devs: One &quot;last&quot; favor"
date: 2012-05-22
forum: The Cafe
---

### Post by Copper Bezel on 2012-05-22
Gnome Shell really works the way I want a window manager to work, even in weird, fiddly little ways. I mean, the UI is really weirdly exactly what I wanted. It's things like this:

[LIST]
[*]Under Compiz / Gnome 2, I used the upper-left hot corner for Scale, but hated that the dock and panel weren't clickable in the window spread. Of course, they are now, in Shell. The big X button for each window is much nicer than middle-clicking to close from the spread, as well.
[*]That also solves the problem of a fiddly dock that's either hidden or taking up valuable screen space. Shell's solution really does save me irritation here.
[*]I love the two-up view to death (and it's not really fair to give Gnome too much credit for Microsoft's idea that everyone else jumped on first, but I think it's handled best here.) I used to use vertical maximization for the same thing, but this is far less fiddly.
[*]It always bothered me that external monitors switched workspaces with the main desktop; I like being able to leave something on the external while I'm paging through whatever I'm using on my main display. Gnome handles this perfectly.
[*]Moving non-maximized windows from one workspace to another under Compiz meant sorting out the piles of windows once I got there, usually hanging over into another workspace. Shell keeps the positioning of the window and just switches it to a different workspace. I love that. And then there was the hunt for buried or minimized windows while in the workspace switcher, which isn't even a relevant problem in Shell. 
[*]I have to mention that I love the addition in 3.4 that windows can be dropped into the filmstrip between two workspaces to create another workspace there. It's very easy to stay organized.
[/LIST]

Real annoyances I had that the Shell devs really solved. I won't say that it means that I spend more time getting real work done. It means that I spend less time fighting with the window manager and more time appreciating the pretty little animations.

Now I want [_this_]("http://arstechnica.com/gadgets/2012/04/hands-on-getting-work-done-with-googles-new-aura-interface-for-chrome-os/") (scroll to the last screenshot in this page of the article.) Chrome OS's WM, like Windows 8 Metro's, can dynamically resize the "halves" of the display in the two-up configuration. You can grab the boundary between the two snapped windows and resize both. For taking notes from a web page or document, or any other situation where one window is the "tool" and the other is the "content," this seems extraordinarily useful. As it is, Gnome's snapped windows can't be resized, and I wouldn't want them to resize normally, either, but changing the size of the snapped regions on a per-workspace basis would be absolutely beautiful. Then I could have a notepad on the left and document on the right and switch out the document window for another in the same slot, in the same way that I can apparently do with Windows 8's Twitter and photo viewer apps. = P

So, two ways to go with this - am I right to think that this is a feature that would fit in well with the Shell design? Or, if you're also using Shell, are there other features you'd like, the next "last" missing piece of your UX?

---

### Post by forrestcupp on 2012-05-22
Yeah, that would be useful. For now, you just have to do it manually by dragging one window to the left and one to the right.

---

### Post by rai4shu2 on 2012-05-22
Am I crazy, or isn't all that more complicated and distracting than the old desktop paradigm? I mean, if being more distracted works for you, then great. But I don't really see how keeping track of hot corners and docks and panels is somehow less distracting than just having one panel.

---

### Post by BigSilly on 2012-05-22
> **rai4shu2 said:**
> Am I crazy, or isn't all that more complicated and distracting than the old desktop paradigm? I mean, if being more distracted works for you, then great. But I don't really see how keeping track of hot corners and docks and panels is somehow less distracting than just having one panel.

That's not really how it is in practice. I agree that Shell is pretty awesome personally.

---

### Post by rai4shu2 on 2012-05-22
Don't get me wrong. That would be a very consistent feature for Gnome Shell. Very befitting that environment. I'm just not sure about the appeal of that environment. I really should try it out one of these days.

---

### Post by Copper Bezel on 2012-05-22
Yeah, I'm thinking more in terms of just how it would fit in. Of course, Chrome OS Aura uses a fairly simple, traditional desktop paradigm, and it seems to fit in there, too. I guess it's just a natural extension of Aero Snap.

In general, though, Gnome Shell is actually *simpler* than my Gnome 2 setup was, but I'm well aware that some folks need less (and that some folks need more.) The problems on that list were things that Shell solved for me, but they're definitely not problems everyone has.

[QUOTE=forrestcupp]Yeah, that would be useful. For now, you just have to do it manually by dragging one window to the left and one to the right.[/QUOTE]
If the window is snapped, I don't even get the resize cursor when I hover the edge. I can use the keyboard shortcut to resize it, but I notice that doing so unsnaps the window, for whatever that's worth. Of course, the resize grips come in handy in those situations (if the theme supports them, which Adwaita does not. Grr.)

---

### Post by forrestcupp on 2012-05-23
> **Copper Bezel said:**
> 
If the window is snapped, I don't even get the resize cursor when I hover the edge. I can use the keyboard shortcut to resize it, but I notice that doing so unsnaps the window, for whatever that's worth. Of course, the resize grips come in handy in those situations (if the theme supports them, which Adwaita does not. Grr.)
Never noticed that. That's kind of dumb.

---

### Post by Copper Bezel on 2012-05-23
Yeah, Gnome doesn't make resizing windows to anything but default, maximized, or half-maximized easy, and the behavior that would be replaced by the Aura / Metro one is "do nothing," so I think it's a feature with a place. I like Ubuntu's overlay scrollbars, though, and they're bound to create a conflict. (I guess I'd just have to approach the "divider" region from the right. Obviously, Shell and the overlay scrollbar aren't meant to be used in concert, but they work together well for now.)

---

### Post by gamblor01 on 2012-05-23
> **Copper Bezel said:**
> 

Now I want [_this_]("http://arstechnica.com/gadgets/2012/04/hands-on-getting-work-done-with-googles-new-aura-interface-for-chrome-os/") (scroll to the last screenshot in this page of the article.) Chrome OS's WM, like Windows 8 Metro's, can dynamically resize the "halves" of the display in the two-up configuration. You can grab the boundary between the two snapped windows and resize both.

Have you looked at the shellshape extension?

[https://extensions.gnome.org/extension/294/shellshape/](https://extensions.gnome.org/extension/294/shellshape/)


It might do some or all of what you are looking for.  There are lots of goodies on extensions.gnome.org.  If you haven't checked them out yet, I highly encourage you to look through them.  A few that I use and highly recommend:

- Steal my focus
- Alternative status menu
- Calculator
- Notifications Alert
- Quicklaunch
- Remove accessibility


I just recently switched over to gnome shell.  I previously used Unity, and I actually really liked it.  But after trying shell, installing those extensions, and adding AWN as a dock (on the left -- just like the Unity launcher) I am finding that I really like shell better.  It's just easier to customize, has some really great features, and in my opinion it's prettier.  Certainly nice looking with the Faience-azul icons on my AWN dock.

We'll have to agree to disagree about the overlay scrollbars though.  I remove them immediately because I can't stand them.  :)

---

### Post by JDShu on 2012-05-23
> **gamblor01 said:**
> 
I just recently switched over to gnome shell.  I previously used Unity, and I actually really liked it.  But after trying shell, installing those extensions, and adding AWN as a dock (on the left -- just like the Unity launcher) I am finding that I really like shell better.  It's just easier to customize, has some really great features, and in my opinion it's prettier.  Certainly nice looking with the Faience-azul icons on my AWN dock.


Being a Shell user, I'm biased, but this seems to be quite common for those of us who are willing to try new UIs. It was the same for me too. I have a theory that Unity is a good stepping stone towards using Shell, because it is more similar to traditional desktops, while still being different.

I must admit I don't like the overlay scrollbars in Unity, because they are less featureful (no quick scrolling by clicking on the space) and actually using them takes a bit too much concentration. I guess it's not as big an issue when you have two finger scrolling on laptops or for tablet devices.

---

### Post by Copper Bezel on 2012-05-23
Yeah, and I really just like them as indicators of where I am in a page. I almost always use two-finger scrolling instead of actually grabbing them. Even edge scrolling seems simpler than actually finding and dragging the scrollbar, and the (minor) pixel cost annoys me on a netbook screen.

gamblor01, yeah, I've browsed through the extensions page quite a bit and have a couple of extensions I can't live without, like the Zeitgeist search, window-driven Alt+Tab and keyboard workspace switching in the overview. (Two of which I felt were missing features before the extensions were launched. Extensions really do solve problems.) But thanks for the recommendation. It's not exactly what I'm looking for, but I'll play with it.

Oh - if you're using AWN for task switching, try installing the DockBarX applet for it. It's all the features of the Unity Launcher and the Windows 7 superbar tasks combined. Quite a step up from AWN's default task list.

---

### Post by markbl on 2012-05-23
> **JDShu said:**
> 
I must admit I don't like the overlay scrollbars in Unity, because they are less featureful (no quick scrolling by clicking on the space) and actually using them takes a bit too much concentration. 
I agree that it is a shame we have lost that function and they are a bit awkward to use, but on the plus side the overlay scrollbars take up less room and certainly look much better.

I installed the latest debian unstable a few days ago to see what gnome-shell looked like there and must admit that the old style scrollbars look extremely ugly now.

---

### Post by Copper Bezel on 2012-05-23
God, that just gets into the old debate about Gnome and Canonical's toxic relationship. Gnome apparently intends to duplicate the overlay scrollbar effort for no reason at all, [s]along with Unity-like quicklists[/s]. And the appindicator spec that started the damned fight would have worked better with Gnome Shell than retaining the old indicators does, because dbus can communicate with the Shell, so all notification tray menus would be consistently drawn by the shell and accessible without leaving the overview. The overlay scrollbars are just the one feature where we lucked out that Gnome didn't have to actually write any code to support Canonical's.  = P

Edit: Correction: I looked into it, and the quicklist work isn't being duplicated, as Gnome really is going to attempt to follow the Ayatana spec on that one. My bad.

---

### Post by gamblor01 on 2012-05-24
> **Copper Bezel said:**
> Oh - if you're using AWN for task switching, try installing the DockBarX applet for it. It's all the features of the Unity Launcher and the Windows 7 superbar tasks combined. Quite a step up from AWN's default task list.

I guess this is another thing we'll have to disagree on.  Don't get me wrong I think that the Unity badges/progress bars behaviors are very useful.  However, I just couldn't get the launchers in the dockbarx applet to look decent.  They aren't sized the same as the awn applets, they are offset, don't have the same little triangular indicators, have a glow behind them, etc.  Using that just made everything look goofy and sloppy because it wasn't consistent.  My workflow hasn't really been impacted by this so I'm just using awn for now and hoping that they will eventually include these items for the task manager applet as well.

---

### Post by Copper Bezel on 2012-05-24
Yeah, I recommended it for workflow reasons, not the look. The sizing and styling of the DockBarX items are all controlled by user-editable themes, but I seem to have lost the theme I was using (and it was Orta / Faenza styled in any case.) You can force them to mesh with the other AWN applets by controlling the icon size and spacing, but I never really had anything but DBX on my dock panel, anyway. And I forgot that most of the really cool features depend on Compiz, so. = / N/M.

---

### Post by gamblor01 on 2012-05-24
> **Copper Bezel said:**
> Yeah, I recommended it for workflow reasons, not the look. The sizing and styling of the DockBarX items are all controlled by user-editable themes, but I seem to have lost the theme I was using (and it was Orta / Faenza styled in any case.) You can force them to mesh with the other AWN applets by controlling the icon size and spacing, but I never really had anything but DBX on my dock panel, anyway. And I forgot that most of the really cool features depend on Compiz, so. = / N/M.

Yeah I was excited to get the window thumbnails back only to realize that they weren't working at all.  After thinking about it for a few seconds I remembered that they rely on compiz and of course, since I'm on shell it's all mutter anyway.  Bummer...but oh well.

---

### Post by gamblor01 on 2012-05-24
> **Copper Bezel said:**
> But thanks for the recommendation. It's not exactly what I'm looking for, but I'll play with it.

Hey I was just looking at gnome shell shortcuts ([http://library.gnome.org/users/gnome-help/stable/keyboard-nav.html.en](http://library.gnome.org/users/gnome-help/stable/keyboard-nav.html.en)) and found out a few useful ones that sort of do this same window snapping thing.  Try holding the super key and pressing arrow keys...

[LIST]
[*]super+left: Maximize a window vertically along the left side of the screen. Press again to restore the window to its previous size.
[*]super+right: Maximize a window vertically along the right side of the screen. Press again to restore the window to its previous size.
[*]super+down: Restore a maximized window to its original size.
[*]super+up: Maximize a window, or restore a maximized window to its original size.
[/LIST]

---

