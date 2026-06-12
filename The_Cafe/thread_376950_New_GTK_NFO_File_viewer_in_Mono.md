---
title: "New GTK NFO File viewer in Mono"
date: 2007-03-05
forum: The Cafe
---

### Post by NiceGuyUK on 2007-03-05
I knocked up a quick NFO file viewer at lunchtime and tidied it up on the train home tonight.  Its now in a condition where I'm brave enough to let other Ubuntu folks give it a try :-)

Not packaged up into a .deb yet, its a source tarball.  I'll aim at nicer packaging when its ready for a wider audience.  Its written in C# under Mono, so you'll need Mono and GTK# at the very least.  Check the README for details

Please use this thread to leave *constructive* feedback.

INSTALL NOTES:
You'll need mono, mono-mcs and gtk-sharp2 packages from the repositories (I'm on Feisty, not tested on Edgy/Dapper).

To compile, change to the source directory (after extracting it) and type :-

```
mcs -pkg:gtk-sharp-2.0 -pkg:glade-sharp-2.0 -out:GNFOView.exe ./gtk-gui/generated.cs MainWindow.cs main.cs
```

USAGE NOTES:
You can pass a filename to open as a command line parameter.  In the viewer, CTRL-O to open a file, CTRL-I to invert the colours, CTRL-Q to quit.  Or use the menus, its up to you.

Thanks guys,

NiceGuyUK

---

### Post by garrison on 2007-12-27
It compiles without error on Gutsy AMD64, thanks.

I have two suggestions:

[LIST]
[*]graceful handling of System.IO.FileNotFoundException
[*]ability to save preferences or last state (inversion, window size)
[/LIST]

---

### Post by garrison on 2007-12-27
> **NiceGuyUK said:**
> ```
mcs -pkg:gtk-sharp-2.0 -pkg:glade-sharp-2.0 -out:GNFOView.exe ./gtk-gui/generated.cs MainWindow.cs main.cs
```

That should read *Main.cs* rather than *main.cs*:

```
mcs -pkg:gtk-sharp-2.0 -pkg:glade-sharp-2.0 -out:GNFOView.exe ./gtk-gui/generated.cs MainWindow.cs Main.cs
```

---

### Post by phrostbyte on 2007-12-27
I can package it for you in a .deb file if you want.

---

### Post by NiceGuyUK on 2007-12-28
> **garrison said:**
> It compiles without error on Gutsy AMD64, thanks.

I have two suggestions:

[LIST]
[*]graceful handling of System.IO.FileNotFoundException
[*]ability to save preferences or last state (inversion, window size)
[/LIST]

I'll try to implement those features, I was looking for something to code this week :-)

---

### Post by NiceGuyUK on 2007-12-28
> **phrostbyte said:**
> I can package it for you in a .deb file if you want.

Thanks for the offer - maybe when I've added the features that Garrison requested?

---

### Post by germanio on 2008-04-28
Hi NiceGuyUK,

I just found your app, and was looking forward to using it :) I'm using ubuntu 8.04, and it seemed to compile fine along with the dependencies, but when I tried to open an nfo file, I got this:

```
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NotSupportedException: CodePage 437 not supported
  at System.Text.Encoding.GetEncoding (Int32 codePage) [0x00000] 
  at MainWindow.sel_OK_Clicked (System.Object obj, System.EventArgs args) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Dialog.gtk_dialog_run(IntPtr )
   at Gtk.Dialog.gtk_dialog_run(IntPtr )
   at Gtk.Dialog.Run()
   at MainWindow.OnOpenActivated(System.Object sender, System.EventArgs e)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at GNFOView.MainClass.Main(System.String[] args)
```

Any suggestions? :confused:

Also, are you going to make a .deb? :D

---

### Post by NiceGuyUK on 2008-04-28
Hi Germanio,

I'm currently a bit tied up with some coding that I get paid for (its how I earn a living), but gimme a couple of weeks and I'll look into it.

I've only just upgraded my Linux desktop to 8.04 myself but I haven't played with it yet.  If you can bear with me, I'll investigate as soon as I've finished my customer's project.

Thanks

NiceGuyUK

---

