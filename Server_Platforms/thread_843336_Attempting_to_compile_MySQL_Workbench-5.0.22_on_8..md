---
title: "Attempting to compile MySQL Workbench-5.0.22 on 8.04"
date: 2008-06-28
forum: Server Platforms
---

### Post by dynamethod on 2008-06-28
Hey there i've got as far as this:

```
configure: error: Could not find mysql_config script. Make sure the mysql client libraries are installed

```


though i have installed LAMP onto this Desktop edition of 8.04 through apt-get


has anyone successfully compiled this before?

---

### Post by pdwerryhouse on 2008-06-28
Have you got the libmysqlclient15-dev package installed?

---

### Post by windependence on 2008-06-28
It's looking for the CLIENT libraries. For LAMP you only install the SERVER libraries. You need to intstall the MySQL client package. Also, you may want to as pdwerryhouse said install the dev package. In fact, you might just want to install the entire dev group if you have space.

-Tim

---

### Post by dynamethod on 2008-06-29
I have all the necessary -dev debs, i can now compile, but it fails on make


```
make  all-recursive
make[1]: Entering directory `/opt/mysql-workbench-5.0.22'
Making all in res
make[2]: Entering directory `/opt/mysql-workbench-5.0.22/res'
Making all in grt
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/res/grt'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/res/grt'
Making all in grtdata
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/res/grtdata'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/res/grtdata'
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/res'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/res'
make[2]: Leaving directory `/opt/mysql-workbench-5.0.22/res'
Making all in images
make[2]: Entering directory `/opt/mysql-workbench-5.0.22/images'
Making all in icons
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/images/icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/images/icons'
Making all in grt
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/images/grt'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/images/grt'
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/images'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/images'
make[2]: Leaving directory `/opt/mysql-workbench-5.0.22/images'
Making all in library
make[2]: Entering directory `/opt/mysql-workbench-5.0.22/library'
Making all in canvas
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/library/canvas'
Making all in src
make[4]: Entering directory `/opt/mysql-workbench-5.0.22/library/canvas/src'
g++ -DHAVE_CONFIG_H -I. -I../../.. -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0   -I../../../backend    -Wall -ggdb3 -MT mdc_algorithms.o -MD -MP -MF .deps/mdc_algorithms.Tpo -c -o mdc_algorithms.o mdc_algorithms.cpp
mdc_algorithms.cpp:94: fatal error: opening dependency file .deps/mdc_algorithms.Tpo: Permission denied
compilation terminated.
make[4]: *** [mdc_algorithms.o] Error 1
make[4]: Leaving directory `/opt/mysql-workbench-5.0.22/library/canvas/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/library/canvas'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/mysql-workbench-5.0.22/library'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/mysql-workbench-5.0.22'
make: *** [all] Error 2
```

---

### Post by windependence on 2008-06-29
OK you have a permissions issue on file .deps/mdc_algorithms.Tpo

First you have to find where that file is. I think it's probably in /usr/include but I could be wrong.

Do a ```
sudo find / -name .deps/mdc_algorithms.Tpo
``` to see where it is and chmod it to something like 775. Then try your make again.

-Tim

---

### Post by dynamethod on 2008-06-30
```
joe@darksun:~$ sudo find / -name .deps/mdc_algorithms.Tpo
[sudo] password for joe: 
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-name .deps/mdc_algorithms.Tpo' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ .deps/mdc_algorithms.Tpo'.
find: /home/joe/.gvfs: Permission denied
```

```
 chmod 755 .gvfs
```


```
make  all-recursive
make[1]: Entering directory `/opt/mysql-workbench-5.0.22'
Making all in res
make[2]: Entering directory `/opt/mysql-workbench-5.0.22/res'
Making all in grt
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/res/grt'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/res/grt'
Making all in grtdata
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/res/grtdata'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/res/grtdata'
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/res'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/res'
make[2]: Leaving directory `/opt/mysql-workbench-5.0.22/res'
Making all in images
make[2]: Entering directory `/opt/mysql-workbench-5.0.22/images'
Making all in icons
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/images/icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/images/icons'
Making all in grt
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/images/grt'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/images/grt'
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/images'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/images'
make[2]: Leaving directory `/opt/mysql-workbench-5.0.22/images'
Making all in library
make[2]: Entering directory `/opt/mysql-workbench-5.0.22/library'
Making all in canvas
make[3]: Entering directory `/opt/mysql-workbench-5.0.22/library/canvas'
Making all in src
make[4]: Entering directory `/opt/mysql-workbench-5.0.22/library/canvas/src'
g++ -DHAVE_CONFIG_H -I. -I../../.. -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0   -I../../../backend    -Wall -ggdb3 -MT mdc_algorithms.o -MD -MP -MF .deps/mdc_algorithms.Tpo -c -o mdc_algorithms.o mdc_algorithms.cpp
mdc_algorithms.cpp:94: fatal error: opening dependency file .deps/mdc_algorithms.Tpo: Permission denied
compilation terminated.
make[4]: *** [mdc_algorithms.o] Error 1
make[4]: Leaving directory `/opt/mysql-workbench-5.0.22/library/canvas/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/opt/mysql-workbench-5.0.22/library/canvas'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/mysql-workbench-5.0.22/library'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/mysql-workbench-5.0.22'
make: *** [all] Error 2 
```

---

### Post by windependence on 2008-06-30
Sorry, my bad, should have been:

```
sudo find / -name mdc_algorithms.Tpo
```

Try that and see if you can find the file before chmodding it. DO NOT chmod anything but mdc_algorithms.Tpo

-Tim

---

### Post by dynamethod on 2008-06-30
No luck :S

---

### Post by windependence on 2008-06-30
So the file does not existon your machine?

I guess I should ask you also is there not a debian package for this?

Also looks like it needs some Windows dependencies. Did you install these first?

-Tim

---

### Post by dynamethod on 2008-06-30
the command: sudo find / -name mdc_algorithms.Tpo

did not find anything unfortunatly, as for Windows dependencies, i had no idea i needed these, i dont even know where or what windows dependancies i need actually, and what deb package should i be looking for exactly, mdc_algorithms.deb? or something similar?

---

### Post by dynamethod on 2008-07-01
Heres the contents of /opt/mysql-workbench-5.0.22/library/canvas/src

```
total 284
-rw-r--r-- 1 root root 18170 2008-06-29 01:25 mdc_algorithms.Po
-rw-r--r-- 1 root root 20816 2008-06-29 01:26 mdc_area_group.Po
-rw-r--r-- 1 root root 20772 2008-06-29 01:26 mdc_back_layer.Po
-rw-r--r-- 1 root root 18319 2008-06-29 01:26 mdc_bounds_magnet.Po
-rw-r--r-- 1 root root 18208 2008-06-29 01:26 mdc_box_handle.Po
-rw-r--r-- 1 root root 18237 2008-06-29 01:26 mdc_box.Po
-rw-r--r-- 1 root root 18306 2008-06-29 01:26 mdc_button.Po
-rw-r--r-- 1 root root 20941 2008-06-29 01:26 mdc_canvas_item.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_canvas_view_glitz.Po
-rw-r--r-- 1 root root     0 2008-06-29 01:37 mdc_canvas_view_glitz.Tpo
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_canvas_view_image.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_canvas_view_linux.Po
-rw-r--r-- 1 root root 21133 2008-06-29 01:26 mdc_canvas_view.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_common.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_connector.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_draw_util.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_figure.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_group.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_gtk_canvas_scroller.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_gtk_canvas_view.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_icon_text.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_image_manager.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_interaction_layer.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_item_handle.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_layer.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_layouter.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_line.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_magnet.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_rectangle.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_selection.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_text.Po
-rw-r--r-- 1 root root     8 2008-06-29 01:21 mdc_vertex_handle.Po
```

Theres no file called mdc_algorithms.Tpo that i could find, only a file called mdc_algorithms.Po

---

### Post by windependence on 2008-07-01
> **dynamethod said:**
> the command: sudo find / -name mdc_algorithms.Tpo

did not find anything unfortunatly, as for Windows dependencies, i had no idea i needed these, i dont even know where or what windows dependancies i need actually, and what deb package should i be looking for exactly, mdc_algorithms.deb? or something similar?

Go here:

[http://dev.mysql.com/downloads/workbench/5.0.html](http://dev.mysql.com/downloads/workbench/5.0.html)

You may want to try 5.023, and don't forget the Windows dependencies. I am a bit confused though, so you install this on windows after you compile?

-Tim

---

### Post by dynamethod on 2008-07-01
im not trying to compile workbench for windows, im trying to do it on ubuntu, but yeah i see on that link that i have missed the Required Windows Dependencies, ill download them tonight and try again

---

### Post by dynamethod on 2008-07-02
I just downloaded .23 and the required windows dependancies and extracted to /opt/mysql-workbench-5.0.23, sh autogen.sh went find but make is still failing:

```
make  all-recursive
make[1]: Entering directory `/opt/mysql-workbench-5.0.23'
Making all in res
make[2]: Entering directory `/opt/mysql-workbench-5.0.23/res'
Making all in grt
make[3]: Entering directory `/opt/mysql-workbench-5.0.23/res/grt'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.23/res/grt'
Making all in grtdata
make[3]: Entering directory `/opt/mysql-workbench-5.0.23/res/grtdata'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.23/res/grtdata'
make[3]: Entering directory `/opt/mysql-workbench-5.0.23/res'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.23/res'
make[2]: Leaving directory `/opt/mysql-workbench-5.0.23/res'
Making all in images
make[2]: Entering directory `/opt/mysql-workbench-5.0.23/images'
Making all in icons
make[3]: Entering directory `/opt/mysql-workbench-5.0.23/images/icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.23/images/icons'
Making all in grt
make[3]: Entering directory `/opt/mysql-workbench-5.0.23/images/grt'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.23/images/grt'
make[3]: Entering directory `/opt/mysql-workbench-5.0.23/images'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/opt/mysql-workbench-5.0.23/images'
make[2]: Leaving directory `/opt/mysql-workbench-5.0.23/images'
Making all in library
make[2]: Entering directory `/opt/mysql-workbench-5.0.23/library'
Making all in canvas
make[3]: Entering directory `/opt/mysql-workbench-5.0.23/library/canvas'
Making all in src
make[4]: Entering directory `/opt/mysql-workbench-5.0.23/library/canvas/src'
g++ -DHAVE_CONFIG_H -I. -I../../.. -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1   -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0   -I../../../backend    -Wall -ggdb3 -MT mdc_algorithms.o -MD -MP -MF .deps/mdc_algorithms.Tpo -c -o mdc_algorithms.o mdc_algorithms.cpp
mdc_algorithms.cpp:94: fatal error: opening dependency file .deps/mdc_algorithms.Tpo: Permission denied
compilation terminated.
make[4]: *** [mdc_algorithms.o] Error 1
make[4]: Leaving directory `/opt/mysql-workbench-5.0.23/library/canvas/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/opt/mysql-workbench-5.0.23/library/canvas'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/mysql-workbench-5.0.23/library'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/mysql-workbench-5.0.23'
make: *** [all] Error 2
```

---

### Post by windependence on 2008-07-02
Did you install the windows deps first?

-Tim

---

### Post by dynamethod on 2008-07-02
in :/opt/mysql-workbench-5.0.23/mysql-gui-win-res/bin, theres only .exe's, i cant find any make file or configure script within the mysql-gui-win-res directorys

---

### Post by windependence on 2008-07-02
What bothers me is that your error message is this:

> fatal error: opening dependency file .deps/mdc_algorithms.Tpo: Permission denied

That tells me the file is there but it has the wrong permissions. Do you have a .deps directory anywhere on the server?

do a :

```
sudo locate .deps
```

and see if you can find it.

-Tim

---

### Post by dynamethod on 2008-07-02
```
joe@server:/opt$ sudo locate .deps
/home/joe/GUI/56438-Aurora-1.4/aurora-1.4/.deps
/home/joe/GUI/56438-Aurora-1.4/aurora-1.4/.deps/animation.Plo
/home/joe/GUI/56438-Aurora-1.4/aurora-1.4/.deps/aurora_draw.Plo
/home/joe/GUI/56438-Aurora-1.4/aurora-1.4/.deps/aurora_rc_style.Plo
/home/joe/GUI/56438-Aurora-1.4/aurora-1.4/.deps/aurora_style.Plo
/home/joe/GUI/56438-Aurora-1.4/aurora-1.4/.deps/aurora_theme_main.Plo
/home/joe/GUI/56438-Aurora-1.4/aurora-1.4/.deps/support.Plo

```

weird :S

---

### Post by windependence on 2008-07-02
What do you get if you do:

```
sudo locate mdc_algorithms.Tpo
```

-Tim

---

### Post by dynamethod on 2008-07-02
no results for sudo locate mdc_algorithms.Tpo

---

### Post by isleshocky77 on 2008-07-22
Did you ever get MySQL Workbench to compile on Ubuntu 8.04? I'm running KUbuntu desktop edition and having little luck.

---

### Post by windependence on 2008-07-23
What is the error you are getting?

-Tim

---

