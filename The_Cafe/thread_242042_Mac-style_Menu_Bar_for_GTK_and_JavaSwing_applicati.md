---
title: "Mac-style Menu Bar for GTK and Java/Swing applications!"
date: 2006-08-23
forum: The Cafe
---

### Post by AqD on 2006-08-23
[COLOR="DimGray"]*re-post from arch linux forum, because there're more people ;) *[/COLOR]
-------------------------------------------------------------------
Hi all!

I hacked gtk2 to use mac-style menubars, [COLOR="Silver"]the pkgbuild is here => http://aur.archlinux.org/packages.php?do_Details=1&ID=6447[/COLOR], the patch is here => [gtkmenubar.diff](http://aur.archlinux.org/packages/gtk2-aqd/gtk2-aqd/gtkmenubar.diff)
**INSTALL**
0.Get gtk+ 2.10.2 (other versions may also work)
1.[color=brown]cd ....../gtk+-2.10.2/[/color]
2.[color=brown]patch -p0 < ...../gtkmenubar.diff[/color]
3.configure and make & install

It's tested working with compiz-quinn and blackbox, and tested apps including epiphany, nautilus, gimp, abiword, vmware, etc. SWT-based apps may have a few minor problem with compiz. Firefox/OpenOffice are not supported.

Screenshots:
[[img]http://static.flickr.com/97/220802752_834ce2f17a_m.jpg[/img]](http://static.flickr.com/97/220802752_834ce2f17a_o.png)  [[img]http://static.flickr.com/87/220842399_a0b0ccfa2d_m.jpg[/img]](http://static.flickr.com/87/220842399_a0b0ccfa2d_o.png)  [[img]http://static.flickr.com/66/220802753_5d912d3a16_m.jpg[/img]](http://static.flickr.com/66/220802753_5d912d3a16_o.png) 

Cheers!

PS: my modifed GT4_white theme => [http://aquila.deus.googlepages.com/GT4_white-aqd.tar.gz](http://aquila.deus.googlepages.com/GT4_white-aqd.tar.gz)

------------------------------------------------------------------
**Java/Swing mac menubar**
Similar to the GTK one, but the quality is not very good due to Swing's limitations.

[[img]http://static.flickr.com/59/222214833_5f81725552_m.jpg[/img]](http://static.flickr.com/59/222214833_5f81725552_o.png)  [[img]http://static.flickr.com/66/222214834_5c5275f4be_m.jpg[/img]](http://static.flickr.com/66/222214834_5c5275f4be_o.png)

**INSTALL:**
0.Need Java 1.5.0_07 (for other versions, use the patch)
1.Download my patched [JRootPane.java](http://aquila.deus.googlepages.com/JRootPane.java)
2.Create a dir [color=indigo]*some_dir/javax/swing*[/color] and move [color=indigo]*JRootPane.java*[/color] to there.
3.Chdir to [color=indigo]*some_dir*[/color] (NOT javax/swing)
4.Run [color=brown]javac javax/swing/JRootPane.java[/color]
5.Swich to root and make a backup of [color=indigo]*/opt/java/jre/lib/rt.jar*[/color]
6.Run [color=brown]zip -ur /opt/java/jre/lib/rt.jar javax -x "*.java"[/color]
7.Run [color=brown]java -Xshare:dump[/color] to re-generate shared cache.
8.Use MToolkit for AWT. Since compiz doesn't work with the new (and default) XToolkit in java 1.5, there is no need to support it. [color=brown]export AWT_TOOLKIT=MToolkit[/color]

The patch: [http://aquila.deus.googlepages.com/JRootPane.patch](http://aquila.deus.googlepages.com/JRootPane.patch)

Problems:
- Some menubar parts (not menu) may be not repainted well
- Mouse movement on menubar can't activate other menus, you have to click or use the old x-window/mac style (press button until you select the target item)
- When you move mouse pointer to menus, it's treated as the mouse has left menubar. No way to solve this, swing sucks...
- You can always move/resize the menubar by Alt+mouse buttons.....

-------------------------------------------------------------------
Original post => [http://bbs.archlinux.org/viewtopic.php?t=24289](http://bbs.archlinux.org/viewtopic.php?t=24289)
I also posted to the HOWTO forum, but it seems to be rejected....

---

### Post by slimdog360 on 2006-08-23
looks quite nice, Im going to have to give this a go when I get the time.

---

### Post by banjobacon on 2006-08-26
So, how ugly is the hack? Is there any chance of this ever being officially worked into GTK? Making this an option in Gnome, as it is in KDE, would be great.

---

### Post by dabear on 2006-08-26
Nice, but I would love having distrubutor logo to the left (with options to update, reboot, shudown the system) and deskbar to the right!

---

### Post by 4KvRMU7Nnv on 2007-01-10
can't figure out how to patch the GTK2 I'm a noob at that.  What is it exactly I have to do???  I think I have the applet, but all i see is the program running, no file, edit, options stuff.  Plz help.

---

### Post by mostwanted on 2007-01-10
> **d3br074 said:**
> can't figure out how to patch the GTK2 I'm a noob at that.  What is it exactly I have to do???  I think I have the applet, but all i see is the program running, no file, edit, options stuff.  Plz help.

You need to get the source code for a version of Gtk+ which is already outdated in Edgy and tinker with it so you probably don't want to do that yourself.

---

