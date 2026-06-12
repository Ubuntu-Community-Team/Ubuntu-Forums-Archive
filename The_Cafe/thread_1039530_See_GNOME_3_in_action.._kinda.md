---
title: "See GNOME 3 in action.. kinda"
date: 2009-01-14
forum: The Cafe
---

### Post by gnomeuser on 2009-01-14
Fedora recently held their developers conference (FUDcon) and now the videos from it have hit the web. One of them, the desktop session, contains a demo of the new GNOME Shell which is being proposed for GNOME 3.

Videos here:
[https://fedoraproject.org/wiki/FUDCon:FUDConF11_BarCamp_schedule](https://fedoraproject.org/wiki/FUDCon:FUDConF11_BarCamp_schedule)

More information:
[http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)

---

### Post by BGFG on 2009-01-14
Seems unnecessaraily large. Reminds me of Vista for some reason. I'm a GNOME man anyway so come what may i'll be using it when it's hooked into Ubuntu.

I like the Gnome menu now. It's what made me immediately love Ubuntu. Applictions:Places:System. It just seemed logical, and was what i was always looking for in a menu.

Thanks for the link.

That should not be a smiley. It should be a colon then the beginning of Places...

---

### Post by gnomeuser on 2009-01-14
> **BGFG said:**
> Seems unnecessaraily large. Reminds me of Vista for some reason. I'm a GNOME man anyway so come what may i'll be using it when it's hooked into Ubuntu.

I like the Gnome menu now. It's what made me immediately love Ubuntu. Applictions:Places:System. It just seemed logical, and was what i was always looking for in a menu.

Thanks for the link.

That should not be a smiley. It should be a colon then the beginning of Places...

Measured in pixels this has more screen space available to applications, you would only pop down the activity menu if you wanted to do something like search, start a new application, add a workspace e.g.. 99% of the time it would be just the top bar and then your work.

---

### Post by BGFG on 2009-01-14
> **gnomeuser said:**
> Measured in pixels this has more screen space available to applications, you would only pop down the activity menu if you wanted to do something like search, start a new application, add a workspace e.g.. 99% of the time it would be just the top bar and then your work.

Sensible. I suppose things such as size would be configurable anyway. I look forward to it. Any word on resources and whether or not they hope to make it 'lighter' ?

---

### Post by gnomeuser on 2009-01-14
> **BGFG said:**
> Sensible. I suppose things such as size would be configurable anyway. I look forward to it. Any word on resources and whether or not they hope to make it 'lighter' ?

Well.. the only things I really know is that this depends on javascript, clutter and something called mutter which is metacity ported to clutter (for the effects). This will depend on having hardware accelerated graphics AFAIK but this with nouveau coming along and ATI providing us code and specs is becoming a manageable problem space in the GNOME 2.28 and 3.0 time frame.

I can't give you a best guess, I just don't know but I promise the second this becomes stable enough for me to even try I will get you numbers. The developers currently advice against running it as it's "kinda crashy"

---

### Post by Kernel Sanders on 2009-01-14
> **gnomeuser said:**
> (FUDcon)

:lol:

---

### Post by BGFG on 2009-01-14
> **gnomeuser said:**
> Well.. the only things I really know is that this depends on javascript, clutter and something called mutter which is metacity ported to clutter (for the effects). This will depend on having hardware accelerated graphics AFAIK but this with nouveau coming along and ATI providing us code and specs is becoming a manageable problem space in the GNOME 2.28 and 3.0 time frame.

I can't give you a best guess, I just don't know but I promise the second this becomes stable enough for me to even try I will get you numbers. The developers currently advice against running it as it's "kinda crashy"

Thanks, the whole ATI opensource thing is still hard to believe though. As for metacity, I hope they also improve it's compositing ability along with including it in the desktop. Would that then do away with the necessity for compiz, or rather just make it optional ?

---

### Post by gnomeuser on 2009-01-14
> **BGFG said:**
> Thanks, the whole ATI opensource thing is still hard to believe though. As for metacity, I hope they also improve it's compositing ability along with including it in the desktop. Would that then do away with the necessity for compiz, or rather just make it optional ?

Mutter is a clutter port with compositing, I also hear there is a plan to do some work with the new Wayland thingy. I assume this means Compiz is not a favored solution. 

but looking at the demo this does some very neat effects and there is no reason why one couldn't leverage clutter to make more "blingy" stuff, at least as I understand it.

---

### Post by BGFG on 2009-01-14
The more i use linux the less interested i am in eyecandy. All i need is a transparent panel, a cool background and 2 mins in 'appearance' gives me the colour scheme i want.
I've tried AWN and Cairo-dock and found them useless or unnecessary rather. Gnome-panel meets all my needs. I think compositing and minimal effects built into the Gnome environment with effecient code would be desirable.

---

### Post by cardinals_fan on 2009-01-14
> **BGFG said:**
> The more i use linux the less interested i am in eyecandy. All i need is a transparent panel, a cool background and 2 mins in 'appearance' gives me the colour scheme i want.

I have no panels, and now that I've switched to ratpoison I also have no wallpaper.  I just need a nice console font :D

---

### Post by BGFG on 2009-01-14
:) i enjoy tweaking around in appearances and creating custom themes. Got some rich browns and dark greys going on.... I installed emerald, but the glow was annoying.
I don't think i'll move away from wallpaper though, even with openbox, i still like a warm desktop.

Really looking forward to hopefully some new innovations in gnome 3 though. I'd like to see more 'right click' functionality, and much tighter integration with gnome apps.

Eg. right click and check properties of a menu item having it display the executable file. Also right click and 'scan file' in the case of ClamTK, i think it's possible to set up, but like i said, tighter integration would be appreciated.

---

### Post by CarpKing on 2009-01-14
I hope mutter allows for antialiased window borders.  That's really my main complaint about Metacity's current compositor.  I'd also like to see some sane but pleasant animations; they don't even need to be configurable if they make sense to begin with.  As a lower priority, it would be nice to cherry-pick the more useful parts of Compiz and add them to Metacity/whatever part of Gnome they actually go with.  

A few off the top of my head:
-Arbitrary keyboard shortcuts
-Visual indication of workspace switch
-Visual indication of unresponsive windows
-Window scaling
-Maximumize
-Probably some of the window rules stuff?
-The Super+mouse-click-&-drag screenshot functionality is pretty slick, but maybe it's not discoverable enough for Gnome

Anyway, I look forward to seeing where the future of Gnome takes us.

---

### Post by Zlatan on 2009-01-15
> **BGFG said:**
> The more i use linux the less interested i am in eyecandy. All i need is a transparent panel, a cool background and 2 mins in 'appearance' gives me the colour scheme i want.
I've tried AWN and Cairo-dock and found them useless or unnecessary rather. Gnome-panel meets all my needs. I think compositing and minimal effects built into the Gnome environment with effecient code would be desirable.

+1
gnome native and very effective effects:)

---

### Post by gnomeuser on 2009-01-15
> **Zlatan said:**
> +1
gnome native and very effective effects:)

From what can be seen in the current demonstration, the effects are mainly enhancing the experience. No wobbly windows or spinning cubes, rather workplaces sliding into place, visual indication for creating a new workspace and so forth. I would use the term elegant about the current state.

I am though sure someone will extend the possibilities to total crack levels at some point, and that will appeal to a number of people. The defaults look tasteful though, a little glitter here and there.

---

