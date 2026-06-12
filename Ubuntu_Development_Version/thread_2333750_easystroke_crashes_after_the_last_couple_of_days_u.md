---
title: "easystroke crashes after the last couple of days updates"
date: 2016-08-12
forum: Ubuntu Development Version
---

### Post by ubername on 2016-08-12
Hi
Easystroke has stopped working. If I run it from the terminal it draws the gesture on the screen and then crashes with
(easystroke:31196): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion 'width > 0' failed
Segmentation fault (core dumped)

Any Clues?

---

### Post by ubername on 2016-08-20
Problem seems to lie with
TreeViewMulti::TreeViewMulti() : Gtk::TreeView(), pending(false) {
	get_selection()->set_select_function(sigc::group(&negate, sigc::ref(pending)));
}
in actions.cc

sigc::group has been deprecated. Any cool coders out there know how to fix this? I am not a coder, but can read error messages!

---

### Post by ubername on 2016-08-22
somehow managed to get to the ui before crashing and switched off 'show in systray' which seems to have helped for the time being.

---

