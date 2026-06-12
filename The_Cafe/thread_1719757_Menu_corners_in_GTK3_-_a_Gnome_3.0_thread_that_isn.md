---
title: "Menu corners in GTK3 - a Gnome 3.0 thread that isn't about Shell"
date: 2011-04-02
forum: The Cafe
---

### Post by Copper Bezel on 2011-04-02
Hello all.

This is a bit random and, I guess, not much of a conversation-starter, but I have a question about Gnome 3 for those who are using it and know a bit about the mechanics. I know that the theming is now based on CSS, which will massively simplify theming, and I know that regardless of the shell (Classic, Shell, Unity, or a-la-carte implementations of third-party panels like Elementary's Docky and eventually Wingpanel) or window manager (Mutter or Compiz) used, future Gnome distros will be able to take advantage of the new features of GTK 3.0. That bit I get. 

Here's where I'm curious: does GTK 3.0 finally support rounded corners for menus and tooltips? For all the talk about Shell and running apps through a browser and so on, this is the one thing I'd have actually expected to see in the next major revision of GTK. KDE has had rounded menus for some time now, and they've been just over the horizon in Gnome for years (even appeared in a mockup for Ubuntu Hardy along with RGBA support.) Will they finally be possible in GTK3?

That's all.

---

### Post by Merk42 on 2011-04-02
Given all the rounded corners in [these images](http://ubuntuforums.org/showthread.php?t=1603874), I'd say yes

---

### Post by Copper Bezel on 2011-04-02
Sweet. = ) I'm officially excited about Gnome 3 now.

---

### Post by zekopeko on 2011-04-02
> **Merk42 said:**
> Given all the rounded corners in [these images](http://ubuntuforums.org/showthread.php?t=1603874), I'd say yes

Those "menu" aren't drawn with GTK+ but with Clutter.

@Copper Bezel: I know that round tooltips appeared in Lucid or thereabout. 

I've also seen round menu corners in GTK+ apps here: [http://lucidfox.org/p/2010/08/19/and_stay_out](http://lucidfox.org/p/2010/08/19/and_stay_out)

---

### Post by Copper Bezel on 2011-04-02
> Those "menu" aren't drawn with GTK+ but with Clutter.

Well, I'm dumb. I don't use the user menu, so I didn't recognize that one. My calendar looks exactly the same as the one in Shell right now (because AWN uses a similar overlay). And yes, not only are rounded tooltips supported, but I already have them. I promise that there was a reason for my confusion and that I wasn't drunk-posting.

The link you provided links to a theme that doesn't exist, but apparently [it's possible in the Murrine engines if RGBA is enabled]("http://gnome-look.org/content/preview.php?preview=2&id=100556&file1=100556-1.jpg&file2=100556-2.jpg&file3=&name=RGBA+Gtk%2B+module"). Thanks!

Edit: So those two elements of the Hardy mockup I mentioned were more closely linked than I thought. In any case, what I'm seeing on this issue from every time it's been proposed is that to do this properly, rather than hacking with the theme, it supposedly "would require a complete rewrite of the GTK+ libraries", which is going on *now*. I do hope the Gnome devs made themselves a sticky note for this.

In the short term, though, I'm presented with the thrilling possibility of getting them *now* with some tweaks to my gtkrc. = )

---

### Post by murderslastcrow on 2011-04-06
You do realize that the Oxygen-GTK guys have already found a way around this, right? Even with a GTK 2 theme, although they're in the process of porting the theme to GTK 3 to support animation (the fading glows/menu items and stuff), among other things.

I don't see why it hasn't been done a million times before. It's one of the main reasons I feel sick using Gnome- every theme that looks nice has those blocky rectangular menus that screw up the mood entirely. Also, it'd be nice to grab the background in any GTK theme, not just Oxygen-gtk.

Hopefully there will be derivatives or something similar from the core Gnome team soon. I really hate feeling like we're living in the 90s even with Gnome 3 having come out today. OS X had these since 2005 or so. We've had them since 2008 on KDE. It should be a standard capability, and used when appropriate.

P.S. Apparently you don't need compositing with Oxygen-gtk to have the rounded corners, either. So either RGBA has nothing to do with compositing, or they've used something clever to enable this feature. I suggest looking it up.

---

### Post by Copper Bezel on 2011-04-07
I'm not really concerned with what is and isn't possible in KDE. I already said it's terribly embarrassing if GTK3 doesn't have the capability.

---

### Post by murderslastcrow on 2011-04-07
Whoah whoah now, Oxygen-gtk doesn't use anything from KDE aside from the color settings. It's very much an independent gnome theme- it doesn't use Qt to run or display its menus.

What I'm saying is that we should look into how they did it, since it's using pure GTK and can produce the menus even in applications where RGBA is blacklisted (albeit a bit rougher than those that do support RGBA). Even if Murrine can hypothetically do it, no one's really trying, and Oxygen-gtk already has it, so it may be a good place to start.

I hope that it's okay for KDE folks to keep making integrated themes for Gnome, like QGtkStyle and Oxygen-Gtk, both for themselves and for Gnome users. :| I find it odd how little cooperation there is on user-facing issues like this, even when people are throwing hours into projects like this.

Soon we'll all have pretty borders and antialiasing on everything, where available. I hope Gnome 3's theme comes with antialiased corners and round menus some time in the near future- I think it's inevitable. And these KDE guys like Hugo have proven that even on Gnome 2 it's totally possible.

---

