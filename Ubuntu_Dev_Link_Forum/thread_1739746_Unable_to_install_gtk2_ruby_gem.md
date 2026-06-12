---
title: "Unable to install gtk2 ruby gem"
date: 2011-04-26
forum: Ubuntu Dev Link Forum
---

### Post by mindaslab on 2011-04-26
Hello People,

I have installed Ruby 1.9.2 by compiling it on Ubuntu. I want to do some Ruby GTK programming and hence I typed sudo gem install gtk2 and this is what I got:

Building native extensions.  This could take a while...
ERROR:  Error installing gtk2:
	ERROR: Failed to build gem native extension.

/usr/local/ruby/bin/ruby extconf.rb
checking for GCC... yes
checking for rb_define_alloc_func() in ruby.h... yes
checking for rb_block_proc() in ruby.h... yes
checking for new allocation framework... yes
checking for attribute assignment... no
checking for Win32 OS... no
checking for gobject-2.0... no
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.

Provided configuration options:
	--with-opt-dir
	--without-opt-dir
	--with-opt-include
	--without-opt-include=${opt-dir}/include
	--with-opt-lib
	--without-opt-lib=${opt-dir}/lib
	--with-make-prog
	--without-make-prog
	--srcdir=.
	--curdir
	--ruby=/usr/local/ruby/bin/ruby
	--with-pkg-config
	--without-pkg-config
	--with-override-variables
	--without-override-variables


Gem files will remain installed in /usr/local/ruby/lib/ruby/gems/1.9.1/gems/glib2-0.90.8 for inspection.
Results logged to /usr/local/ruby/lib/ruby/gems/1.9.1/gems/glib2-0.90.8/ext/glib2/gem_make.out

**Please don't tell me to sudo apt-get install gobject-2.0 **, because if I do it, it says its already in it latest version. I think there is some library missing in Ubuntu thats causing this problem.

Thanks for reading this message. Hope you can find a solution.

---

### Post by mc4man on 2011-04-26
I do build and install ruby-gtk2 here (ruby-gtk2-0.19.4), do a little differently and for different reasons - 
Anyway maybe you should try installing libgtk2.0-dev which will pull in some add. dep's
Here's a full ex. of ruby extconf.rb on the gtk2 source

> ~/rubyr/ruby-gtk2-0.19.4$ ruby extconf.rb
extconf.rb: Entering directory `glib'
checking for GCC... yes
checking for rb_define_alloc_func() in ruby.h... yes
checking for rb_block_proc() in ruby.h... yes
checking for new allocation framework... yes
checking for attribute assignment... no
checking for gobject-2.0... yes
checking for gthread-2.0... yes
checking for G_PLATFORM_WIN32... no
checking for unistd.h... yes
checking for io.h... no
checking for g_spawn_close_pid() in glib.h... yes
checking for g_thread_init() in glib.h... yes
checking for g_main_depth() in glib.h... yes
checking for g_listenv() in glib.h... yes
checking for rb_check_array_type() in ruby.h... yes
checking for rb_exec_recursive() in ruby.h... yes
checking for rb_errinfo() in ruby.h... yes
checking for rb_sourcefile() in ruby.h... yes
checking for rb_sourceline() in ruby.h... yes
checking for ruby_set_current_source() in ruby.h... no
checking for rb_thread_blocking_region() in ruby.h... yes
checking for ruby_native_thread_p() in ruby.h... yes
checking for rb_str_encode() in ruby.h... yes
checking for curr_thread in ruby.h,node.h... no
checking for rb_curr_thread in ruby.h,node.h... no
creating ruby-glib2.pc
creating glib-enum-types.c
creating glib-enum-types.h
creating Makefile
extconf.rb: Leaving directory 'glib'
extconf.rb: Entering directory `gdkpixbuf'
checking for GCC... yes
checking for rb_define_alloc_func() in ruby.h... yes
checking for rb_block_proc() in ruby.h... yes
checking for new allocation framework... yes
checking for attribute assignment... no
checking for gdk-pixbuf-2.0... yes
checking for G_PLATFORM_WIN32... no
checking for gdk_pixbuf_set_option() in gdk-pixbuf/gdk-pixbuf.h... yes
checking for gdk-pixbuf/gdk-pixbuf-io.h... yes
checking for gdk-2.0... yes
checking for cairo... yes
checking for rb_cairo.h... no
creating ruby-gdkpixbuf2.pc
creating Makefile
extconf.rb: Leaving directory 'gdkpixbuf'
extconf.rb: Entering directory `pango'
checking for GCC... yes
checking for rb_define_alloc_func() in ruby.h... yes
checking for rb_block_proc() in ruby.h... yes
checking for new allocation framework... yes
checking for attribute assignment... no
checking for pango... yes
checking for G_PLATFORM_WIN32... no
checking for pango_layout_iter_get_type() in pango/pango.h... yes
checking for pango_layout_set_ellipsize() in pango/pango.h... yes
checking for pango_layout_get_font_description() in pango/pango.h... yes
checking for pango_render_part_get_type() in pango/pango.h... yes
checking for pango_attr_strikethrough_color_new() in pango/pango.h... yes
checking for pango_attr_underline_color_new() in pango/pango.h... yes
checking for pango_glyph_item_free() in pango/pango.h... yes
checking for pango_glyph_item_get_type() in pango/pango.h... yes
checking for pango_attr_iterator_get_attrs() in pango/pango.h... yes
checking for pango_itemize_with_base_dir() in pango/pango.h... yes
checking for pango_font_family_is_monospace() in pango/pango.h... yes
checking for pangocairo... yes
checking for cairo... yes
checking for rb_cairo.h... no
creating rbpangoversion.h
creating ruby-pango.pc
creating Makefile
extconf.rb: Leaving directory 'pango'
extconf.rb: Entering directory `atk'
checking for GCC... yes
checking for rb_define_alloc_func() in ruby.h... yes
checking for rb_block_proc() in ruby.h... yes
checking for new allocation framework... yes
checking for attribute assignment... no
checking for atk... yes
checking for G_PLATFORM_WIN32... no
checking for atk_action_get_localized_name() in atk/atk.h... yes
checking for atk_hyperlink_is_inline() in atk/atk.h... yes
checking for atk_object_add_relationship() in atk/atk.h... yes
checking for atk_object_remove_relationship() in atk/atk.h... yes
checking for atk_component_get_layer() in atk/atk.h... yes
checking for atk_component_get_mdi_zorder() in atk/atk.h... yes
checking for atk_hyperlink_is_selected_link() in atk/atk.h... yes
checking for atk_text_get_bounded_ranges() in atk/atk.h... yes
checking for atk_role_get_localized_name() in atk/atk.h... yes
checking for atk_text_clip_type_get_type() in atk/atk.h... yes
checking for atk_text_free_ranges() in atk/atk.h... yes
creating rbatkversion.h
creating ruby-atk.pc
creating Makefile
extconf.rb: Leaving directory 'atk'
extconf.rb: Entering directory `gtk'
checking for GCC... yes
checking for rb_define_alloc_func() in ruby.h... yes
checking for rb_block_proc() in ruby.h... yes
checking for new allocation framework... yes
checking for attribute assignment... no
checking for gthread-2.0... yes
checking for gtk+-2.0... yes
checking for G_PLATFORM_WIN32... no
checking for st.h... yes
checking for ruby/st.h... yes
checking for target... x11
checking for gtk_plug_get_type() in gtk/gtk.h... yes
checking for gtk_socket_get_type() in gtk/gtk.h... yes
checking for pango_render_part_get_type() in gtk/gtk.h... yes
checking for gtk/gtkfilesystem.h... yes
checking for X11/Xlib.h... yes
checking for XReadBitmapFileData() in X11/Xlib.h... yes
checking for XGetErrorText() in X11/Xlib.h... yes
checking for gtk+-unix-print-2.0... yes
checking for rb_errinfo()... yes
checking for cairo... yes
checking for rb_cairo.h... no
creating ruby-gtk2.pc
creating Makefile
extconf.rb: Leaving directory 'gtk'

-----
Target libraries: glib, gdkpixbuf, pango, atk, gtk
-----
Done.


---

### Post by themactep on 2011-07-18
you need to install libgtk2.0-dev in order to build gtk2 gem

---

