---
title: "Gnome Shell done in Javascript"
date: 2009-03-28
forum: The Cafe
---

### Post by BGFG on 2009-03-28
If i understand correctly, the Gnome3.0 shell is being done in javascript. If this is the case, why has there not been more discussion in the forums ?
Also, from the FUDCON videos, it would seems that gnome is aggressively moving away from dependence on other FOSS projects: X, Compiz....

What do you think ?

FUDCON vids:

[http://alt.fedoraproject.org/pub/alt/videos/2009/FUDConF11/fudcon-f11-rm345-session4.ogg](http://alt.fedoraproject.org/pub/alt/videos/2009/FUDConF11/fudcon-f11-rm345-session4.ogg)

---

### Post by swoll1980 on 2009-03-28
> **BGFG said:**
> If i understand correctly, the Gnome3.0 shell is being done in javascript. If this is the case, why has there not been more discussion in the forums ?
Also, from the FUDCON videos, it would seems that gnome is aggressively moving away from dependence on other FOSS projects: X, Compiz....

What do you think ?

FUDCON vids:

[http://alt.fedoraproject.org/pub/alt/videos/2009/FUDConF11/fudcon-f11-rm345-session4.ogg](http://alt.fedoraproject.org/pub/alt/videos/2009/FUDConF11/fudcon-f11-rm345-session4.ogg)

From what I read [here]("arstechnica.com/open-source/news/2008/07/gnome-3-0-officially-announced-and-explained.ars") it will be nothing that dramatic.

---

### Post by klange on 2009-03-28
> **BGFG said:**
> Also, from the FUDCON videos, it would seems that gnome is aggressively moving away from dependence on other FOSS projects: X, Compiz....

Gnome has never had any dependence on Compiz. Ever. And until Gnome starts putting out framebuffer-capable GTK, it's always going to be very dependent on X.

---

### Post by BGFG on 2009-03-28
> **klange said:**
> Gnome has never had any dependence on Compiz. Ever. And until Gnome starts putting out framebuffer-capable GTK, it's always going to be very dependent on X.

In the case of compiz i should have worded it differently. Compatibility then. With Clutter, will there be a need for compiz in the gnome desktop? Also, another new feature was mentioned and demonstrated, (I forget the name) that could conceivably replace the X server in future...

I find it all exciting.

@Swoll1980, that link is kinda old, check the vids some newer stuff is mentioned and demonstrated

---

### Post by fissionmailed on 2009-03-29
So gnome is using enterprise code, interesting.

---

### Post by gnomeuser on 2009-03-29
> **BGFG said:**
> In the case of compiz i should have worded it differently. Compatibility then. With Clutter, will there be a need for compiz in the gnome desktop? Also, another new feature was mentioned and demonstrated, (I forget the name) that could conceivably replace the X server in future...

I find it all exciting.

@Swoll1980, that link is kinda old, check the vids some newer stuff is mentioned and demonstrated

Wayland is also not a move away from X, consider it X updated to take full advantage of the improvements we have gotten in recent history such as KMS and DRI2. You can run X under Wayland (which is actually demoed in the video). Wayland is a long way off though.

As for Mutter (Metacity + Clutter) it completely replaces Compiz, it does everything Compiz does or at least it is capable of doing so. Currently it doesn't match it feature for feature, it's also not likely to do so. There is a debate on the GNOME Desktop-devel-list right now as to how closely to tie Mutter to the gnome-shell, there are advantages to an approach where the two are closely tied and very few downsides really. I would encourage going to mail.gnome.org and following the relevant thread.

Now personally I really want the future of GNOME to be a switch to using Silverlight and C#, JavaScript always irked me a lot but I can see the appeal of using a language which is as popular as JavaScript is, it would open GNOME to a large existing base of poor programmers. Maybe we will see some interesting features spring from this, hopefully. Remembering though that the backend is still in C and the bindings to JS (and others) will be done using introspection, so you really get the worse of all worlds (then again, I want my kernel written in C# so my tolerance level for non-managed code is rather low).

---

