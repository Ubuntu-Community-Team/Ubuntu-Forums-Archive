---
title: "Don't gedit in ubuntu session"
date: 2015-11-20
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-11-20
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1515461](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1515461) fixed
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1515810](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1515810)
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1518516](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1518516)
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1518517](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1518517) fixed

---

### Post by P-I H on 2015-11-21
[https://bugs.launchpad.net/ubuntu/+s...t/+bug/1515461]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1515461")
This bug seems to be theme related. It works OK with the Adwaita theme.

[https://bugs.launchpad.net/ubuntu/+s...t/+bug/1515810]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/1515810")
Effects other programs like [https://wiki.gnome.org/Apps/Weather](https://wiki.gnome.org/Apps/Weather)

Marked
[COLOR=#484848][FONT=Ubuntu]**"Yes, it affects me"**[/FONT][/COLOR]
to the bugs.

---

### Post by ventrical on 2015-11-21
Also has tabby relics or virtual paper cuts on top left and right corners :) lol

---

### Post by grahammechanical on 2015-11-21
That is the Ambiance theme. With the Radiance theme Gedit has sharp right angle corners at top left & right. It still looks out of place with the rounded corners used else where.

---

### Post by fthx on 2015-11-22
I use Ubuntu Gnome.
I think it's since gtk 3.18.5 that I've got some issues with Adwaita (Gnome's default) : large grey border instead of shadowed border.
The other issue is with Ambiance, but this one stands since an-old-age : sharp right&left top corners whitened.

---

### Post by harry332 on 2015-11-22
Exactly this fthx.
The issue is not to try to repair gedit 3.18.2.
It is GTK+3 3.18.5 or newer (like 3.19.2) that is broken somehow.
Downgrading back to GTK+3 3.18.4 solves the issues with gedit, eog and nautilus (3.18.2).

---

### Post by sgage on 2015-11-22
> **fthx said:**
> I use Ubuntu Gnome.
I think it's since gtk 3.18.5 that I've got some issues with Adwaita (Gnome's default) : large grey border instead of shadowed border.
The other issue is with Ambiance, but this one stands since an-old-age : sharp right&left top corners whitened.

I'm seeing the same large grey border in Gnome apps. Has this been reported? I'd like to 'me too' it.

---

### Post by sammiev on 2015-11-22
Guess I must be missing something.

---

### Post by PaulW2U on 2015-11-22
> **sgage said:**
> I'm seeing the same large grey border in Gnome apps. Has this been reported? I'd like to 'me too' it.
Is this the bug report we're looking for?

[https://bugs.launchpad.net/bugs/1518661](https://bugs.launchpad.net/bugs/1518661)

I'm seeing the unwanted border problem here too in Ubuntu GNOME.

---

### Post by sgage on 2015-11-22
> **PaulW2U said:**
> Is this the bug report we're looking for?

[https://bugs.launchpad.net/bugs/1518661](https://bugs.launchpad.net/bugs/1518661)

I'm seeing the unwanted border problem here too in Ubuntu GNOME.

Yes, that looks like it! Thanks for letting me/us know. I seem to have the worst luck searching for bugs. I never would have found this one! :KS  I will 'me-too' it immediately...

---

### Post by tista on 2015-11-22
@PaulW2U,

Please let me be clear,
> [https://bugs.launchpad.net/bugs/1518661](https://bugs.launchpad.net/bugs/1518661)

I'm seeing the unwanted border problem here too in Ubuntu GNOME.
This happened in Gome-Shell with Adwaita, too?
Anyway this might be caused new ubuntu specific patch what unveiled from 3.18.5-1ubuntu1 package:
```
diff --git a/gtk/gtkwindow.c b/gtk/gtkwindow.c
index 2d9f4b5..0476b6b 100644
--- a/gtk/gtkwindow.c
+++ b/gtk/gtkwindow.c
@@ -7122,6 +7122,11 @@ gtk_window_realize (GtkWidget *widget)
   gtk_widget_register_window (widget, gdk_window);
   gtk_widget_set_realized (widget, TRUE);
 
+  G_GNUC_BEGIN_IGNORE_DEPRECATIONS
+  if (!gtk_widget_get_app_paintable (widget))
+    gtk_style_context_set_background (gtk_widget_get_style_context (widget), gdk_window);
+  G_GNUC_END_IGNORE_DEPRECATIONS
+
   attributes.x = allocation.x;
   attributes.y = allocation.y;
   attributes.width = allocation.width;
-- 
2.6.2
```
This patch seems very dangerous... :(

I'm now building Gtk+ 3.19.2 with the patch and soon I'm going to test it on metacity 3.18.1.
And that patch could solve black flickering on opening windows on Compiz really?

Regards.
Tista

**EDIT #1**
OK. I could confirm that patch broke Mutter's window decorations by drawing solid background in shadow areas... :(
This patch (0001-gtkwindow-continue-calling-gtk_style_context_set_bac.patch) should be removed ASAP since the downside effects was too heavy and critical.
I can not understand why the contributors did not review this patch on Mutter...

**EDIT #2**
It affects to Metacity's window decorations, too.
Seems the worst patchworks in Gtk+ ever...

---

### Post by mc4man on 2015-11-22
> **tista said:**
> 
OK. I could confirm that patch broke Mutter's window decorations by drawing solid background in shadow areas... :(
This patch (0001-gtkwindow-continue-calling-gtk_style_context_set_bac.patch) should be removed ASAP since the downside effects was too heavy and critical.
I can not understand why the contributors did not review this patch on Mutter...
Maybe they'll revert or fix if reported.
It does seem that at default what works for gnome sessions doesn't in some cases work for an ubuntu session & vice-versa 

In those cases it seems patches that benefit an ubuntu session are needed & should be Ubuntu's first focus. Their effect in a gnome session shouldn't (obviously won't) be ignored, though I wouldn't consider any failings there to be a deal breaker to making an ubuntu session better or correct.
Nautilus 3.18+ will by default not be right in an ubuntu session so here is hoping, unlike gedit,  they fix it before committing to.
Edit: or if resources better spent elsewhere then leave nautilus as is till 16.10 or whatever.

---

### Post by sgage on 2015-11-22
Yes, the big gray border thing occurs in Gnome Shell with Adwaita. This is Ubuntu Gnome 16.04, without proposed enabled or any ppa's or such...

---

### Post by flocculant on 2015-11-23
just fyi - it's all fubar in xubuntu too 

pointed this out to people in -desktop this morning using that newest bug

---

### Post by PaulW2U on 2015-11-23
> **tista said:**
> This happened in Gome-Shell with Adwaita, too?
Yes.
> **sgage said:**
> This is Ubuntu Gnome 16.04, without proposed enabled or any ppa's or such...
Same here. I don't mind testing and reporting/confirming bugs when I find them but I won't make my test laptop any more unstable than I need to. :D

---

### Post by fthx on 2015-11-24
Gedit has been patched today.

---

### Post by tista on 2015-11-24
Greetings,

Today Matthias Clasen, the lead Gtk+ developer, confirmed that issue (drawn solid background & thick border around the windows) as 'downstream issue'.
So he changed bug status on Gnome bugzilla to 'resolved, notGnome'.

And Tim Lunn, Ubuntu GNOME maintainer, released "dispatched" Gtk+ 3.18.5 packages on Gnome3-staging-PPA:
[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging/+packages?field.name_filter=&field.status_filter=published&field.series_filter=xenial]("https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging/+packages?field.name_filter=&field.status_filter=published&field.series_filter=xenial")

If you guys want to check the dispatched state, it would be easy and safe by downloading some deb packages from ppa showed above and install them via dpkg-ing.

Best Regards.
Tista

---

### Post by PaulW2U on 2015-11-24
> **tista said:**
> If you guys want to check the dispatched state, it would be easy and safe by downloading some deb packages from ppa showed above and install them via dpkg-ing.
Thanks tista. Works for me. :D

---

### Post by sgage on 2015-11-24
> **PaulW2U said:**
> Thanks tista. Works for me. :D

Me too :KS

---

