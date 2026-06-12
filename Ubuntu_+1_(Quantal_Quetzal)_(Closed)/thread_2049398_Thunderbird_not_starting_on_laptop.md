---
title: "Thunderbird not starting on laptop"
date: 2012-08-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by guyster on 2012-08-28
Hi all, I really hope someone can help me here, cause I am stumped.  I upgraded both my desktop and laptop to quantal this past weekend.  My desktop is working as it should, however, on my laptop, I cannot start Thunderbird.  It hangs, and I have to click force quit in order to get it to close.  When I launch it from terminal, I get the following output:

code:
guy@guy-laptop:~>thunderbird

Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 103: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 138: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/69-language-selector-ja-jp.conf", line 141: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/69-language-selector-zh-tw.conf", line 79: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 9: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 22: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 26: Having multiple <family> in <alias> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 31: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-nanum.conf", line 40: Having multiple values in <test> isn't supported and may not works as expected
Fontconfig warning: "/etc/fonts/conf.d/90-fonts-unfonts-core.conf", line 11: Having multiple values in <test> isn't supported and may not works as expected

(thunderbird:2301): GLib-GObject-WARNING **: cannot register existing type `ESource'

(thunderbird:2301): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(thunderbird:2301): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_param_spec_object: assertion `g_type_is_a (object_type, G_TYPE_OBJECT)' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_param_spec_object: assertion `g_type_is_a (object_type, G_TYPE_OBJECT)' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_param_spec_object: assertion `g_type_is_a (object_type, G_TYPE_OBJECT)' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_param_spec_object: assertion `g_type_is_a (object_type, G_TYPE_OBJECT)' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_param_spec_object: assertion `g_type_is_a (object_type, G_TYPE_OBJECT)' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_param_spec_object: assertion `g_type_is_a (object_type, G_TYPE_OBJECT)' failed

(thunderbird:2301): GLib-GObject-CRITICAL **: g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed

(thunderbird:2301): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.33.10/./gobject/gsignal.c:1634: parameter 1 of type `<invalid>' for signal "ESourceRegistry::source_added" is not a value type

(thunderbird:2301): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.33.10/./gobject/gsignal.c:1634: parameter 1 of type `<invalid>' for signal "ESourceRegistry::source_changed" is not a value type

(thunderbird:2301): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.33.10/./gobject/gsignal.c:1634: parameter 1 of type `<invalid>' for signal "ESourceRegistry::source_removed" is not a value type

(thunderbird:2301): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.33.10/./gobject/gsignal.c:1634: parameter 1 of type `<invalid>' for signal "ESourceRegistry::source_enabled" is not a value type

(thunderbird:2301): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.33.10/./gobject/gsignal.c:1634: parameter 1 of type `<invalid>' for signal "ESourceRegistry::source_disabled" is not a value type

On the desktop, I still get the font-config warnings, but then only one gobject warning and everything is fine.  Anyone have any ideas or suggestions?  If so, I would greatly appreciate them.  Thanks much in advance.


Guy

---

### Post by dino99 on 2012-08-28
you should purge then reinstall thunderbird (and watch the similar thread opened)
about the fonts warnings, also a thread is around here, and you can delte the fonts you dont need following the error path.

---

### Post by guyster on 2012-08-28
I solved the problem.  I had three libedataserver packages on my laptop.  Two of them were being loaded when thunderbird ran.  .  Doing sudo apt-get remove libedataserver-1.2-15 is what worked for me.  Keep up the good work Canonical, looking forward to quantal final.

---

### Post by critin on 2012-08-28
> On the desktop, I still get the font-config warnings, but then only one  gobject warning and everything is fine.  Anyone have any ideas or  suggestions?  If so, I would greatly appreciate them.  Thanks much in  advance.

Guy

I also get the font warnings as 'values can't be mixed in test' or something like that.  It comes on shutdown too fast for me to read.

Since 12.10 is still being developed these things are to be expected.  

You might wish you'd kept one of your computers on a stable version.  12.10 isn't ready for production work yet.   Enjoy the testing ride-it's bumpy.

---

