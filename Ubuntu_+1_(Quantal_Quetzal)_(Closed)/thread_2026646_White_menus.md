---
title: "White menus"
date: 2012-07-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mcellius on 2012-07-15
Since I began testing QQ in Alpha 1, I've encountered an error in which some of the menus are displayed in white and are almost unreadable.  In particular, I've noticed these menus in the panel, in some of the indicators on the right side.  (Lately, this has happened in Nautilus, too.)

I've found a workaround that won't be useful to ordinary users, but which might help those working on bugs.

It's this: I downloaded and installed Ambiance-colors.  While using Ubuntu Tweak 0.73 (testing) I tried to apply the Ambiance-blue theme (I don't think it matters which Ambiance-colors theme is chosen).  It applies the window theme just fine, but not the Gtk theme: instead, it changes some of the text to be a difficult-to-read grey on white.  Ick!  So I changed it back using the reset button next to the theme, and NOW all of the other menus work correctly.

I don't know why this works, but I've been messing with it for several days and it is consistent.

---

### Post by effenberg0x0 on 2012-07-15
> **mcellius said:**
> Since I began testing QQ in Alpha 1, I've encountered an error in which some of the menus are displayed in white and are almost unreadable.  In particular, I've noticed these menus in the panel, in some of the indicators on the right side.  (Lately, this has happened in Nautilus, too.)

I've found a workaround that won't be useful to ordinary users, but which might help those working on bugs.

It's this: I downloaded and installed Ambiance-colors.  While using Ubuntu Tweak 0.73 (testing) I tried to apply the Ambiance-blue theme (I don't think it matters which Ambiance-colors theme is chosen).  It applies the window theme just fine, but not the Gtk theme: instead, it changes some of the text to be a difficult-to-read grey on white.  Ick!  So I changed it back using the reset button next to the theme, and NOW all of the other menus work correctly.

I don't know why this works, but I've been messing with it for several days and it is consistent.

I've been seeing the same thing. Here are some screenshots.

The volume and "envelope" menu are white:
[ATTACH]221318[/ATTACH]
[ATTACH]221319[/ATTACH]

Time/Date and cpu indicator are normal:
[ATTACH]221320[/ATTACH]
[ATTACH]221321[/ATTACH]

Regards,
Effenberg

**EDIT:** Indeed, Dash/Settings/Appearance, changing from Ambiance (Default) to Adwaita or anything else, and then back to to Ambiance fixes things (until the next session).

---

### Post by mc4man on 2012-07-15
I believe this is a known light-themes bug though haven't looked for.
Generally switching from & then back to Ambiance fixes

(those using the StanAngeloff light-theme mod wouldn't see this as some change he made in gtk-widgets.css keeps all the drop down menus dark

---

### Post by effenberg0x0 on 2012-07-15
> **mc4man said:**
> I believe this is a known light-themes bug though haven't looked for.
Generally switching from & then back to Ambiance fixes

(those using the StanAngeloff light-theme mod wouldn't see this as some change he made in gtk-widgets.css keeps all the drop down menus dark

mc4man, thanks for the tip on StanAngelOff! 
Maybe the menus discrepancy comes from GTK2/GTK3 theming sync/mess?

Regards,
Effenberg

---

### Post by mc4man on 2012-07-15
The modded theme restores the dark context menus for gtk3 & _Fixes_ the gtk2 menus which Ubuntu has shown [no interest in doing]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/961679")
(common gtk2 would be browsers, synaptic,  vlc, & surprisingly the context menu on window deco

The modded gtk-widgets.css, while still usable in 12.10 likely produces some xsession errors due to all values above 0 need to have px, like 1px vs. 1, ect.

=======================================================
Atm I'm using the git nautilus to see what's coming. It would appear light-themes (ambiance) would need some work so maybe when ?? the newer nautilus lands some light-theme work will start up again

The new nautilus with no ubuntu patches has an awful look with ambiance so I've adjusted it here to tone down a bit, more of a combo of ambiance & radiance 
(- did this only for nautilus, put the back, forward buttons in separate gtk boxes, narrowed the toolbar itself, created a new color-define and atm applied to sidebar & toolbar, looking at diff colors for that though hard to see 'right' on small laptop

---

### Post by philinux on 2012-07-16
Indeed changing themes fixes it in session.

The [https://github.com/StanAngeloff/AmbianceOneiric]("https://github.com/StanAngeloff/AmbianceOneiric") solution doesn't work in QQ.

---

### Post by mc4man on 2012-07-16
> **philinux said:**
> Indeed changing themes fixes it in session.

The [https://github.com/StanAngeloff/AmbianceOneiric]("https://github.com/StanAngeloff/AmbianceOneiric") solution doesn't work in QQ.
Probably not - it does here because every time L-T's updated I applied the commits manually to my existing Ambiance files
As it currently stands I'm only keeping the gtk3 fixes to eliminate the need to switch every session though do plan to keep gtk2 (gtkrc) fixes unless the 12.10 L-T fixes that

(i figure in a couple of weeks or so things should become more apparent as far as nautilus

---

### Post by philinux on 2012-07-16
> **mc4man said:**
> Probably not - it does here because every time L-T's updated I applied the commits manually to my existing Ambiance files
As it currently stands I'm only keeping the gtk3 fixes to eliminate the need to switch every session though do plan to keep gtk2 (gtkrc) fixes unless the 12.10 L-T fixes that

(i figure in a couple of weeks or so things should become more apparent as far as nautilus

I think I'll leave my install as default. I usually do this to check that bugs do actually get fixed. I'm none to keen on workarounds in testing.

Regards.

---

### Post by mcellius on 2012-08-09
I don't know which update did it, but as of today the problem appears to be fixed.  Without having to change themes, all of the indicator menus now look correct.

---

### Post by GreatDanton on 2012-08-09
> I don't know  which update did it, but as of today the problem appears to be fixed.   Without having to change themes, all of the indicator menus now look  correct. 			 		   		 		 		


True same here.

---

### Post by kuvanito on 2012-08-10
amen
all fixed up!

---

