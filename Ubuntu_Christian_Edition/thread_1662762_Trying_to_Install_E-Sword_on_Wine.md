---
title: "Trying to Install E-Sword on Wine"
date: 2011-01-08
forum: Ubuntu Christian Edition
---

### Post by Jonah Bron on 2011-01-08
Hello, world!

I'm atually using Ubuntu Netbook, but I figured this is where all the people that use E-Sword are.  I installed it via the .deb package available here:

[http://www.davidcox.com.mx/e-swordmodules/linux.html](http://www.davidcox.com.mx/e-swordmodules/linux.html)

It went well, but it won't run.  When I try, it gives me an alert box that says this:

> Run-time error '-2147221166 (80040152):

Automation errorWhat does that mean?  I've heard that E-Sword is one of the best programs to run under Wine, so I was hopeful until this point.  Thanks for your help!

Edit: the same thing happened when I tried installing as instructed here, too: [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

---

### Post by david_kt on 2011-01-08
> **Jonah Bron said:**
> 
Edit: the same thing happened when I tried installing as instructed here, too: [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

Do you use the latest installer?
What wine version is installed?

DK

---

### Post by Jonah Bron on 2011-01-08
Thanks for the reply.  The latest, on both counts.  At least, the latest Wine in the repo.  I'd really like to get it working... if I don't, I have to figure out how to install Windows again.

---

### Post by david_kt on 2011-01-08
> **Jonah Bron said:**
> Thanks for the reply.  The latest, on both counts.  At least, the latest Wine in the repo.  I'd really like to get it working... if I don't, I have to figure out how to install Windows again.

Please try to use the wine stable (1.0). Remove wine1.2

DK

---

### Post by Jonah Bron on 2011-01-08
I should also mention that the label of the alert box says "ODCboLst".

---

### Post by Jonah Bron on 2011-01-09
Oh, I didn't see your reply there.  I don't see anything on the Wine website for downloading older versions.  Where could I download Wine 1.0?  I did find older versions on the Sourceforge site, but they only had .rpm and source.  Do I need to build the source?

---

### Post by Jonah Bron on 2011-01-09
I also tried downloading an RPM and converting it to a DEB with Alien.  The conversion went with several errors, but it installed fine.  When I tried to run e-Sword, I got these errors in the terminal.

```
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/steve/.wine' has been updated.
err:ole:create_server class {8c62eeb0-4ef2-40ce-aff7-1c899ef32cbe} not registered
err:ole:CoGetClassObject no class object {8c62eeb0-4ef2-40ce-aff7-1c899ef32cbe} could be created for context 0x5
fixme:ole:OleLoadPictureEx (0xfcbca4,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f9d0), partially implemented.
fixme:ole:OleLoadPictureEx (0xfd073c,3334,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f150), partially implemented.
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:ole:OleLoadPictureEx (0xfd073c,3334,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f150), partially implemented.
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:ole:OleLoadPictureEx (0xfd616c,1150,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f58c), partially implemented.
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x166f8c), stub!
fixme:ole:OleLoadPictureEx (0xfd073c,3334,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32f150), partially implemented.
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
err:ole:CoGetClassObject no class object {20dd1b9e-87c4-11d1-8be3-0000f8754da1} could be created for context 0x3
err:listview:LISTVIEW_WindowProc unknown msg 2210 wp=00000001 lp=00010086
err:listview:LISTVIEW_WindowProc unknown msg 2210 wp=00000001 lp=0001008a
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\tx4ole14.ocx") not found
err:ole:CoGetClassObject no class object {15a32f01-b939-11dc-af58-0013d350667c} could be created for context 0x3
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
```I don't know if that means anything to you.

---

### Post by david_kt on 2011-01-09
> **Jonah Bron said:**
> Oh, I didn't see your reply there.  I don't see anything on the Wine website for downloading older versions.  Where could I download Wine 1.0?  I did find older versions on the Sourceforge site, but they only had .rpm and source.  Do I need to build the source?

Just run below command:

```
sudo apt-get install wine1.0
```

DK

---

### Post by Jonah Bron on 2011-01-09
Okay, I tried to install it that way, but I got the "Errors were encountered while processing ..." error.  But, I'm thinking that's a result of the other stuff I've been doing trying to get it working.  So, I'm reinstalling the operating system.  When that's done, I'll give it another go-round.

---

### Post by Jonah Bron on 2011-01-09
Making progress!  Wine 1.0 is now installed.  Should I run that installer bash script at this point?

---

### Post by Jonah Bron on 2011-01-09
Alright, I ran the installer script.  Everything went smoothly.  But, I ran "wine e-Sword.exe", and it said "Library MSVBVM60.DLL (which is needed by ...) not found".  What's the problem this time?  Thanks for your help so far.

---

### Post by Jonah Bron on 2011-01-09
Oh, it's working!  Awesome!  I copied everything from ~/.wine_Esword to ~/.wine, and ran e-Sword.exe from there, and it worked!  Thanks a lot for your help!

---

### Post by david_kt on 2011-01-09
> **Jonah Bron said:**
> Making progress!  Wine 1.0 is now installed.  Should I run that installer bash script at this point?

Make sure you have cabextract install before running the installer.

DK

---

### Post by david_kt on 2011-01-10
> **Jonah Bron said:**
> Alright, I ran the installer script.  Everything went smoothly.  But, I ran "wine e-Sword.exe", and it said "Library MSVBVM60.DLL (which is needed by ...) not found".  What's the problem this time?  Thanks for your help so far.

Sorry I did not see your post before. You should not run wine e-Sword.exe, but run from the launcher on your desktop. Or, from terminal you should run:

 ```
env WINEPREFIX=~/.wine_Esword wine "C:\Program Files\e-Sword\e-Sword.exe"
```

DK

---

