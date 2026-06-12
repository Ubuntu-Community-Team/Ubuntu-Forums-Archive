---
title: "No previews in Nautilus/Files"
date: 2015-08-20
forum: Ubuntu Development Version
---

### Post by x-shaney-x on 2015-08-20
I have noticed for some time during testing that I don't get image previews in nautilus.
Is this actually a bug or new behaviour?

---

### Post by mc4man on 2015-08-20
This started a while ago, it's only a 'bug' in the sense that yet again gnome devs think that what they like is correct . So in addition to removing the preview they've left no user side option to restore.  (if this is what you're referring to??
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1426085](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1426085)

They also caused - '[ellipsed file names are not expanded on mouseover]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1448474")' for the few bothered about very long names going over the icon below, again no option to restore.
(- though this is easily brought back, I do so here via a patch I made - 

```
--- nautilus-3.14.2.orig/libnautilus-private/nautilus-canvas-item.c
+++ nautilus-3.14.2/libnautilus-private/nautilus-canvas-item.c
@@ -707,6 +707,7 @@ prepare_pango_layout_for_draw (NautilusC
 	needs_highlight = details->is_highlighted_for_selection || details->is_highlighted_for_drop;
 
 	if (needs_highlight ||
+           details->is_prelit ||
 	    details->is_highlighted_as_keyboard_focus ||
 	    details->entire_text) {
 		/* VOODOO-TODO, cf. compute_text_rectangle() */
@@ -1299,6 +1300,11 @@ nautilus_canvas_item_draw (EelCanvasItem
 
 #define ZERO_WIDTH_SPACE "\xE2\x80\x8B"
 
+#define ZERO_OR_THREE_DIGITS(p)			\
+	(!g_ascii_isdigit (*(p)) ||		\
+	 (g_ascii_isdigit (*(p+1)) &&		\
+	  g_ascii_isdigit (*(p+2))))
+
 
 static PangoLayout *
 create_label_layout (NautilusCanvasItem *item,
@@ -1327,9 +1333,11 @@ create_label_layout (NautilusCanvasItem
 		for (p = text; *p != '\0'; p++) {
 			str = g_string_append_c (str, *p);
 
-			if (*p == '_' || *p == '-' || (*p == '.' && !g_ascii_isdigit(*(p+1)))) {
+			if (*p == '_' || *p == '-' || (*p == '.' && ZERO_OR_THREE_DIGITS (p+1))) {
 				/* Ensure that we allow to break after '_' or '.' characters,
-				 * if they are not followed by a number */
+				 * if they are not likely to be part of a version information, to
+				 * not break wrapping of foobar-0.0.1.
+				 * Wrap before IPs and long numbers, though. */
 				str = g_string_append (str, ZERO_WIDTH_SPACE);
 			}
 		}
```

---

### Post by x-shaney-x on 2015-08-25
Wow!  I tend to just adapt to most changes and get on with it but since I work with graphics a lot there really is no point me testing any more.
Thanks for the info

---

### Post by qamelian on 2015-08-25
Just an FYI: I'm running a fully updated Wily with Nautilus 3.14.2-0ubuntu10 installed, and I'm not seeing this issue. I'm still getting thumbnails for all my images, etc.

---

### Post by x-shaney-x on 2015-08-25
@ [COLOR=#000000][FONT=Ubuntubeta]qamelian

That's odd. have you installed anything that might have enabled the thumbnails?
I have a pretty much default install and re-installed it all from a daily cd last week and fully up to date.[/FONT][/COLOR]

---

### Post by ventrical on 2015-08-25
Works fine here.

---

### Post by qamelian on 2015-08-25
I can't think of anything that I might have installed. I don't tend to install much on this box beyond ubuntu-restricted-extras, guake, mc, htop, and GIMP, for my day-to-day needs. 

> **x-shaney-x said:**
> @ [COLOR=#000000][FONT=Ubuntubeta]qamelian

That's odd. have you installed anything that might have enabled the thumbnails?
I have a pretty much default install and re-installed it all from a daily cd last week and fully up to date.[/FONT][/COLOR]

---

### Post by mc4man on 2015-08-25
What was removed in gnome was **text file** previews (as per bug report
Image files should get previews if - 
totem is installed or you install the ffmpegthumbnailer & switch nautilus to use it.

If totem is installed & still no thumbnails for images then remove ~/.cache/thumbnails folder
( some mimes require the gstreamer libav plugin installed for image previews

---

### Post by ventrical on 2015-08-26
> **mc4man said:**
> What was removed in gnome was **text file** previews...


Very slippery indeed.  All others are working. Text files are grabbing a generic blob. Interesting.

Regards..

---

