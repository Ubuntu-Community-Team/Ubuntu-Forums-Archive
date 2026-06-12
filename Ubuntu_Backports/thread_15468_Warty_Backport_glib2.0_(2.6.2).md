---
title: "Warty Backport: glib2.0 (2.6.2)"
date: 2005-02-14
forum: Ubuntu Backports
---

### Post by rufius on 2005-02-14
**Synopsis**
Rebuilt glib2.0 (2.6.2) for Warty due to dependency issue with beep-media-player & bmp-extra-plugins.

**Backporting Process**
The source archive directly came from Hoary. With modifications to the debian/rules file I was able to successfully build the libraries.

**Packaging Status:**
i386 -- Staging at revision 33
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**
The libraries work as expected and without err.

---

### Post by dcstar on 2005-02-15
[QUOTE=rufius]**Synopsis**
Rebuilt glib2.0 (2.6.2) for Warty due to dependency issue with beep-media-player & bmp-extra-plugins.

**Backporting Process**
The source archive directly came from Hoary. With modifications to the debian/rules file I was able to successfully build the libraries.

**Packaging Status:**
i386 -- Staging at revision 33
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**
The libraries work as expected and without err.[/QUOTE]

If these are the libglib2.0 files that appeared today, then there is a problem with them.

When I upgraded my Warty 4.10 from the existing 2.4.7-0ubuntu2 versions to the 2.6.2 ones, I then lost all of my custom Applications Menu items.

I could see the Launcher icons in Nautilus "applications:///", but they did not appear in the drop down boxes on my desktop.

I did a "Force Version" and downgraded to the 2.4.7 ones, and the problem disappeared, tried the 2.6.2 upgrade again and the problem returned.

The files in question are:

libglib2.0-0
libglib2.0-data
libglib2.0-dev

---

### Post by rufius on 2005-02-15
[QUOTE=dcstar]If these are the libglib2.0 files that appeared today, then there is a problem with them.

When I upgraded my Warty 4.10 from the existing 2.4.7-0ubuntu2 versions to the 2.6.2 ones, I then lost all of my custom Applications Menu items.

I could see the Launcher icons in Nautilus "applications:///", but they did not appear in the drop down boxes on my desktop.

I did a "Force Version" and downgraded to the 2.4.7 ones, and the problem disappeared, tried the 2.6.2 upgrade again and the problem returned.

The files in question are:

libglib2.0-0
libglib2.0-data
libglib2.0-dev[/QUOTE]
 I suspect this may be an isolated issue then because I've had no issues with them and have been using an upgraded glib2.0 for about 2 weeks now (I hadn't rebuilt them for the repository standards yet). Another user commented that it has been working great for him, and I don't see why glib2.0 would affect the 'Applications' menu seeing as glib2.0 only provides the underlying C construct calls for gnome and not the actual gnome theme/appearance editing things. I could understand if it were maybe GTK+2.0 doing it but glib2.0 shouldn't create said problems. I'll look into it though.

---

### Post by jdong on 2005-02-16
[http://ubuntuforums.org/showthread.php?p=72227#post72227](http://ubuntuforums.org/showthread.php?p=72227#post72227)

We have another bug report against this backport.

It would appear that this new glib somehow imports Hoary's new menu layout into Warty.

I recommend you rebuild it, using Hoary's .orig.tar.gz, and Warty's .diff.gz, or remove it from Backports altogether. We cannot go around dramatically changing Warty's menu layout.

---

### Post by rufius on 2005-02-16
[QUOTE=jdong][http://ubuntuforums.org/showthread.php?p=72227#post72227](http://ubuntuforums.org/showthread.php?p=72227#post72227)

We have another bug report against this backport.

It would appear that this new glib somehow imports Hoary's new menu layout into Warty.

I recommend you rebuild it, using Hoary's .orig.tar.gz, and Warty's .diff.gz, or remove it from Backports altogether. We cannot go around dramatically changing Warty's menu layout.[/QUOTE]
 Noted, I'll work on it tonight.

<edit>
libglib2.0 has been updated, using the .diff.gz from Warty with the orig.tar.gz from Hoary.
</edit>

---

### Post by dcstar on 2005-02-28
[QUOTE=rufius]I suspect this may be an isolated issue then because I've had no issues with them and have been using an upgraded glib2.0 for about 2 weeks now (I hadn't rebuilt them for the repository standards yet). Another user commented that it has been working great for him, and I don't see why glib2.0 would affect the 'Applications' menu seeing as glib2.0 only provides the underlying C construct calls for gnome and not the actual gnome theme/appearance editing things. I could understand if it were maybe GTK+2.0 doing it but glib2.0 shouldn't create said problems. I'll look into it though.[/QUOTE]
I still have the same problem with the version 2 libglib backport, I cannot see my personal menu items with it.

Is there a dependency I haven't upgraded?

---

### Post by rufius on 2005-02-28
[QUOTE=dcstar]I still have the same problem with the version 2 libglib backport, I cannot see my personal menu items with it.

Is there a dependency I haven't upgraded?[/QUOTE]
 ubp2 release fixed that issue. do a "dpkg -l libglib2.0-0" and make sure you paste the whole name. It should have ubp2 which is the updated version using the diff.gz from Warty's libglib2.0 and the Hoary tar.gz.

---

### Post by dcstar on 2005-03-01
[QUOTE=rufius]ubp2 release fixed that issue. do a "dpkg -l libglib2.0-0" and make sure you paste the whole name. It should have ubp2 which is the updated version using the diff.gz from Warty's libglib2.0 and the Hoary tar.gz.[/QUOTE]

In a shell window it says:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libglib2.0-0   2.6.2-0ubuntu1 The GLib library of C routines


In Synaptic (installed and latest) it says: 2.6.2-0ubuntu1-4.10ubp2

And just out of interest:

# dpkg -L libglib2.0-0
/.
/usr
/usr/lib
/usr/lib/libglib-2.0.so.0.600.2
/usr/lib/libgthread-2.0.so.0.600.2
/usr/lib/libgobject-2.0.so.0.600.2
/usr/lib/libgmodule-2.0.so.0.600.2
/usr/share
/usr/share/doc
/usr/share/doc/libglib2.0-0
/usr/share/doc/libglib2.0-0/changelog.gz
/usr/share/doc/libglib2.0-0/changelog.Debian.gz
/usr/lib/libglib-2.0.so.0
/usr/lib/libgmodule-2.0.so.0

/usr/lib # l libglib*
lrwxrwxrwx    1 root     root           21 2005-01-16 09:03 libglib-1.2.so.0 -> libglib-1.2.so.0.0.10
-rw-r--r--    1 root     root       141740 2004-08-13 10:48 libglib-1.2.so.0.0.10
lrwxrwxrwx    1 root     root           22 2005-03-01 09:39 libglib-2.0.so.0 -> libglib-2.0.so.0.600.2
-rw-r--r--    1 root     root       522872 2005-02-18 08:17 libglib-2.0.so.0.600.2
lrwxrwxrwx    1 root     root           23 2005-01-19 18:25 libglibmm-2.0.so.1 -> libglibmm-2.0.so.1.5.10
-rw-r--r--    1 root     root       278392 2004-08-13 11:18 libglibmm-2.0.so.1.5.10

/usr/lib # l libgmodule*
lrwxrwxrwx    1 root     root           24 2005-01-16 09:03 libgmodule-1.2.so.0 -> libgmodule-1.2.so.0.0.10
-rw-r--r--    1 root     root         8652 2004-08-13 10:48 libgmodule-1.2.so.0.0.10
lrwxrwxrwx    1 root     root           25 2005-03-01 09:39 libgmodule-2.0.so.0 -> libgmodule-2.0.so.0.600.2
-rw-r--r--    1 root     root        10824 2005-02-18 08:17 libgmodule-2.0.so.0.600.2

---

### Post by rufius on 2005-03-01
[QUOTE=dcstar]In a shell window it says:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libglib2.0-0   2.6.2-0ubuntu1 The GLib library of C routines


In Synaptic (installed and latest) it says: 2.6.2-0ubuntu1-4.10ubp2

And just out of interest:

# dpkg -L libglib2.0-0
/.
/usr
/usr/lib
/usr/lib/libglib-2.0.so.0.600.2
/usr/lib/libgthread-2.0.so.0.600.2
/usr/lib/libgobject-2.0.so.0.600.2
/usr/lib/libgmodule-2.0.so.0.600.2
/usr/share
/usr/share/doc
/usr/share/doc/libglib2.0-0
/usr/share/doc/libglib2.0-0/changelog.gz
/usr/share/doc/libglib2.0-0/changelog.Debian.gz
/usr/lib/libglib-2.0.so.0
/usr/lib/libgmodule-2.0.so.0

/usr/lib # l libglib*
lrwxrwxrwx    1 root     root           21 2005-01-16 09:03 libglib-1.2.so.0 -> libglib-1.2.so.0.0.10
-rw-r--r--    1 root     root       141740 2004-08-13 10:48 libglib-1.2.so.0.0.10
lrwxrwxrwx    1 root     root           22 2005-03-01 09:39 libglib-2.0.so.0 -> libglib-2.0.so.0.600.2
-rw-r--r--    1 root     root       522872 2005-02-18 08:17 libglib-2.0.so.0.600.2
lrwxrwxrwx    1 root     root           23 2005-01-19 18:25 libglibmm-2.0.so.1 -> libglibmm-2.0.so.1.5.10
-rw-r--r--    1 root     root       278392 2004-08-13 11:18 libglibmm-2.0.so.1.5.10

/usr/lib # l libgmodule*
lrwxrwxrwx    1 root     root           24 2005-01-16 09:03 libgmodule-1.2.so.0 -> libgmodule-1.2.so.0.0.10
-rw-r--r--    1 root     root         8652 2004-08-13 10:48 libgmodule-1.2.so.0.0.10
lrwxrwxrwx    1 root     root           25 2005-03-01 09:39 libgmodule-2.0.so.0 -> libgmodule-2.0.so.0.600.2
-rw-r--r--    1 root     root        10824 2005-02-18 08:17 libgmodule-2.0.so.0.600.2[/QUOTE]
 No, thats not the whole name. stretch the terminal horizontally and you'll see the entire version number when you type 'dpkg -l libglib2.0-0'.

---

### Post by dcstar on 2005-03-01
[QUOTE=rufius]No, thats not the whole name. stretch the terminal horizontally and you'll see the entire version number when you type 'dpkg -l libglib2.0-0'.[/QUOTE]
# dpkg -l libglib2.0-0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  libglib2.0-0              2.6.2-0ubuntu1-4.10ubp2   The GLib library of C routines

---

