---
title: "bug: wrong network interface monitored"
date: 2006-08-05
forum: Ubuntu System Panel
---

### Post by Poldi on 2006-08-05
USP seems to put eth0 in the menu no matter what. 

on my system eth0 is a _disabled_ ethernet card thats never used. eth1 is the active wireless lan that should be monitored.

I could not figure out how to change this in a graphical way myself.

suggestion: at least use the first _enabled_ ethX instead of the very first.

some minor suggestions:
- the 'find' functionlity is much more usefull for documents than for applications
- why are the application categories different from those in the Gnome (freedesktop.org) menu?
- 'System Management': I thing 'install software' as a management task is very different to 'lock screen' and 'Quit'. 
- I have no idea what the small button on top of the vertical settings, applications, places switches is meant to do. and no, I don't read any doc. because I try to simulate a typical user. the start menu is by definition the last thing I should need to read doc about.
- 'Computer' is used as a place, as a category and as an option in said category. smallest is the 'Computer' from places, which I use most often. biggest is the 'Computer' as the item that launches a system monitor. this is not a functionality used at all by lots of users.
- on my notebook there is no bborder around the window and is is ca. 16 pixel awqay from the menubar is is launched from. looks not very comforting... this is with Clearlook theme on a 1400x1050 display on an ATI Radeon Mobility 7500.
- tested version was 3.1

thanks for doing this. keep up your work.
kind regards,
Carsten

---

### Post by lazyd2 on 2006-08-05
Open gconf-editor, applications-->usp-->network interface and change it to ethx

---

### Post by _simon_ on 2006-08-05
> **Poldi said:**
> 

some minor suggestions:
- the 'find' functionlity is much more usefull for documents than for applications
[B][I]
You can have it filtered so that it does a normal gnome-search rather than an apps + file search.

Gconf -> apps -> usp -> do_not_filter[/I][/B]

- I have no idea what the small button on top of the vertical settings, applications, places switches is meant to do. and no, I don't read any doc. because I try to simulate a typical user. the start menu is by definition the last thing I should need to read doc about.

***It pins the menu in place so that you have to click the button again to close it.***

- 'Computer' is used as a place, as a category and as an option in said category. smallest is the 'Computer' from places, which I use most often. biggest is the 'Computer' as the item that launches a system monitor. this is not a functionality used at all by lots of users.

[B][I]You can change the size of the icons in "Places"

gconf -> apps -> usp -> place_icon_size[/I][/B]

- on my notebook there is no bborder around the window and is is ca. 16 pixel awqay from the menubar is is launched from. looks not very comforting... this is with Clearlook theme on a 1400x1050 display on an ATI Radeon Mobility 7500.
- tested version was 3.1

[B][I]To set your border 

gconf -> apps -> usp -> border_width[/I][/B]



See above responces for some of your points.

---

### Post by chanders on 2006-08-05
> **_simon_ said:**
> See above responces for some of your points.

Thank you _simon_! I think I should put a big disclaimer saying ALPHA software..

USP still has a LOT of work to be done and we are getting it done a little at a time (quite fast if you ask me ;))

@Poldi - Thanks for your suggestions. They will no doubt make it into subsequent revisions. Thanks again.

---

