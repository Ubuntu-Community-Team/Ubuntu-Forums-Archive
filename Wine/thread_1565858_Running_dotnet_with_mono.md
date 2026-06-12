---
title: "Running dotnet with mono"
date: 2010-09-01
forum: Wine
---

### Post by kuro_kid on 2010-09-01
first, i want to say sorry if i post in wrong section

i want to running windows app that need .net, so i try to use mono but i got some error
```
kuro_kid@Ubunchu:$mono win_apps.exe


Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for &#8199; ---> System.ArgumentException: Encoding name 'windows-1256' not supported
Parameter name: name
  at System.Text.Encoding.GetEncoding (System.String name) [0x00000] in <filename unknown>:0 
  at &#8193;..ctor () [0x00000] in <filename unknown>:0 
  at &#8199;. () [0x00000] in <filename unknown>:0 
  at &#8199;..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at&#8192;. (Boolean ) [0x00000] in <filename unknown>:0 
  at&#8192;. () [0x00000] in <filename unknown>:0 
  at&#8192;..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check)&#8192;:.ctor ()
  at &#8201;. () [0x00000] in <filename unknown>:0
```i really don't understand what is meaning,, please help me!!!!:confused:

---

### Post by kuro_kid on 2010-09-03
anyone????

---

### Post by dino99 on 2010-09-04
install winetricks if not already installed, and add the related .net files and maybe some additional fonts too

---

### Post by kuro_kid on 2010-09-05
thank's for respon
but i'm not using wine, i'm using mono
if i using wine and than installing mono with winetrick, i have this error

```
kuro_kid@Ubunchu:$wine win_apps.exe

fixme:win:EnumDisplayDevicesW ((null),0,0x60dc5c,0x00000000), stub!
fixme:dciman:DCICreatePrimary 0x430 0x1b322ac
System.TypeInitializationException: An exception was thrown by the type initializer for System.Windows.Forms.MimeIconEngine ---> System.DllNotFoundException: libgdk-x11-2.0.so.0
  at (wrapper managed-to-native) System.Windows.Forms.GnomeUtil:gdk_init_check (intptr,intptr)
  at System.Windows.Forms.GnomeUtil.Init () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.GnomeUtil.GetIcon (System.String icon, Int32 size) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.GnomeHandler.AddGnomeIcon (System.String internal_mime_type, System.String name) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.GnomeHandler.CreateUIIcons () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.GnomeHandler.Start () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.MimeIconEngine..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Windows.Forms.WinFileSystem..ctor () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.MWFVFS..ctor () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.FolderBrowserDialog+FolderBrowserTreeView..ctor (System.Windows.Forms.FolderBrowserDialog parent_dialog) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.FolderBrowserDialog/FolderBrowserTreeView:.ctor (System.Windows.Forms.FolderBrowserDialog)
  at System.Windows.Forms.FolderBrowserDialog..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.FolderBrowserDialog:.ctor ()
  at ?. () [0x00000] in <filename unknown>:0 
  at ?..ctor (.?
                  , . , System.Windows.Forms.ListView , Boolean, Boolean , Boolean ) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) ?:.ctor (?
                                                     ,,System.Windows.Forms.ListView,bool,bool,bool)
  at?.? (System.Object , System.EventArgs ) [0x00000] in <filename unknown>:0 
  at?. (System.Object , System.Windows.Forms.MouseEventArgs ) [0x00000] in <finknown>:0 
  at System.Windows.Forms.Control.OnMouseDoubleClick (System.Windows.Forms.MouseEventArgs e) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ListView+ItemControl.HandleClicks (System.Windows.Forms.MouseEventArgs me) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ListView+ItemControl.ItemsMouseUp (System.Object sender, System.Windows.Forms.MouseEventArgs me) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Control.OnMouseUp (System.Windows.Forms.MouseEventArgs e) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Control.WmLButtonUp (System.Windows.Forms.Message& m) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.ListView+ItemControl.WndProc (System.Windows.Forms.Message& m) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.NativeWindow.WndProc (IntPtr hWnd, Msg msg, IntPtr wParam, IntPtr lParam) [0x00000] in <filename unknown>:0 

```

---

### Post by dino99 on 2010-09-05
some usefull links about:

[http://www.google.fr/search?as_q=dotnet%2Bmono%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=dotnet%2Bmono%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

by the way, you said above that you want to run windoz apps using .net, so on linux you need to run them on wine [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true), on the other hand, mono is at linux what .net is at windoz, so what you try seem confuse to me, sorry.

---

### Post by kuro_kid on 2010-09-12
wine have program to run .net program called mono that we can install by winetrick but except that linux have independent program called mono(the name same as program in wine) and the two program have same function. my problem is i can't run windoz program using neither wine or mono???

---

