---
title: "Ubuntu64 raw photo import problem"
date: 2007-01-21
forum: The Cafe
---

### Post by dannesthlm on 2007-01-21
Hi

My new Canon EOS400D, is now (after a little bit of editing) working with my distro. This means my jpg's now are imported to my computer. My problem is that raw photos (*.cr2) are not imported at all, after a search on the net, ie it's not recogniced by the importing tool.

After a search a found the solution to use an import function in a program called "F-spot". This program seems to recognice the raw-pictures on the camera, but when i start to import, it shows me a strange error, 'Error scanning WMF file'. This seems pretty odd as it should not be any wmf-files involved in the operation at all(?). The program recognices the file as an cr2 in the import window. 

The full expanded messages looks like this:

Error scanning WMF file

  at Gdk.PixbufLoader.Close () [0x00000] 
  at Gdk.PixbufLoader.InitFromStream (System.IO.Stream stream) [0x00000] 
  at Gdk.PixbufLoader..ctor (System.IO.Stream stream) [0x00000] 
  at Gdk.Pixbuf..ctor (System.IO.Stream stream) [0x00000] 
  at GPhotoCamera.GetPreviewPixbuf (.GPhotoCameraFile camfile) [0x00000] 
  at FSpot.CameraFileSelectionDialog.GetPreviews () [0x00000] 
  at FSpot.CameraFileSelectionDialog.CreateInterface () [0x00000] 
  at FSpot.CameraFileSelectionDialog.Run () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
  at ImportCommand.set_Source (.SourceItem value) [0x00000] 
  at ImportCommand+SourceMenu.HandleActivated (System.Object sender, System.EventArgs args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr gch) [0x00000] 
  at (wrapper native-to-managed) GLib.Signal:voidObjectCallback (intptr,intptr)
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) Gtk.Dialog:gtk_dialog_run (intptr)
  at Gtk.Dialog.Run () [0x00000] 
  at ImportCommand.ImportFromFile (.PhotoStore store, System.String path) [0x00000] 
  at MainWindow.HandleImportCommand (System.Object sender, System.EventArgs e) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr gch) [0x00000] 
  at (wrapper native-to-managed) GLib.Signal:voidObjectCallback (intptr,intptr)
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) Gtk.Application:gtk_main ()
  at Gtk.Application.Run () [0x00000] 
  at Gnome.Program.Run () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 1.1.4322.2032

Assembly Version Information:

libgphoto2-sharp (1.0.2476.10545)
FlickrNet (1.1.0.0)
google-sharp (0.1.0.0)
gconf-sharp (2.16.0.0)
pango-sharp (2.10.0.0)
SemWeb (0.7.1.0)
glade-sharp (2.10.0.0)
gtkhtml-sharp (2.16.0.0)
System.Data (1.0.5000.0)
Mono.Data.SqliteClient (1.0.5000.0)
gdk-sharp (2.10.0.0)
gnome-vfs-sharp (2.16.0.0)
dbus-sharp (0.60.0.0)
System (1.0.5000.0)
Mono.Posix (1.0.5000.0)
atk-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gnome-sharp (2.16.0.0)
f-spot (0.2.1.0)
mscorlib (1.0.5000.0)

Platform Information: Linux 2.6.17-10-generic x86_64 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"


Hope someone can come up with a solution for me, so i can start importing my raw's in some way at least.

---

### Post by ubuntwinkel on 2007-02-26
This is late to respond, but please submit your post as a bug to [bugzilla.gnome.org]("http://bugzilla.gnome.org/simple-bug-guide.cgi").  

Also, as I am seeking a cure for this (for my 350D), I will post back as soon as I get it :)  figured out.  I will post back with the details even if I do not :( get it figured out.

---

### Post by bpmorris on 2007-02-26
Definatly please post a solution as I have a 400D and at the moment copy the raw images locally then edit with Bibble. I would love to have a more automated import solution.

Cheers

---

### Post by ubuntwinkel on 2007-02-27
OK, first the quick and dirty...

**gthumb** seems to be the default digital camera importer in ubuntu, and it doesn't immediately recognize canon cr2 images (maybe it can with tweaking, upgrading, etc, maybe more on that later...)

**gtkam** (my version is 0.1.13) will recognize .cr2 files but will not generate thumbnails for them.  It will simply list them by name.  This may be different if you shoot in RAW+JPG mode--I've never done that yet, so I don't know.  Typically, I don't examine the thumbnails, I just import everything and delete later.  And I never use the importer to delete from the camera after importing--takes too long.  After importing, I just disconnect the camera, select _review_, then _delete_, then _delete all_.  The camera wipes them all out in about 5 seconds.  It sometimes takes the importers that long to delete *per image!* 

gtkam may not be instlled by default in unbuntu.  I have installed lots of extra stuff, and gtkam may have been one.  I used it in the un-ubuntuud past, when I used a mandriva system.  And I installed it then for the same reason: to access RAW images.  But then I stopped using RAW.  However, at the time I seem to remember doing lots of searching for a prettier interface that did RAW... and never found one.  That was about a year ago, so I'll search some more (b/c things change fast).

But, I think gtkam may be the best one available currently.  It is rather down and dirty itself; for example, once it connects to the Canon, it will show nothing.  One must click through the several levels of folders on the camera's filesystem to reach the folder containing the photos.  Not too tedious, but not a take-me-by-the-hand delight, either.  

On my Canon, the folders, as viewed in gtkam look like this:
[INDENT]>Canon EOS 350D (PTP mode)
[INDENT]>store_00000001
[INDENT]>DCIM
[INDENT]113CANON
114CANON
115CANON
116CANON
117CANON
118CANON
119CANON
120CANON
121CANON
122CANON
...
128CANON
[/INDENT][/INDENT][/INDENT][/INDENT]

The latest photos are in the last folder, '128CANON' in my example above.

I download off the camera (I don't use a card reader) and gtkam does so lickity-split compared to other importers I've used.  

That's the quick (sort of) and dirty.  Hope this helps.  Will try to be back soon with more.

---

### Post by ubuntwinkel on 2007-02-27
digiKam does RAW, too.  And does it nice and pretty, too.  But I have not tried to make it work solely as an image importer.  It is an image album manager with an image importer integrated into it.  There's probably a command line option to run the importer alone, but it's late...

I have, however, found a secret for changing the default application which is launched when I connect my camera.  I used gconf-editor (version 2.14.0).

At a command line type```
gconf-editor
```if it runs, yay!  If not then do ```
sudo apt-get install gconf-editor
```or do it via synaptic, if you prefer.  Once gconf-editor is installed and running, then...

In the gconf-editor gui, navigate to [INDENT]/desktop[INDENT]/gnome[INDENT]/volume_manager[/INDENT][/INDENT][/INDENT]and in the 'settings window' on the right, highlight *autophoto_command.*  Double clicking the entry will allow you to edit it, which will be something very long (it seemed to me) and ending in, probably, 'gthumb', like *'gnome-volume-manager-gthumb %h'*.  Replace it all with *'gtkam'* just by itself, or if you really want to use digikam (not a bad choice, providing you have **it** installed) then type *'digikam --detect-camera'*, which is, curiously enough, that command I mentioned earlier for running the importer alone.  Nice.  

And those little checkboxes in gconf-editor are REAL easy to check and uncheck.  Be careful where you click.  In fact, be careful about everything you change.  There is no handy back-up to revert to if all goes kaput.  Be careful, and go slowly.

---

### Post by flar on 2007-03-02
for loading RAW images, try ufraw, there's also a plugin for the gimp called gimp-ufraw.  both of these are in the repos

for getting them off your camera, I don't know for Canon.  but for Nikon, I can select either PTP mode or USB mass storage mode on the camera.  when the camera is in USB mass storage mode, RAW can simply be copied to any folder from the camera.  The other option is to get a card reader and do it that way.

---

### Post by Gossie on 2008-06-18
ufraw is great thanks!

it works! ---now I have jpg

thanks and goodbye, Gossie

---

