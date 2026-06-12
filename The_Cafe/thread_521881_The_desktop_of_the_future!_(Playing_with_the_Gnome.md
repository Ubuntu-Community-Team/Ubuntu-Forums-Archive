---
title: "The desktop of the future! (Playing with the Gnome panel)"
date: 2007-08-09
forum: The Cafe
---

### Post by Mr. Picklesworth on 2007-08-09
One thing I like about Windows Vista is its clean, tidy desklets achieved through that nice sidebar it has.

When I add panels in Ubuntu, I always end up having to consider the amount of my screen they will end up consuming. The ability to have some only above the desktop and not obscuring any other windows would be quite excellent, letting me add all the useless / fun gadgets I want.

One thing I am not satisfied with regarding the current situation of the Gnome desktop is the lack of a desklets implementation that does not hate me.

I found this weird, because gnome-panel already does some really nice stuff with panel applets. Why can't it do desklets?

Something I do not like about Windows Vista is how its sidebar is portrayed as the second coming of Christ...

Thus, I decided to put things right, having a panel and a tidy desklets solution in Ubuntu, both seamlessly integrated under one concept. (Take *that*, Windows!)

It took very few actual changes to gnome-panel itself, which means that this, with some extra tweaking, is probably the best way to do desklets. (Please excuse my complete lack of modesty). By tying together desklets and panel applets, we are not unnecessarily reusing code to achieve some eye candy. (I stopped using gdesklets, for example, because it was clearly consuming valuable memory, CPU time and visible space on my menu just so I could have a pretty looking clock on my desktop).

So, I sat down yesterday and have been playing with gnome-panel to create a desklets thing myself. (Thanks to those who helped me with my ignorant questions!). It took very few significant changes - just the addition of a single command and a harmless new option in the properties. (And a lot of learning).
Somehow, after a lot of copying and pasting, I think I also have the configuration thing working pretty solidly for it, too. (I take it back, if anyone heard me yelling just a while ago: Gconf is not stupid!).

The panel set to stay behind normal windows is still setting struts, which means that maximized windows will fit around it (instead of going over it) and that you feel a little sticky edge as you move a window over it. I also have to make this code of mine a bit more defensive, as right now it will probably cause problems with any errors.
Also, quite bothersomely, this thing will probably not play nice with the desktop icons. (Which brings to mind some applets to replace them).
As well, (though I am unsure if this should be fixed) a drawer in an always beneath window has to be told to be always beneath or it will appear on top of everything. I guess drawers could inherit the property from their parents...


As I mentioned, I made an addition to the properties window. I realize that this is a foolish action, but in this case I think "Always beneath" is a much more necessary option than "Arrows on hide buttons," so if anything should go it is that.
"Always beneath" is a pretty ugly name for that option, though. Do you have any suggestions?
I had tried "Always above", but I decided it would make more sense with the unchecked option meaning "change nothing," while the checked option means something unusual occurs. (In this case, the panel being below normal windows is overriding the default behaviour of the windowing system).

I should admit that I cheated a little with the screenshots below. The panels are usually limited to 120 pixels wide (and I have yet to learn why), but a panel like this should be significantly larger, so I resized it via the gconf editor to 200.

Truth be told, this little adjustment does not deserve this big a post since it is far from perfect; there are no applets that really work with this style of panel (yet), making it quite pointless. That, and it isn't really a major change anyway. (Which brings to mind the question of why it hasn't been done before, since having the panel do this is Really nice!)
The purpose of this thread is to discuss the wonderful things we gain by having panels not permanently consume screen space! I want to make this little change actually worthwhile, so what do you think would be a really great, unique and intuitive panel applet to go here?


Attached images:
1. A sidebar, like Vista's but currently very much appletless (and basic looking as a result).
2. Floating panel that stays behind windows, thus a lot like a "normal" desklet.
3. My addition to the properties dialog. (Which turns out to be unnecessary to upload, since it is seen in image #2).

PS: Sorry, no downloads. I'm trying to collect some reasons to make this useful, make a few little cleanups as mentioned, then I intend to submit a patch. (Available in Gutsy+1, maybe, if a miracle happens?)

---

### Post by forrestcupp on 2007-08-09
I'm using Gutsy, and I don't have "Always Beneath" in my panel properties.  I wish I did.  Any ideas?

---

### Post by vexorian on 2007-08-10
vista's widgets are not an original idea anyways, in fact gnome did it first :) try looking for things like gDesklets or conky, etc . not my specialty since I don't use them...

anyways thanks, let me figure there are even more things possible to customize on the gconf-editor I think your changes are interesting.

> I'm using Gutsy, and I don't have "Always Beneath" in my panel properties. I wish I did. Any ideas?
He is actually modiffying some things.

--
edit: I finally finished downloading the screenshots, I think that's very cool if you only used the gnome panel! don't hesitate to make an alpha release, more people will test it and you'll get feedback that will help you get the cleaning and polishing you are looking to do.

---

### Post by UbuWu on 2007-08-10
Have a look at [Screenlets]("http://hendrik.kaju.pri.ee/screenlets/"), it is beautiful! :KS

---

### Post by arcx.rw on 2007-12-16
> **vexorian said:**
> 
He is actually modiffying some things.

If it is not a secret, whitch settings? :)
(the only thing I'd like to know, is how to keep those panels always beneath all other windows :) )

---

### Post by Mr. Picklesworth on 2007-12-16
Ah yes. Sorry I never followed up on this!

I have been sitting on the patch due to some bugs that still exist regarding positioning panels. I have an idea to fix it, finally. (What I must do is follow the life of a panel to figure out why the non-expanded panels cannot be moved past top-level panels, and set things up so that panels which are always beneath will *always* obey the struts set by other panels, be they new or old!)
My work always follows a rather meandering flight path; right now, I am working on a really cool application lister panel applet that has nothing to do with this whatsoever, but it should give me enough experience with panel applets to do desklet-like things fairly easily.

The change is, at its simplest, calling gtk_window_set_keep_below on a created panel. Using a gtk command is a bit sad, since they seem to have been avoided almost entirely here, but it was the only one I could get working at the time.
I also added some calls to gconf and a new entry in Preferences.
The real important detail is in setting Struts, which define the edges of the screen which a maximized window should not overlap. Useful when the window should be always on top, annoying and illogical when the window is meant to be always beneath others. Those struts be turned on and off, but problems come from interacting with other panels: A regular panel will overlap the always below one that didn't set struts!

Attached is a patch that (should hopefully) work on gnome-panel's source in Gutsy.
If you have any ideas for fixes, or know how to use a gdk command to get that panel window staying below, please post, because I am currently stumped.

---

### Post by Niklas Schröder on 2008-01-09
how do we apply the patch?  and what exactly does it change?

---

### Post by jayleesan on 2008-01-11
I am not a experienced linux-tweaker but I am trying to achieve the same effect. I dont like gDesklets, mainly because they are removed from the desktop when you press the "show desktop"-button. 

As you can see on the screenshot I attached, I used the gnome panel for a sidebar, ofcourse a graphical clock and a mini-calculator are still missing, but maybe it's not to much efford to post the tweak you applyed to put the panel in te background.

Nice work!

---

### Post by macogw on 2008-01-11
I used Screenlets and set them all as window type "Widget" and turn on the "Widget Layer" in Compiz when I used them.  Then it acts like the Dashboard on OSX.  I just don't use them really, so I stopped setting them to auto-run on startup.

---

### Post by cwgannon on 2008-02-23
Any progress on this?  Allowing other windows to overlap gnome-panel would be swell, most especially for those of us with limited screen real estate.

---

