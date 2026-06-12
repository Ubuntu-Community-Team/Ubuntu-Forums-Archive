---
title: "Dashboard, F-Spot, Tomboy on Ubuntu Linux"
date: 2004-11-28
forum: The Cafe
---

### Post by macewan on 2004-11-28
Just wanted to drop a note saying that dashboard, f-spot, tomboy & beagle also install and work fine on Ubuntu Linux Warty. Dashboard was installed from cvs.


Note sure where this should be posted so I choose this section.
:)

---

### Post by yatesco on 2005-02-28
When did you checkout dashboard CVS?  Today's (28/02/2005, 21:49 GMT) was broken when running make:

<code>
mcs -g -warnaserror -target:library -L ../util/webservices -r:/usr/lib/mono/gtk-sharp/glib-sharp.dll -r:/usr/lib/mono/gtk-sharp/pango-sharp.dll -r:/usr/lib/mono/gtk-sharp/atk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gdk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gtk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gnome-sharp.dll -r:/usr/lib/mono/gtk-sharp/art-sharp.dll -r:/usr/lib/mono/gtk-sharp/gtkhtml-sharp.dll   -r:/usr/lib/mono/gtk-sharp/gconf-sharp.dll -r:/usr/lib/mono/gtk-sharp/gconf-sharp-peditors.dll -r:/usr/lib/mono/gtk-sharp/gnome-sharp.dll -r:/usr/lib/mono/gtk-sharp/glib-sharp.dll -r:/usr/lib/mono/gtk-sharp/pango-sharp.dll -r:/usr/lib/mono/gtk-sharp/atk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gdk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gtk-sharp.dll -r:/usr/lib/mono/gtk-sharp/art-sharp.dll   -r:System.Web -r:../engine/dashboard.exe -r:../util/drive/drive.dll -r:../engine/rdf.dll -out:BeagleBackend.dll ./BeagleBackend.cs ../engine/gnome.cs -r:/usr/local/lib/beagle/Beagle.dll -r:/usr/local/lib/beagle/Tiles.dll -r:/usr/local/lib/beagle/Util.dll -r:/usr/lib/mono/dbus-sharp/dbus-sharp.dll
./BeagleBackend.cs(63) error CS0103: The name `Beagle.Util.Icon.LookupByURI' could not be found in `Dashboard.BeagleBackend'
./BeagleBackend.cs(64) error CS0165: Use of unassigned local variable `icon'
./BeagleBackend.cs(85) error CS0162: Unreachable code detected
Compilation failed: 3 error(s), 0 warnings
make[1]: *** [BeagleBackend.dll] Error 1
make[1]: Leaving directory `/home/yatesco/projects/dashboard/backends'
make: *** [all-recursive] Error 1

</code>

---

### Post by macewan on 2005-02-28
[QUOTE=yatesco]When did you checkout dashboard CVS?  Today's (28/02/2005, 21:49 GMT) was broken when running make:

<code>
mcs -g -warnaserror -target:library -L ../util/webservices -r:/usr/lib/mono/gtk-sharp/glib-sharp.dll -r:/usr/lib/mono/gtk-sharp/pango-sharp.dll -r:/usr/lib/mono/gtk-sharp/atk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gdk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gtk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gnome-sharp.dll -r:/usr/lib/mono/gtk-sharp/art-sharp.dll -r:/usr/lib/mono/gtk-sharp/gtkhtml-sharp.dll   -r:/usr/lib/mono/gtk-sharp/gconf-sharp.dll -r:/usr/lib/mono/gtk-sharp/gconf-sharp-peditors.dll -r:/usr/lib/mono/gtk-sharp/gnome-sharp.dll -r:/usr/lib/mono/gtk-sharp/glib-sharp.dll -r:/usr/lib/mono/gtk-sharp/pango-sharp.dll -r:/usr/lib/mono/gtk-sharp/atk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gdk-sharp.dll -r:/usr/lib/mono/gtk-sharp/gtk-sharp.dll -r:/usr/lib/mono/gtk-sharp/art-sharp.dll   -r:System.Web -r:../engine/dashboard.exe -r:../util/drive/drive.dll -r:../engine/rdf.dll -out:BeagleBackend.dll ./BeagleBackend.cs ../engine/gnome.cs -r:/usr/local/lib/beagle/Beagle.dll -r:/usr/local/lib/beagle/Tiles.dll -r:/usr/local/lib/beagle/Util.dll -r:/usr/lib/mono/dbus-sharp/dbus-sharp.dll
./BeagleBackend.cs(63) error CS0103: The name `Beagle.Util.Icon.LookupByURI' could not be found in `Dashboard.BeagleBackend'
./BeagleBackend.cs(64) error CS0165: Use of unassigned local variable `icon'
./BeagleBackend.cs(85) error CS0162: Unreachable code detected
Compilation failed: 3 error(s), 0 warnings
make[1]: *** [BeagleBackend.dll] Error 1
make[1]: Leaving directory `/home/yatesco/projects/dashboard/backends'
make: *** [all-recursive] Error 1

</code>[/QUOTE]


11-28-2004

---

### Post by yatesco on 2005-03-01
Cool.  I will checkout that date.  If only I can remember how :)

---

### Post by telmo on 2005-03-05
Can you please post how you installed them step by step?
thx

---

### Post by poofyhairguy on 2005-03-05
[QUOTE=telmo]Can you please post how you installed them step by step?
thx[/QUOTE]

Look in wiki:

[http://www.ubuntulinux.org/wiki/BeagleInstallHowto](http://www.ubuntulinux.org/wiki/BeagleInstallHowto)

[http://www.ubuntulinux.org/wiki/Dashboard](http://www.ubuntulinux.org/wiki/Dashboard)

---

### Post by macewan on 2005-03-05
[QUOTE=poofyhairguy]Look in wiki:

[http://www.ubuntulinux.org/wiki/BeagleInstallHowto](http://www.ubuntulinux.org/wiki/BeagleInstallHowto)

[http://www.ubuntulinux.org/wiki/Dashboard](http://www.ubuntulinux.org/wiki/Dashboard)[/QUOTE]
 careful though - think the latest beagle doesn't need inotify

---

### Post by telmo on 2005-03-05
Thx... 

I was trying to install that but it seems libxss-dev in not in any repository. :(
I'm not even going to try and install Beagle without that!
I don't want to have my pc filled with 'useless' trash.

By the way... is it possible to install dashboard without Beagle?

---

### Post by tim1 on 2005-03-05
[QUOTE=telmo]By the way... is it possible to install dashboard without Beagle?[/QUOTE]

Since beagle is meant as underlying indexing daemon for dashboard I don't think so.

greets, tim

---

### Post by telmo on 2005-03-05
That's what i thought... thx.

---

