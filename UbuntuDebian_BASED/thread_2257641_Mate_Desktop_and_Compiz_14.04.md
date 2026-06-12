---
title: "Mate Desktop and Compiz 14.04"
date: 2014-12-21
forum: Ubuntu/Debian BASED
---

### Post by ibjsb4 on 2014-12-21
I have added compiz per:
[http://wiki.mate-desktop.org/compiz#ubuntu](http://wiki.mate-desktop.org/compiz#ubuntu)

In compiz configure I have gone to 'Effects' and activated the 'Window dressing' plugin, but it has no effect. I need my title bar.

Have I missed something?

---

### Post by ibjsb4 on 2014-12-21
I just found out that window decoration must be set before the command 'compiz --replace'.  I now have a title bar.

But I am getting this warning in terminal:
```
compiz (decor) - Warn: No default decoration found, placement will not be correct
```
Using default settings
[ATTACH=CONFIG]258724[/ATTACH]

---

### Post by buzzingrobot on 2014-12-21
Make sure all the packages listed at that wiki.mate-desktop.org page are actually installed.  I seem to remember that the recommended "sudo apt-get install ...' line did not pull them all in.

I also found I need to log out/log in when I switch to compiz for the decorations to appear correctly.

---

### Post by ibjsb4 on 2014-12-21
Hi buzzingrobot
> Make sure all the packages listed at that wiki.mate-desktop.org page are actually installed. I seem to remember that the recommended "sudo apt-get install ...' line did not pull them all in.
That is correct and all have been added, thanks.
> I also found I need to log out/log in when I switch to compiz for the decorations to appear correctly.
Found that out this morning, thanks :)

Also got the workspace switcher working and next is the cube.

Im new to compiz, got any tips on the cube?

I will just use 'compiz --replace' command for now.

---

### Post by ibjsb4 on 2014-12-21
I should add that I am going for maximum eye candy.

---

### Post by deadflowr on 2014-12-21
Cube is pretty basic to setup.
First adjust the workspaces in General Options > Desktop Size > usuially set the H(horizontal) to 3 or more(can go as high as 30 or so) and set the v(vertical) to 1.

Then enable desktop Cube, and Cube Rotate. Then look at setting the various parameters; like zoom, or skydome, or what have. 
(If you have the other cube plugin, cube reflection and deformation, enable that one too and play around some)
 
You can, if you want try to set 3dWindows, but there is a good chance of clipping. If that happens just disable it.
(You'll understand the clipping when you see it)

If you want max eye candy play around with all the setting in Effects.
I would start with Animations and play with those various settings, like "make the closed window explode and other fun stuffs.

You might also look at seeing if it is still possible to install the experimental plugins, which you need to add manually.
Here's one place that has some
[http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+U%2BD+3-18-12?content=118511](http://gnome-look.org/content/show.php/Compiz+Experimental+Plugins+U%2BD+3-18-12?content=118511)

Edit: I should probably point out you can expect a certain feeling of total breakage through out the enabling and disabling of each plugin you play with. This is normal, best practice is to ride it out. It's a rare instance where it won't eventually reset itself. Sometimes it might take a little longer than you might want.(ie several minutes of a totally frozen screen) If it stays frozen for a really really long time(like half an hour or more), then in that case something is terribly wrong.

---

### Post by ibjsb4 on 2014-12-21
> Edit: I should probably point out you can expect a certain feeling of  total breakage through out the enabling and disabling of each plugin you  play with.
I decided to test breakage and loaded all plugins that appealed to me (34 of them) and  no breakage yet.  I will remove them now and start with a few.

Thanks deadflowr for the informative post.  I am off and playing :)

---

### Post by deadflowr on 2014-12-21
Aside from the eye candy have some fun playing around with the window management tools, like place windows, move windows, scale, etc etc.
You'll find a level of functionality you might not have expected by tweaking of a few of those.
It's the little things like having certain windows always open in a specific workspace. Little things like that.

---

### Post by ibjsb4 on 2014-12-23
Well I added some plugins and got things running.  No clipping.  I like what I have so far and want more.  All in due time I guess, but ..

I want windows to burn up upon closing and not hitting on the proper tweaks to do this.  Got fusion/extras installed.

Do you play with fire :)

---

### Post by deadflowr on 2014-12-24
Unfortunately, I think fire might have been pulled for the more recent versions of compiz-plugins.
Simply put it was no longer functional, and no one wanted to maintain it.
For as much as it was ever actually maintained.
:cry:

---

