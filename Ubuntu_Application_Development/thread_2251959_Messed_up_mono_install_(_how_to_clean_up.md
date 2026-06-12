---
title: "Messed up mono install :( how to clean up?"
date: 2014-11-07
forum: Ubuntu Application Development
---

### Post by aikeru on 2014-11-07
So... I think I installed multiple copies of mono and I'm not sure how to clean up. I'm sorry if this is not the best place to ask this question. I didn't think it was appropriate for askubuntu and if there's a better forum kindly point me in the right direction... :)

I am trying to compile monodevelop from source. This was working with mono 3.8, but now I've installed mono 3.10 and it's broken. Way back I had installed 3.2 (from the Ubuntu default apt-get).

The first thing I notice is this:
```
msnead@lt-msnead8:~$ whereis mono
mono: /usr/bin/mono /etc/mono /usr/lib/mono /usr/bin/X11/mono /usr/local/bin/mono.bak /usr/local/etc/mono /usr/local/lib/mono /usr/share/mono /usr/share/man/man1/mono.1.gz

```

Also, when I try to compile monodevelop it gives the sort of errors as though Gtk# wasn't installed or in GAC (ie: "The type `Glib.IIcon' is defined in an assembly that is not referenced.")

I installed gtk-sharp from git/source. When I configure gtk-sharp to compile it says "WARNING: Prefix to use (/usr/local) is not the same as Mono's (/usr)."
I've tried installing gtk-sharp with both prefixes which didn't seem to affect anything.

Also, I've run gacutil -i ... as described here [http://stackoverflow.com/questions/16485826/ubuntu-13-04-how-to-build-monodevelop-4-0-1](http://stackoverflow.com/questions/16485826/ubuntu-13-04-how-to-build-monodevelop-4-0-1) which works in /usr/local/lib/mono/gac but doesn't work in /usr/lib/mono/gac where I seem to have another copy of the gac. 

Run from /usr/local/lib/mono/gac
```

msnead@lt-msnead8:/usr/local/lib/mono/gac$ sudo gacutil -i glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll && sudo gacutil -i atk-sharp/2.12.0.0__35e10195dab3c99f/atk-sharp.dll && sudo gacutil -i gdk-sharp/2.12.0.0__35e10195dab3c99f/gdk-sharp.dll && sudo gacutil -i gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll && sudo gacutil -i glade-sharp/2.12.0.0__35e10195dab3c99f/glade-sharp.dll && sudo gacutil -i pango-sharp/2.12.0.0__35e10195dab3c99f/pango-sharp.dll && sudo gacutil -i gnome-sharp/2.24.0.0__35e10195dab3c99f/gnome-sharp.dll &&  sudo gacutil -i gconf-sharp/2.24.0.0__35e10195dab3c99f/gconf-sharp.dll && sudo gacutil -i gnome-vfs-sharp/2.24.0.0__35e10195dab3c99f/gnome-vfs-sharp.dll
Installed glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll into the gac (/usr/lib/mono/gac)
Installed atk-sharp/2.12.0.0__35e10195dab3c99f/atk-sharp.dll into the gac (/usr/lib/mono/gac)
Installed gdk-sharp/2.12.0.0__35e10195dab3c99f/gdk-sharp.dll into the gac (/usr/lib/mono/gac)
Installed gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll into the gac (/usr/lib/mono/gac)
Installed glade-sharp/2.12.0.0__35e10195dab3c99f/glade-sharp.dll into the gac (/usr/lib/mono/gac)
Installed pango-sharp/2.12.0.0__35e10195dab3c99f/pango-sharp.dll into the gac (/usr/lib/mono/gac)
Installed gnome-sharp/2.24.0.0__35e10195dab3c99f/gnome-sharp.dll into the gac (/usr/lib/mono/gac)
Installed gconf-sharp/2.24.0.0__35e10195dab3c99f/gconf-sharp.dll into the gac (/usr/lib/mono/gac)
Installed gnome-vfs-sharp/2.24.0.0__35e10195dab3c99f/gnome-vfs-sharp.dll into the gac (/usr/lib/mono/gac)

```

Run from /usr/lib/mono/gac
```
msnead@lt-msnead8:/usr/lib/mono/gac$ sudo gacutil -i glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll && sudo gacutil -i atk-sharp/2.12.0.0__35e10195dab3c99f/atk-sharp.dll && sudo gacutil -i gdk-sharp/2.12.0.0__35e10195dab3c99f/gdk-sharp.dll && sudo gacutil -i gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll && sudo gacutil -i glade-sharp/2.12.0.0__35e10195dab3c99f/glade-sharp.dll && sudo gacutil -i pango-sharp/2.12.0.0__35e10195dab3c99f/pango-sharp.dll && sudo gacutil -i gnome-sharp/2.24.0.0__35e10195dab3c99f/gnome-sharp.dll &&  sudo gacutil -i gconf-sharp/2.24.0.0__35e10195dab3c99f/gconf-sharp.dll && sudo gacutil -i gnome-vfs-sharp/2.24.0.0__35e10195dab3c99f/gnome-vfs-sharp.dll
[sudo] password for msnead: 


Unhandled Exception:
System.IO.FileNotFoundException: glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll does not exist
File name: 'glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll'
  at System.IO.File.Copy (System.String sourceFileName, System.String destFileName, Boolean overwrite) [0x00000] in <filename unknown>:0 
  at Mono.Tools.Driver.Copy (System.String source, System.String target, Boolean v) [0x00000] in <filename unknown>:0 
  at Mono.Tools.Driver.Install (Boolean check_refs, System.String name, System.String package, System.String gacdir, System.String link_gacdir, System.String libdir, System.String link_libdir) [0x00000] in <filename unknown>:0 
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.IO.FileNotFoundException: glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll does not exist
File name: 'glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll'
  at System.IO.File.Copy (System.String sourceFileName, System.String destFileName, Boolean overwrite) [0x00000] in <filename unknown>:0 
  at Mono.Tools.Driver.Copy (System.String source, System.String target, Boolean v) [0x00000] in <filename unknown>:0 
  at Mono.Tools.Driver.Install (Boolean check_refs, System.String name, System.String package, System.String gacdir, System.String link_gacdir, System.String libdir, System.String link_libdir) [0x00000] in <filename unknown>:0 
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] in <filename unknown>:0 



```

I did try uninstalling mono to start from scratch. The two things I did to try and do this were to
1) sudo apt-get purge mono-runtime (should remove 3.2 and 3.10 which were installed via ubuntu and mono apt-get repositories, respectively)
2) go to 3.8 folder and make uninstall

The latest installation I ran was to reinstall 3.10 from mono's apt-get repository.

I'm tempted to reinstall Ubuntu, but I'd really like to learn the proper thing to do so I can clean up after myself and I can help others with similar issues.

Thanks!

PS I am on Ubuntu 14.04 64-bit

---

