---
title: "WinFF Stop Working"
date: 2012-02-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kuvanito on 2012-02-26
after latest updates winff stoped working with this message:
this is a clean install of pp and winff was working yesterday
any clues?

---

### Post by dino99 on 2012-02-26
you should find some errors logged into xsession-errors or dmesg
or run it from a terminal to get the output, and maybe send a report.

---

### Post by kuvanito on 2012-02-26
this what i get when run from terminal:
ari@Ari:~$ winff

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
TApplication.HandleException Unable to create file "/home/ari/.winff/cfg.xml"
  Stack trace:
  $0821A152
  $08203602
  $081FA20A
  $081F9629
  $081F951F
  $0820FEE2
  $0806FF93
  $081045B4
  $0815C15F
  $0815C7A6
  $0814F60F
  $0815C06A
  $082100EA
  $080F9ABD
  $081BD387
  $081C6810
  $B706E59C
[CRITICAL] os_bar_hide: assertion `OS_IS_BAR (bar)' failed

Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
[CRITICAL] os_bar_set_parent: assertion `OS_IS_BAR (bar)' failed

LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
ari@Ari:~$

---

