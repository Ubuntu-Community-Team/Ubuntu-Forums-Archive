---
title: "ies4linux: Can't install with Flash, trouble without"
date: 2009-06-22
forum: Wine
---

### Post by Jesdisciple on 2009-06-22
I initially tried to install all four versions (7, 6, 5.5, 5) of IE, but GTK errors came up which seem dependent on the combination of IE v<6 and Flash.  After much experimenting, I discovered that unchecking the Flash option allowed all four to be installed.  I just wonder what's necessary to get Flash to work (on Wine 1.1.24~winehq0~ubuntu~9.04-0ubuntu1).  Note that this isn't for normal browsing at all.

```
$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

/home/coder/ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py:399: GtkWarning: /build/buildd/gtk+2.0-2.16.1/gtk/gtktextview.c:4550: somehow some text lines were modified or scrolling occurred since the last validation of lines on the screen - may be a text widget bug.
  gtk.main()
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.16.1/gtk/gtktextview.c:4551:gtk_text_view_paint: code should not be reached
ui/pygtk/python-gtk.sh: line 6: 28269 Aborted                 python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py
```

Then I tried just 6 and 7, and then only 7, and got this notice while Flash was being installed (but no CLI errors):[QUOTE="Program Error"]The program rundll32.exe has encountered a serious problem and needs to close.  We are sorry for the inconvenience.[/QUOTE]

I'm not sure how I got this:```
$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

/home/coder/ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py:264: GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed
  self.textbuffer.delete(it, self.textbuffer.get_end_iter())
```

Thanks.

---

### Post by Vietman on 2009-07-31
Same here:

/home/x0r/ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py:264: GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed
  self.textbuffer.delete(it, self.textbuffer.get_end_iter())

---

### Post by Jesdisciple on 2009-07-31
Hi Vietman.  You might find [this]("http://ubuntuforums.org/showthread.php?t=1205122&page=3") useful regarding IE7.  Also, note that the ies4linux version of IE7 is **very** beta (I don't think this is stressed enough in the GUI), and I think its IE6 is expected to lock the computer eventually.  Using the method described at the above link might help with IE6 if you're persistent.

---

