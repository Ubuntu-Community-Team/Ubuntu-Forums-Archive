---
title: "URGENT: Massive Mono Testing Needed"
date: 2005-05-24
forum: Ubuntu Backports
---

### Post by jdong on 2005-05-24
I was just talking to tseng (Mono maintainer for Ubuntu), who was very upset about the Mono backport (1.1.7) in Hoary Backports. The gist of the conversation was that Mono has switched infrastructure, which causes most of **Hoary Universe's mono-dependent packages to be BROKEN.**

Please test mono apps in Hoary, and tell me if any aren't working. I know blam has refreshing issues. These need to be backported ASAP.

---

### Post by Technoviking on 2005-05-24
The only thing I have noticed is that Best (from Beagle) crashes on file searches.

Mike

---

### Post by jdong on 2005-05-24
[QUOTE=Mike Basinger]The only thing I have noticed is that Best (from Beagle) crashes on file searches.

Mike[/QUOTE]

You're a dev, lol

Have you investigated the cause of the crash?

---

### Post by jdong on 2005-05-24
Blam: uploaded new backport from Breezy. Hopefully this fixes it.

EDIT:
```

$ blam

Unhandled Exception: System.DllNotFoundException: libblam.so
in (wrapper managed-to-native) Imendio.Blam.MessageConnection:bacon_message_connection_new (string)
in <0x00016> Imendio.Blam.MessageConnection:.ctor (System.String appName)
in <0x00075> Imendio.Blam.Application:.ctor (System.String[] args, System.Object[] props)
in <0x0002c> Imendio.Blam.Application:Main (System.String[] args)

```

hmm, libblam.so is in /usr/lib/blam....

How do I get mono to search for so's in a specific folder?

---

### Post by Technoviking on 2005-05-25
[QUOTE=jdong]You're a dev, lol

Have you investigated the cause of the crash?[/QUOTE]
Just starting use Beagle, so thought it could be a configure error on my part. I will keep playing with it.

Mike

---

### Post by dlpfmVfH on 2005-05-25
Ok, how can I help testing this,

by just installing everything mono?? or what?? want to help with the backports project

---

### Post by man.life on 2005-05-25
Muine works.
F-Spot doesn't work, it worked before updating mono from bp.
Beagle doesn't work, but I have a Breezy installation and it doesn't work anyway...

---

### Post by dlpfmVfH on 2005-05-25
installed beagle with the use of the howto's and it's giving me this message
when I start beagled

```
Unhandled Exception: System.UnauthorizedAccessException: Access to the path "/home/aboe/.beagle/Log/2005-05-25-14-40-24-Beagle" is denied.
in [0x00224] (at /home/jdong/dev/mono-1.1.7/mcs/class/corlib/System.IO/FileStream.cs:207) System.IO.FileStream:.ctor (System.String name, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean isAsync, Boolean anonymous)
in [0x0000d] (at /home/jdong/dev/mono-1.1.7/mcs/class/corlib/System.IO/FileStream.cs:116) System.IO.FileStream:.ctor (System.String name, FileMode mode, FileAccess access, FileShare share)
in (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare)
in <0x00138> Beagle.Util.Logger:LogToFile (System.String path, System.String name, Boolean foreground_mode)
in <0x0029b> Beagle.Daemon.BeagleDaemon:Main (System.String[] args)
Beagle Daemon exited with errors.  See ~/.beagle/Log/current-Beagle for more details.

```

had to chmod .beagle first before

can somebody help??

Blam gave the same error the first time, just ran it from console, and it works :roll: 

muine works here too 

f-spot runs and I can see some pictures, but I don't have a camera...

tom-boy works spell-checking causes a reload, but then everythings ok

running hoary,

---

### Post by Fab on 2005-05-25
[QUOTE=jdong]I was just talking to tseng (Mono maintainer for Ubuntu), who was very upset about the Mono backport (1.1.7) in Hoary Backports. The gist of the conversation was that Mono has switched infrastructure, which causes most of **Hoary Universe's mono-dependent packages to be BROKEN.**

Please test mono apps in Hoary, and tell me if any aren't working. I know blam has refreshing issues. These need to be backported ASAP.[/QUOTE]
 beagle works very well for me...
i use the backports version of beagle and mono
only thing that took long was the indexing (i used the option to index the whole system in one sweep with high priority, some hundred thousand files ;))
i really like it so far though :)

---

### Post by dlpfmVfH on 2005-05-25
how did you get beagled to work??
cause I can't launch beagled

nevermind, did a reinstall and suddenly it works.. ](*,)

---

### Post by man.life on 2005-05-25
How did you do it? I've followed the guide at beaglewiki and this is what I'm getting:

```

05-05-25 16.45.24.44 13362 Beagle INFO: Starting Beagle Daemon (version 0.0.9)
05-05-25 16.45.24.66 13362 Beagle INFO: Attempting to replace another beagled.
05-05-25 16.45.24.66 13362 Beagle INFO: Building Remote Control Proxy
05-05-25 16.45.24.66 13362 Beagle INFO: Sending Shutdown
05-05-25 16.45.27.03 13362 Beagle ERROR: Caught exception while instantiating Files backend
05-05-25 16.45.27.05 13362 Beagle ERROR: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.TypeInitializationException: An exception was thrown by the type initializer for Beagle.Util.Inotify ---> System.DllNotFoundException: libMonoPosixHelper.so
in (wrapper managed-to-native) Mono.Posix.Syscall:map_Mono_Posix_OpenFlags (Mono.Posix.OpenFlags)
in [0x00014] (at /home/jdong/dev/mono-1.1.7/mcs/class/Mono.Posix/Mono.Posix/Syscall.cs:174) Mono.Posix.Syscall:open (System.String pathname, OpenFlags flags)
in <0x00105> Beagle.Util.Inotify:.cctor ()--- End of inner exception stack trace ---

in <0x00000> <unknown method>
in <0x00011> Beagle.Daemon.FileSystemQueryable.FileSystemQueryable:BuildFileAttributesStore (System.String index_fingerprint)
in <0x000e1> Beagle.Daemon.LuceneQueryable:.ctor (System.String index_name)
in <0x0000f> Beagle.Daemon.FileSystemQueryable.FileSystemQueryable:.ctor ()
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in [0x00044] (at /home/jdong/dev/mono-1.1.7/mcs/class/corlib/System.Reflection/MonoMethod.cs:336) System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)--- End of inner exception stack trace ---

in [0x0006b] (at /home/jdong/dev/mono-1.1.7/mcs/class/corlib/System.Reflection/MonoMethod.cs:342) System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in [0x00007] (at /home/jdong/dev/mono-1.1.7/mcs/class/corlib/System.Reflection/MonoMethod.cs:347) System.Reflection.MonoCMethod:Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in [0x00018] (at /home/jdong/dev/mono-1.1.7/mcs/class/corlib/System.Reflection/ConstructorInfo.cs:62) System.Reflection.ConstructorInfo:Invoke (System.Object[] parameters)
in [0x00091] (at /home/jdong/dev/mono-1.1.7/mcs/class/corlib/System/Activator.cs:260) System.Activator:CreateInstance (System.Type type, Boolean nonPublic)
in [0x00002] (at /home/jdong/dev/mono-1.1.7/mcs/class/corlib/System/Activator.cs:143) System.Activator:CreateInstance (System.Type type)
in <0x00188> Beagle.Daemon.QueryDriver:ScanAssembly (System.Reflection.Assembly assembly)
05-05-25 16.45.27.10 13362 Beagle INFO: Loaded 124 records from /home/alex/.beagle/LauncherIndex/FileAttributesStore.db in 0,005s
05-05-25 16.45.27.71 13362 Beagle INFO: Starting Evolution mail backend
05-05-25 16.45.27.72 13362 Beagle INFO: Starting launcher backend
05-05-25 16.45.27.72 13362 Beagle INFO: Starting Evolution mail backend
05-05-25 16.45.27.72 13362 Beagle WARN: Evolution mail store not found, watching for it.
05-05-25 16.45.28.04 13362 Beagle INFO: Launcher backend worker thread done in ,32s
05-05-25 16.45.28.06 13362 Beagle WARN: Could not open Evolution addressbook.  Addressbook searching is disabled.

```

---

### Post by dlpfmVfH on 2005-05-25
did not use beaglewiki:
from boinka: sudo apt-get install mono libgtk-cil automake1.8 libmono-dev mono-gac cvs linux-source-2.6.10 libncurses5-dev kernel-package libtool libgtksourceview-cil libgecko-cil mozilla-dev build-essential libgnomeui-dev libxss-dev gtk-doc-tools gtk-sharp-gapi sqlite


and :

[http://beaglewiki.org/index.php/UbuntuInstall](http://beaglewiki.org/index.php/UbuntuInstall)

hope it helps...

---

### Post by tmowerman on 2005-05-25
I had the file searching crash on beagle, but I found a forum post which I have now lost the url too.  Anyway, the solution was to install libgnomeui-dev

[http://beaglewiki.org/index.php/UbuntuInstall](http://beaglewiki.org/index.php/UbuntuInstall)

It has been added there in the list of packages to install before beagle.  Now Beagel does not crash.  I have no idea why this works, I thought the dev files were just used on compilation, but then I don't know anything really.

---

### Post by infinito on 2005-05-25
For me, using Hoary Backports...

- Beagle works. Used this to make it work: [http://infinito.f2o.org/blog/?p=28](http://infinito.f2o.org/blog/?p=28)

- Tomboy works.

- Monodevelop seems to work (not tried too much)

- F-Spot doesn't work. Got his message on launch:
```
infinito@soho:~$ f-spot

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Object:__icall_wrapper_mono_struct_delete_old (intptr,intptr)
in (wrapper managed-to-native) Gtk.StockManager:gtk_stock_lookup (string,Gtk.StockItem&)
in <0x00017> Gtk.StockManager:Lookup (System.String stock_id, Gtk.StockItem item)
in <0x00048> GtkUtil:MakeToolbarToggleButton (Gtk.Toolbar toolbar, System.String stock_id, System.EventHandler e)
in <0x001cb> MainWindow:.ctor (.Db db)
in <0x00134> Driver:Main (System.String[] args)

```

Hope this help!

---

### Post by man.life on 2005-05-25
Thank you for that HOWTO, infinito.  :) 

Now,

Beagle works.
F-Spot doesn't work (same error as above).
Muine works.

---

### Post by perdix on 2005-05-25
Hoary's f-spot doesn't work with the backported mono.
When I start it from the foot-menu it displays an empty all-grey window, when I start it from a terminal it throws the following exception:

```
Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Object:__icall_wrapper_mono_struct_delete_old (intptr,intptr)
in (wrapper managed-to-native) Gtk.StockManager:gtk_stock_lookup (string,Gtk.StockItem&)
in <0x00017> Gtk.StockManager:Lookup (System.String stock_id, Gtk.StockItem item)
in <0x0004b> GtkUtil:MakeToolbarButton (Gtk.Toolbar toolbar, System.String stock_id, System.EventHandler e)
in <0x00177> MainWindow:.ctor (.Db db)
in <0x00134> Driver:Main (System.String[] args)

```

The good news: blam, muine, monodevelop are all working fine for me.

---

### Post by jdong on 2005-05-25
[QUOTE=infinito]For me, using Hoary Backports...

- Beagle works. Used this to make it work: [http://infinito.f2o.org/blog/?p=28]("http://infinito.f2o.org/blog/?p=28")

- Tomboy works.

- Monodevelop seems to work (not tried too much)

- F-Spot doesn't work. Got his message on launch:
```
infinito@soho:~$ f-spot

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Object:__icall_wrapper_mono_struct_delete_old (intptr,intptr)
in (wrapper managed-to-native) Gtk.StockManager:gtk_stock_lookup (string,Gtk.StockItem&)
in <0x00017> Gtk.StockManager:Lookup (System.String stock_id, Gtk.StockItem item)
in <0x00048> GtkUtil:MakeToolbarToggleButton (Gtk.Toolbar toolbar, System.String stock_id, System.EventHandler e)
in <0x001cb> MainWindow:.ctor (.Db db)
in <0x00134> Driver:Main (System.String[] args)

```

Hope this help![/QUOTE]

This is funny... f-spot works fine on my system. can you issue **dpkg -s f-spot** for me?

---

### Post by man.life on 2005-05-25
As I'm having the same problem (exactly same output when starting f-spot), here you have it:

dpkg -s f-spot

```

Package: f-spot
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 1940
Maintainer: Ond&#345;ej Surý <ondrej@debian.org>
Architecture: i386
Version: 0.0.12-0ubuntu1
Depends: libc6 (>= 2.3.2.ds1-4), libjpeg62, libsqlite0 (>= 2.8.15), mono-jit (>= 1.0.5) | mono-mint (>= 1.0.5), libexif10, libgconf-cil (>= 1.0), libglade-cil (>= 1.0), libglib-cil (>= 1.0), libglib2.0-0 (>= 2.6.0), libgnome-cil (>= 1.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgtk-cil (>= 1.0), libgtk2.0-0 (>= 2.6.0), liblcms1 (>= 1.08-1), mono-assemblies-base (>= 1.0), libgphoto2-2 (>= 2.1.4), libexif10 (>= 0.5.1)
Description: personal photo management application
 F-Spot is meant to be an easy-to-use photo management
 application.  It allows for importing of your existing
 photo collections, tagging photos with identifiers,
 as well as doing simple edits of photos (e.g. rotating).
 .
 This application is still in its early stage of development.

```

---

### Post by infinito on 2005-05-25
```
infinito@soho:~$ dpkg -s f-spot
Package: f-spot
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 1940
Maintainer: Ond&#345;ej Surý <ondrej@debian.org>
Architecture: i386
Version: 0.0.12-0ubuntu1
Depends: libc6 (>= 2.3.2.ds1-4), libjpeg62, libsqlite0 (>= 2.8.15), mono-jit (>= 1.0.5) | mono-mint (>= 1.0.5), libexif10, libgconf-cil (>= 1.0), libglade-cil (>= 1.0), libglib-cil (>= 1.0), libglib2.0-0 (>= 2.6.0), libgnome-cil (>= 1.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgtk-cil (>= 1.0), libgtk2.0-0 (>= 2.6.0), liblcms1 (>= 1.08-1), mono-assemblies-base (>= 1.0), libgphoto2-2 (>= 2.1.4), libexif10 (>= 0.5.1)
Description: personal photo management application
 F-Spot is meant to be an easy-to-use photo management
 application.  It allows for importing of your existing
 photo collections, tagging photos with identifiers,
 as well as doing simple edits of photos (e.g. rotating).
 .
 This application is still in its early stage of development.
```

---

### Post by jdong on 2005-05-25
A bit of googling suggests this may be due to you removing a picture from your home directory without first deleting it from F-spot.
 
Can you guys remove the ~/.gnome2/f-spot/photos.db file (THIS WILL DELETE F-SPOT's PHOTO DATABASE), and see if the error persists?

---

### Post by infinito on 2005-05-26
[QUOTE=jdong]A bit of googling suggests this may be due to you removing a picture from your home directory without first deleting it from F-spot.
 
Can you guys remove the ~/.gnome2/f-spot/photos.db file (THIS WILL DELETE F-SPOT's PHOTO DATABASE), and see if the error persists?[/QUOTE]
Deleted ~/.gnome2/f-spot/ anf the problem's still there.

---

### Post by Majlo on 2005-05-26
I complile Blam 1.8 from source ..
It worked fine with mono from backport.

Blam 1.8

1.8.0:
------
*** Don't automatically refresh on start (micke)**
* Don't save window size if maximized (Peter Rother, micke)
* Replaced C implementation of eggtrayicon with C# version (Markus Jonsson)
* Fixed Livejournal feeds (Heath Harrelson)
* Support for Atom, YAY (Heath Harrelson)
*** Fixed problem where it didn't update on Mono >= 1.1.7 (Peter Johanson)**
* Fixed leak in HTML widget wrapper (micke)
* Changed the menu entry for application menu to be Blam Feed Reader (micke)
* Fixed a crash when running blam a second time (micke)
* New translations (it, rw)
* Updated translations 
  (de, no, nb, en_CA, cs, en_GB, fi, sq, nl, pt_BR, sv, ca, hu)

I dont have problem with refresh

---

### Post by man.life on 2005-05-26
Same here, deleting ~/.gnome2/f-spot/photos.db does nothing...

---

### Post by xmlblog on 2005-05-26
Beagle, F-Spot, Muine, Tomboy all working for me.


Package: f-spot
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 1940
Maintainer: Ond&#345;ej Surý <ondrej@debian.org>
Architecture: i386
Version: 0.0.12-0ubuntu1
Depends: libc6 (>= 2.3.2.ds1-4), libjpeg62, libsqlite0 (>= 2.8.15), mono-jit (>= 1.0.5) | mono-mint (>= 1.0.5), libexif10, libgconf-cil (>= 1.0), libglade-cil (>= 1.0), libglib-cil (>= 1.0), libglib2.0-0 (>= 2.6.0), libgnome-cil (>= 1.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgtk-cil (>= 1.0), libgtk2.0-0 (>= 2.6.0), liblcms1 (>= 1.08-1), mono-assemblies-base (>= 1.0), libgphoto2-2 (>= 2.1.4), libexif10 (>= 0.5.1)
Description: personal photo management application
 F-Spot is meant to be an easy-to-use photo management
 application.  It allows for importing of your existing
 photo collections, tagging photos with identifiers,
 as well as doing simple edits of photos (e.g. rotating).
 .
 This application is still in its early stage of development.

---

### Post by perdix on 2005-05-26
[QUOTE=jdong]This is funny... f-spot works fine on my system. can you issue **dpkg -s f-spot** for me?[/QUOTE]

Sure:
> mkhl@mukade:~$ dpkg -s f-spot
Package: f-spot
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 1940
Maintainer: Ond&#345;ej Surý <ondrej@debian.org>
Architecture: i386
Version: 0.0.12-0ubuntu1
Depends: libc6 (>= 2.3.2.ds1-4), libjpeg62, libsqlite0 (>= 2.8.15), mono-jit (>= 1.0.5) | mono-mint (>= 1.0.5), libexif10, libgconf-cil (>= 1.0), libglade-cil (>= 1.0), libglib-cil (>= 1.0), libglib2.0-0 (>= 2.6.0), libgnome-cil (>= 1.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgtk-cil (>= 1.0), libgtk2.0-0 (>= 2.6.0), liblcms1 (>= 1.08-1), mono-assemblies-base (>= 1.0), libgphoto2-2 (>= 2.1.4), libexif10 (>= 0.5.1)
Description: personal photo management application
 F-Spot is meant to be an easy-to-use photo management
 application.  It allows for importing of your existing
 photo collections, tagging photos with identifiers,
 as well as doing simple edits of photos (e.g. rotating).
 .
 This application is still in its early stage of development.



Removing ~/.gnome2/f-spot/ doesn't change a thing unfortunately.  I can't recompile (dpkg-buildpackage) f-spot from the hoary sources either.

---

### Post by A-star on 2005-05-27
I compiled monotheka from source and it works fine with mono 1.1.7.
Even wrote a howto for it -> see the howto forum.

---

### Post by infinito on 2005-05-31
f-spot problem just happens when trying to run it under locales different from English.

Please everyone havign problems with f-spot, try this:
```
$ LANG=C f-spot
```
It did work for me...

PD: Pointed out by: [http://ubuntuforums.org/showthread.php?t=38432](http://ubuntuforums.org/showthread.php?t=38432)

---

### Post by man.life on 2005-05-31
That worked for me too. So... does anyone know how to edit /usr/share/applications/f-spot.desktop so that it starts automatically with the "LANG=C" parameter? I've tried:

LANG=C f-spot
`LANG=C f-spot`
f-spot LANG=C

but it won't work. I don't have a clue about .desktop files... could someone help me?

---

### Post by joseph.bourez@free.fr on 2005-05-31
[QUOTE=infinito]For me, using Hoary Backports...

- Beagle works. Used this to make it work: [http://infinito.f2o.org/blog/?p=28](http://infinito.f2o.org/blog/?p=28)

- Tomboy works.

- Monodevelop seems to work (not tried too much)

- F-Spot doesn't work. Got his message on launch:
```
infinito@soho:~$ f-spot

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Object:__icall_wrapper_mono_struct_delete_old (intptr,intptr)
in (wrapper managed-to-native) Gtk.StockManager:gtk_stock_lookup (string,Gtk.StockItem&)
in <0x00017> Gtk.StockManager:Lookup (System.String stock_id, Gtk.StockItem item)
in <0x00048> GtkUtil:MakeToolbarToggleButton (Gtk.Toolbar toolbar, System.String stock_id, System.EventHandler e)
in <0x001cb> MainWindow:.ctor (.Db db)
in <0x00134> Driver:Main (System.String[] args)

```

Hope this help![/QUOTE]
 same message for me when i try to run f-spot

---

### Post by joseph.bourez@free.fr on 2005-05-31
[QUOTE=joseph.bourez@free.fr]same message for me when i try to run f-spot[/QUOTE]
 it works when i try with LANG=C f-spot. (I'am a french user)
Muine works without problem

---

### Post by MaX on 2005-06-01
Blam won't work for me I get:

```
Unhandled Exception: System.DllNotFoundException: gdk-x11-2.0
in <0x00046> (wrapper managed-to-native) Egg.TrayIcon:gdk_x11_display_get_xdispl ay (intptr)
in <0x00049> Egg.TrayIcon:OnRealized ()
in <0x0003b> Gtk.Widget:realized_cb (intptr)
in <0x00027> (wrapper native-to-managed) Gtk.Widget:realized_cb (intptr)
in (unmanaged) 0x4c7fffad
in <0x00004> (wrapper managed-to-native) Gtk.Widget:gtk_widget_show_all (intptr)
in <0x00017> Gtk.Widget:ShowAll ()
in <0x0000d> Imendio.Blam.TrayIcon:Show ()
in <0x0007c> Imendio.Blam.Application:UpdateTotalNumberOfUnread ()
in <0x00048> Imendio.Blam.Application:ChannelRefreshFinishedCb (Imendio.Blam.Cha nnel)
in <0x0003d> (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_Chan nel (Imendio.Blam.Channel)
in <0x00018> Imendio.Blam.MainloopEmitter:TimeoutEmit ()
in <0x00039> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x0002b> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0x4c769ab2
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x00007> Gnome.Program:Run ()
in <0x00045> Imendio.Blam.Application:Main (string[])

```

---

### Post by manstrike on 2005-06-01
beagle works for me

however i'm not shore if mono-utils is all ok
when trying the included monograph I get this output

/usr/bin/monograph: error: /usr/bin/.libs/monograph does not exist
This script is just a wrapper for monograph.
See the libtool documentation for more information.

I got graphviz and libtool installed

---

### Post by ametade on 2005-06-01
Beagle is working fine (on ReiserFS). F-Spot is working too although I don't have a camera. I'm using tomboy 0.3.2 without problems. Muine works but uses 100% CPU...

---

### Post by scoon on 2005-06-05
Hey there, 

monodevelop does NOT work for me.  It starts up fine but does not show any files that I open.  If i start from a console this is all i get: 

```
2005-06-05 08:10:46,076 [-1478653056] INFO  MonoDevelop.Services.ILoggingService [(null)] - Reading /home/scoon/.config/MonoDevelop/CodeCompletionData/mscorlib_1.0.5000.0_b77a5c561934e089.pidb
2005-06-05 08:10:46,176 [-1478653056] INFO  MonoDevelop.Services.ILoggingService [(null)] - WARNING Could not find stock Icons.16x16.FindPrevIcon
2005-06-05 08:10:46,186 [-1478653056] INFO  MonoDevelop.Services.ILoggingService [(null)] - WARNING Could not find stock gtk-stop
2005-06-05 08:10:46,207 [-1478653056] INFO  MonoDevelop.Services.ILoggingService [(null)] - Creating DefaultWorkbench
2005-06-05 08:10:59,720 [-1478653056] INFO  MonoDevelop.Services.ILoggingService [(null)] - WARNING Could not find stock gtk-open

```

Any ideas ?

regards, 

scoon

---

### Post by m3x on 2005-06-05
Problems with beagle, f-spot and tomboy on ppc.

I have installed all the mono files and dependencies from the backports.ubuntu...

Now I get always this message:

beagled start:

The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the `/usr/lib/mono/1.0/mscorlib.dll' directory.

same messages for f-spot and tomboy too. Tried to do a link, but then mono tells me that it is too old ...

Any hints?

Regards,

m3x

---

### Post by Slo Mo Snail on 2005-06-05
[QUOTE=m3x]Problems with beagle, f-spot and tomboy on ppc.

I have installed all the mono files and dependencies from the backports.ubuntu...

Now I get always this message:

beagled start:

The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the `/usr/lib/mono/1.0/mscorlib.dll' directory.

same messages for f-spot and tomboy too. Tried to do a link, but then mono tells me that it is too old ...

Any hints?

Regards,

m3x[/QUOTE]

Try uninstalling mono and then reinstalling it... mscorlib.dll should be in that directory then... at least mono-assemblies-base installs the dll there for me...

---

### Post by m3x on 2005-06-05
Hi,

Thank you very much! Reinstalling helped :-) But solving a problem generates a new problem ;-)

muine runs fine now.

best wants gecko-sharp but libgecko-cil is installed. Yes, I tried a reinstall too ;-)

<output>
best

** (/usr/lib/beagle/Best.exe:12250): WARNING **: The following assembly referenced from /usr/lib/beagle/Tiles.dll could not be loaded:
     Assembly:   gecko-sharp    (assemblyref_index=8)
     Version:    1.0.0.0
     Public Key: ccf7d78a55e9f021
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (/usr/lib/beagle/Best.exe:12250): WARNING **: The class Gecko.WebControl could not be loaded, used in /usr/lib/beagle/Tiles.dll (token 0x0100003c)

** ERROR **: file class.c: line 2119 (mono_class_setup_parent): should not be reached
aborting...
Aborted
</output>

What could it be?

Regards,

m3x

---

### Post by jdong on 2005-06-05
Beagle must be installed according to [http://beaglewiki.org/index.php/UbuntuInstall](http://beaglewiki.org/index.php/UbuntuInstall)

Not all deps are auto-installed.

---

### Post by scoon on 2005-06-05
Yeah, that was the problem i was having with monodevelop, not all of the monodoc deps got installed w/ it. 

regards, 

scoon

---

### Post by webwurst on 2005-06-05
I'm running Mono-1.1.7

Beagle works fine for me, but f-spot throws an error:

> ** (f-spot:21179): WARNING **: Missing method Add in assembly /usr/lib/f-spot/f-spot.exe, type StockManager

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in <0x00090> Driver:Main (System.String[] args)

[**update**]:
I installed f-spot again on a fresh-ubuntu-installation and there it works..

---

### Post by perdix on 2005-06-10
[QUOTE=man.life]That worked for me too. So... does anyone know how to edit /usr/share/applications/f-spot.desktop so that it starts automatically with the "LANG=C" parameter? I've tried:

LANG=C f-spot
`LANG=C f-spot`
f-spot LANG=C

but it won't work. I don't have a clue about .desktop files... could someone help me?[/QUOTE]

That would be
```
env LANG=C f-spot
```

---

### Post by Wolki on 2005-06-16
Hi!

I just updated using the backports repos. Unfortunately the new Mono breaks Muine's plugins, especially the cuckoo plugin which is quite essential to me.

Here's the error message:

```
wolki@client418:~/.gnome2/muine/plugins $ muine
Fehler beim Laden des Plugins Cuckoo.dll: Object type cannot be converted to target type.
Parameter name: val
Speicherzugriffsfehler
```

and here's the plugin page: [http://www.public.asu.edu/~bnickel/muine-cuckoo/](http://www.public.asu.edu/~bnickel/muine-cuckoo/)

now, trying to go back to the hoary mono seems to be a big effort since i have to do it manually for each package :-/ is there a smarter way, or - even better - a fix for this problem so i can continue to use the new Mono?

wolki

---

### Post by wolovids on 2005-06-16
Slightly offtopic, but is the new Muine (0.8.3) using Gstreamer or Xine as it's backend?  It supposedly switched to Gstreamer as default and was just wondering what it was compiled with?  

Thanks!

---

### Post by NiceGuyUK on 2005-06-17
So far tested Beagle/Best, Monodevelop, some apps I wrote myself  ;-) F-Spot and bunch of other apps I suspect are in Mono (not always easy to tell!), and haven't found any major problems.

---

### Post by moolett on 2005-06-17
[QUOTE=jdong]I was just talking to tseng (Mono maintainer for Ubuntu), who was very upset about the Mono backport (1.1.7) in Hoary Backports. The gist of the conversation was that Mono has switched infrastructure, which causes most of **Hoary Universe's mono-dependent packages to be BROKEN.**

Please test mono apps in Hoary, and tell me if any aren't working. I know blam has refreshing issues. These need to be backported ASAP.[/QUOTE]
 I have installed kubuntu and i am in the process of installing mono. It is a very exiciting development for me. I hope to keep you posted with any updates. I see mono and kubuntu as a serious step for man kind...
I hope to contribute knowledge at some point.

---

### Post by malmjako on 2005-07-09
I'm trying out Beagle. Seems to be working mostly fine. It finds  files, mail and instant messages, but ***no address book entries***. It just won't happen. I don't get any error messages at all about it in the log files though... The libebook links I think are in order. I have the following:
```
/usr/lib$ ls -l libebook-1.2.*
-rw-r--r--  1 root root   1765 2005-03-17 23:45 libebook-1.2.la
lrwxrwxrwx  1 root root     21 2005-07-09 22:56 libebook-1.2.so -> libebook-1.2.so.3.1.1
lrwxrwxrwx  1 root root     24 2005-07-09 22:57 libebook-1.2.so.0 -> /usr/lib/libebook-1.2.so
lrwxrwxrwx  1 root root     21 2005-06-09 22:05 libebook-1.2.so.3 -> libebook-1.2.so.3.1.1
-rw-r--r--  1 root root 203888 2005-03-17 23:46 libebook-1.2.so.3.1.1
```
I just can't figure out what more is needed. beagle-index-info reports (layout changed...):
```
$ beagle-index-info
Index information:

Name: Files, Count: 18007
Name: IMLog, Count: 2
Name: Blam, Count: 315
Name: Liferea, Count: 626
Name: Mail, Count: 921
Name: Launcher, Count: 302
Name: Tomboy, Count: 2
Name: IndexingService, Count: 0
Name: Google, Count: -1
Name: EvolutionDataServer, Count: 0
Name: NetworkedBeagle, Count: -1
```
EvolutionDataServer has no indexed entries. I've started up beagled with --allow-backend EvolutionDataServer and BEAGLE_EXERCISE_THE_DOG=1 set, but it makes no difference.

Has anyone else had this problem? Any solutions?

---

### Post by suoko on 2005-08-03
[QUOTE=malmjako]I'm trying out Beagle. Seems to be working mostly fine. It finds  files, mail and instant messages, but ***no address book entries***. It just won't happen. I don't get any error messages at all about it in the log files though... The libebook links I think are in order. I have the following:
```
/usr/lib$ ls -l libebook-1.2.*
-rw-r--r--  1 root root   1765 2005-03-17 23:45 libebook-1.2.la
lrwxrwxrwx  1 root root     21 2005-07-09 22:56 libebook-1.2.so -> libebook-1.2.so.3.1.1
lrwxrwxrwx  1 root root     24 2005-07-09 22:57 libebook-1.2.so.0 -> /usr/lib/libebook-1.2.so
lrwxrwxrwx  1 root root     21 2005-06-09 22:05 libebook-1.2.so.3 -> libebook-1.2.so.3.1.1
-rw-r--r--  1 root root 203888 2005-03-17 23:46 libebook-1.2.so.3.1.1
```
I just can't figure out what more is needed. beagle-index-info reports (layout changed...):
```
$ beagle-index-info
Index information:

Name: Files, Count: 18007
Name: IMLog, Count: 2
Name: Blam, Count: 315
Name: Liferea, Count: 626
Name: Mail, Count: 921
Name: Launcher, Count: 302
Name: Tomboy, Count: 2
Name: IndexingService, Count: 0
Name: Google, Count: -1
Name: EvolutionDataServer, Count: 0
Name: NetworkedBeagle, Count: -1
```
EvolutionDataServer has no indexed entries. I've started up beagled with --allow-backend EvolutionDataServer and BEAGLE_EXERCISE_THE_DOG=1 set, but it makes no difference.

Has anyone else had this problem? Any solutions?[/QUOTE]
 Hi,

I'm trying to run beagle but beagled exits with following problem:

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Beagle.Util.Inotify ---> System.DllNotFoundException: libMonoPosixHelper.so
in (wrapper managed-to-native) Mono.Posix.Syscall:map_Mono_Posix_OpenFlags (Mono.Posix.OpenFlags)
in [0x00014] (at /home/jdong/dev/mono-1.1.7/mcs/class/Mono.Posix/Mono.Posix/Syscall.cs:174) Mono.Posix.Syscall:open (System.String pathname, OpenFlags flags)
in <0x00101> Beagle.Util.Inotify:.cctor ()--- End of inner exception stack trace
 ---

in (unmanaged) 0x80c630f
in <0x00142> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x0002b> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0x4b8c9a02
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0052e> Beagle.Daemon.BeagleDaemon:Main (string[])

While Muine and f-spot are working fine.
I have tried both with my custom kernel and the default ubuntu kernel (in case the problem were inotify).
I enabled the user_xattr option in fstab but only for my root partition (which is reiserfs).
I couldn't enable it for my home partition since it's xfs.
Is that the problem?
 (Beagle is installed through ubuntu backports)

---

### Post by malmjako on 2005-08-08
[QUOTE=suoko]I enabled the user_xattr option in fstab but only for my root partition (which is reiserfs).
I couldn't enable it for my home partition since it's xfs.
Is that the problem?[/QUOTE]
I would think so. From what I've been able to figure out, Beagle MUST have user_xattr set for the partition which hosts your home directory.

---

