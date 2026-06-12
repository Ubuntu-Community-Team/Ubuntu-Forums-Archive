---
title: "metacity theme not getting used in gnome fallback"
date: 2014-05-03
forum: System76 Support
---

### Post by system76panp9 on 2014-05-03
I posted a while back about how I suddenly was unable to log in to unity and even when I ran gnome fallback instead, I had frequent window manager crashes which left my windows undecorated. I was very grateful to get several helpful responses and after running the command "dconf reset -f /org/compiz" as someone suggested, my system is pretty stable under gnome fallback, which I have kept using since it seems to better meet my needs than the unity desktop environment. I just am having the one problem which I also alluded to before, namely: whatever metacity theme I specify in my index.theme file, the window manager does not draw it, and instead gives me what according to the compiz wiki is the default cairo window decoration. I believe that compiz is managing the windows, since I am selecting gnome fallback and not the variant with "No Effects", which I guess sets metacity itself as the manager. I compared all my dconf settings to what I had archived prior to this happening, and they are identical except that the compiz "profile" is now "Default" instead of "unity", but in particular the boolean setting in dconf which asks whether to use the metacity theme still has the value true. I would be very appreciative if anyone has any ideas about how I could diagnose what is going on and maybe figure out where the decision is being taken to not load the metacity xml file in lieu of the cairo title bar and buttons etc. I should point out that I was able to get my chosen theme "Crux" to work under gnome fallback at first, but it suddenly stopped working for no apparent reason. I have Ubuntu 13.04 on my panp9 laptop. Thanks for any assistance

---

