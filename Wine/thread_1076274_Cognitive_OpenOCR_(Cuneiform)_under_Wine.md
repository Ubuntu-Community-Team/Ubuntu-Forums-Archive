---
title: "Cognitive OpenOCR (Cuneiform) under Wine"
date: 2009-02-21
forum: Wine
---

### Post by canakas on 2009-02-21
Dear all,

The availability of solid OCR-software is getting better these days. The release of the source of [tesseract]("http://code.google.com/p/tesseract-ocr/") and now the even more sought after [Cognitive OpenOCR (Cuneiform)]("http://en.openocr.org/")(english version) has given open source users industry standard alternatives to other freely available packages (kooka w/gocr or OCRAD, Clara).

The windows compilation of Cognitive OpenOCR (Cuneiform)' source has got a gold rating in the WineHQ AppDB under Ubuntu.
(It is necessary to get some DLLs with vcrun6 using winetricks, and setting a (native,builtin) override for msvcrt.-)

Now the program installs fine and starts fine, although todays tip is a little clouded.

The problem is; When I try to open an image file(JPEG or PNG) I get an error message saying "Unable to open image"

Is there anything I need to add to Wine for there to be a codec available for JPEG or PNG decoding?

Here are the terminal outputs:

On opening
```
~/.wine/drive_c/Program Files/Cognitive/CuneiForm$ wine Face.exe
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Cognitive\\CuneiForm\\Face.exe" failed with error 0
fixme:win:LockWindowUpdate (0x1b00e8), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
err:ole:marshal_object object doesn't expose interface {00000126-0000-0000-c000-000000000046}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002

```

On clicking the "open file"-button
```
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented

```

On selecting image and clicking open
```
fixme:gdiplus:GdipCreateHBITMAPFromBitmap stub

```

All input is appreciated

-canakas

---

### Post by cogadh on 2009-02-21
The "fixme" messages are just developer notes about incomplete or unimplemented functions in Wine. There is really nothing you can do to fix them, unless you feel like coding a patch for Wine. However, for getting the JPG and PNG files to display properly, you might try using Winetricks to install gdiplus. There is a [known JPG/PNG bug in Wine]("http://bugs.winehq.org/show_bug.cgi?id=16249") (currently unrelated to Cuneiform) that seems to be corrected by installing a native gdiplus.

As for that gold rating, that was on an older version of Wine, so more current versions of Wine may be experiencing regressions that are preventing full functionality. This would seem to be the case, since the app has a general rating of silver and the most current test with Wine 1.1.10 also got a silver rating (distro used really shouldn't affect that).

---

### Post by canakas on 2009-02-21
Hello and thanks very much for the reply

I ran ```
sh winetricks gdiplus
```

and this fixed the problem with opening the archives. I will now have to understand how to get the markup mode to work. Automarkup gives this error message:

```
err:tooltips:TOOLTIPS_Timer How did this happen?
fixme:win:LockWindowUpdate (0x20184), partial stub!
fixme:win:LockWindowUpdate (0x20184), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
err:ole:create_server class {00000000-0000-0000-0000-000000000000} not registered
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x4
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented
fixme:win:LockWindowUpdate (0x20184), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
err:ole:create_server class {00000000-0000-0000-0000-000000000000} not registered
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x4
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented
fixme:win:LockWindowUpdate (0x20184), partial stub!
fixme:win:LockWindowUpdate (0x20184), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x5300d2), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x5300d2), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x9015a

```

I will post back if more interesting results appear.

Thanks a lot for your continuing help.

-canakas

---

### Post by sb73542 on 2009-03-02
Hi there,

Which is currently the best option to run under wine, the new open source Windows version ( [http://www.cuneiform.ru/downloads/setup_openocr_cuneiform_eng.exe](http://www.cuneiform.ru/downloads/setup_openocr_cuneiform_eng.exe) ) or the original version 12 release ( [http://www.cuneiform.ru/downloads/cuneiform.zip](http://www.cuneiform.ru/downloads/cuneiform.zip) ) ?

Thanks!

---

### Post by canakas on 2009-03-02
Hello,

the zip file contains a setup that only installs with russian language on my box... if you can make 12 install in english, please let us know =)

---

### Post by sb73542 on 2009-03-03
Good point!

FYI, I tried the english version under Wine 1.1.15, and it can't load images, even after doing the msvcrt override.  I am now going to try downgrading Wine to 1.0.1.

---

### Post by sb73542 on 2009-03-09
I got it to work, but not under the current Wine, 1.1.16.  I need the newest version for another program.

---

