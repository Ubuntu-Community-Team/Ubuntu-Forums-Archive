---
title: "Gnome-fallback feature request"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by JHCKX on 2012-03-24
Is there any way to submit a feature request for gnome-fallback? I looked at the launchpad site but there doesn't seem to be a way to provide feedback.

Gnome-fallback is great. I don't mind giving Unity a try but I want to be able to make my own choices. But one shortcoming of gnome-fallback is there's no way to empty the trash! It also doesn't work well with the default Ambiance theme, the names of running programs in the lower panel are almost the same grey colour as the panel.

Switching to the Radiance theme solves the second problem. Alt right-clicking a panel lets you modify it and add a trashcan (and eyes). But that's my third minor beef with gnome-fallback, alt right-clicking isn't something I could come up with without googling. Couldn't it work with just right-clicking?

But let me re-iterate, Gnome-fallback is great!

---

### Post by dino99 on 2012-03-24
im a fallback fan too, using radiance theme, but its a personal choice. 

there is two ways for your request.
- using brainstorm whishlist
- open a bug report with: ubuntu-bug gnome-session-fallback

note: hopes your nickname is a fake email address, otherwise you'll get bombed by bots of all kinds

---

### Post by jerrrys on 2012-03-24
Can't get trash to work? wow.  Maybe you should wait for the final release.

---

### Post by SemiExpert on 2012-03-24
> **John2.Hendrickx@gmail.com said:**
> Is there any way to submit a feature request for gnome-fallback? I looked at the launchpad site but there doesn't seem to be a way to provide feedback.

Gnome-fallback is great. I don't mind giving Unity a try but I want to be able to make my own choices. But one shortcoming of gnome-fallback is there's no way to empty the trash! It also doesn't work well with the default Ambiance theme, the names of running programs in the lower panel are almost the same grey colour as the panel.

Switching to the Radiance theme solves the second problem. Alt right-clicking a panel lets you modify it and add a trashcan (and eyes). But that's my third minor beef with gnome-fallback, alt right-clicking isn't something I could come up with without googling. Couldn't it work with just right-clicking?

But let me re-iterate, Gnome-fallback is great!

 Gnome-panel is buggy, at least from my experience this week.  I had two crashes involving the bottom panel and 100% CPU utilization for a single core.  I had to uninstall gnome-panel.  Do I think that gnome-panel belongs in the repostitory?  Sure?  But I don't think that it's appropriate as part of the .iso.

---

### Post by jbicha on 2012-03-24
dino99, the correct link is ubuntu-bug gnome-panel

I don't think the trash icon should show in gnome-panel by default; the GNOME developers don't have it on by default either. I just don't think people use the trash that often. You can easily empty the trash by opening your file manager. Right-click on the Trash link in the sidebar and click Empty Trash. I believe the Trash applet you can add to gnome-panel works the same way.

Personally, I access my Documents and Downloads folders multiple times almost every day, but I can't remember the last time I dug around in the trash.

---

### Post by NHclimber on 2012-03-29
> **JHCKX said:**
> But that's my third minor beef with gnome-fallback, alt right-clicking isn't something I could come up with without googling. Couldn't it work with just right-clicking?

The [sub-standard] reason why gnome-panel doesn't itself respond to right-click is because the right-click event is assumed to go to the underlying applet or widget (right-click on Applications brings up context menu with 'Edit Menus' action, right-click on a launcher brings up context menu with 'Properties' action, etc..)

I suppose it could be changed to respond to right-click in areas not occupied by an applet or widget but to a user the distinction between panel area and widget area might not be obvious.  For example, the area in between the 'Show desktop button' and the tasklist, might appear to be part of the panel but actually its part of the tasklist applet and it supposed to have a grab handle on it (but doesn't because of a bug in the theme engine). So right-clicking there brings up a 'Preferences' context menu which is preferences for the tasklist -- not the panel.

---

### Post by jbicha on 2012-03-30
I thought that the reason for Alt+right-click was to prevent people from accidentally moving or removing panel applets.

That said, I'd definitely take a look at a patch to revert that behavior.

---

### Post by hawthornso23 on 2012-03-31
Note that I'm still running Oneiric at this point. But unless this has changed yet again in Precise you actually need

```

<super><alt> rightclick     
```to modify a panel in gnome-fallback in the case that compiz is running. So the behavior depends on what window manager you have running. Bizarre!  That happened because ```
<alt> rightclick
```   broke compiz shortcuts.

---

