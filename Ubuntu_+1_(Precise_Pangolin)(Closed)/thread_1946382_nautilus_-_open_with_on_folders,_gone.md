---
title: "nautilus - open with on folders, gone"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-03-24
Certainly not surprising in the current climate & not really a big deal.
Though for some users, multimedia wise in particular, it was handy.

For those missing it can be easily be restored in a self build, either by manully editing or by means of a small patch
(have 3 current patches of use here
toolbar.patch - moves navigation arrows to left side, adds parent(up) arrow
undo.patch - returns Bookmarks to appmenu on Desktop focus
open_with.patch - returns open with on folders

The change back is quite simple (ATM)

```
--- nautilus-3.3.92.orig/src/nautilus-view.c
+++ nautilus-3.3.92/src/nautilus-view.c
@@ -4491,8 +4491,9 @@ reset_open_with_menu (NautilusView *view
 
 		file = NAUTILUS_FILE (node->data);
 
-		other_applications_visible &= (!nautilus_mime_file_opens_in_view (file) &&
-					       !nautilus_file_is_nautilus_link (file));
+		other_applications_visible &=
+			(!nautilus_mime_file_opens_in_view (file) ||
+			 nautilus_file_is_directory (file));
 	}
```

Edit: this change was apparently part of a commit to allow access in nautilus to non-desktop desktop files, ex. "index.theme"

At least here see no side affect of restoring the open with on directories & keeping the ability to see & open .theme files
Then again maybe nautilus dev's know best, myself will keep both

---

### Post by mc4man on 2012-03-25
Whole deal seems curious so
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/964186](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/964186)

To put some perspective?, the bug fixed, 'how nautilus displays/act on files like .theme', was 6+ years old.
[https://bugzilla.gnome.org/show_bug.cgi?id=319981](https://bugzilla.gnome.org/show_bug.cgi?id=319981)

---

### Post by VMC on 2012-03-25
I wondered what happened. I thought it would eventually it put back. Now I know. Thanks also for the patch!

Thanks for the bug report. I "affects me too" on your bug.

---

### Post by mc4man on 2012-03-25
I think this is Gnome's idea of 'a little give & take'

---

### Post by ranch hand on 2012-03-25
Slapped a me to on there myself.

Don't have a buntu that runs Nautilus but I do have Gnome3 with Gnome Shell on a Sid install.  Also have Xfce4.8 on that.

Never would have thought as little as a year ago that I would see the day that running Gnome I would be really really relieved to have the option to open something with Thunar.  Sure am now.

The kind of thing you did in the Nautilus config file can easily be done in Thunar with Edit>Configure Custom Actions.  Of coarse for things like media opening you don't need it as Thunar devs don't have the good sense to take it out in the first place.  Troglodytes.

I like Troglodyte devs.

---

### Post by mc4man on 2012-03-25
Speaking of file managers, -  that's another use of the 'open with' on directories.
Obviously one could open an alt. fm & then do whatever, but there's no reason not to be able to do from the context menu

For instance was checking out [this dual pane fm,]("http://code.google.com/p/sunflower-fm/") don't intend to use as default but it has some interest so I'll keep around

Filed upstream also, always curious to hear a response, (- if there is one & if so  hopefully before 2018
[https://bugzilla.gnome.org/show_bug.cgi?id=672809](https://bugzilla.gnome.org/show_bug.cgi?id=672809)

---

### Post by mc4man on 2012-03-26
fixed upstream (reverted the offending section), so should be restored with next nautilus update

---

### Post by VMC on 2012-03-26
> **mc4man said:**
> fixed upstream (reverted the offending section), so should be restored with next nautilus update

Great news. I use that feature a lot with VLC among others. I also had trouble with the patch.

---

### Post by mc4man on 2012-03-26
> **VMC said:**
> Great news. I use that feature a lot with VLC among others. I also had trouble with the patch.

A patch like I posted would be used in /debian/patches, if you tried by using a patch command it wouldn't know where the file is due to  - 
"--- [COLOR="Blue"]nautilus-3.3.92.orig[/COLOR]/src/nautilus-view.c"
"+++ [COLOR="Blue"]nautilus-3.3.92/[/COLOR]src/nautilus-view.c

(posted more as a guide as to how it was before, though here add patches as such to /debian/folders & apply before build with dpkg --commit

When I copied into post inadvertently left 1 final line out, wouldn't matter, that's the 'fuzz'

So if you tried to manually patch you'd see something like this, can be solved as shown by giving just the source path

> ~/Desktop/naut4/nautilus-3.3.92$ patch -p0 < ../open_with.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- nautilus-3.3.92.orig/src/nautilus-view.c
|+++ nautilus-3.3.92/src/nautilus-view.c
--------------------------
File to patch: src/nautilus-view.c
patching file src/nautilus-view.c
Hunk #1 succeeded at 4491 with fuzz 1.

or in such cases edit a patch to remove so like this in this instance

```
--- src/nautilus-view.c
+++ src/nautilus-view.c
@@ -4491,8 +4491,9 @@ reset_open_with_menu (NautilusView *view
 
 		file = NAUTILUS_FILE (node->data);
 
-		other_applications_visible &= (!nautilus_mime_file_opens_in_view (file) &&
-					       !nautilus_file_is_nautilus_link (file));
+		other_applications_visible &=
+			(!nautilus_mime_file_opens_in_view (file) ||
+			 nautilus_file_is_directory (file));
 	}

```

(what i left out at the end was 
<empty line>
default_app = NULL;

Anyway here's the revert almost the same as what was there before, he added a little bit - 

```
--- a/src/nautilus-view.c
+++ b/src/nautilus-view.c
@@ -4491,8 +4491,9 @@ reset_open_with_menu (NautilusView *view, GList *selection)
 
 		file = NAUTILUS_FILE (node->data);
 
-		other_applications_visible &= (!nautilus_mime_file_opens_in_view (file) &&
-					       !nautilus_file_is_nautilus_link (file));
+		other_applications_visible &= ((!nautilus_mime_file_opens_in_view (file) &&
+						!nautilus_file_is_nautilus_link (file)) ||
+					       nautilus_file_is_directory (file));
 	}
 
 	default_app = NULL;
```

In any event should show up in near future

---

