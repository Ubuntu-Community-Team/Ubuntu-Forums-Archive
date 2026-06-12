---
title: "Advice on Gettng an app to run which uses IE"
date: 2009-06-09
forum: Wine
---

### Post by paradigm2 on 2009-06-09
Hello all.  I have installed the latest development version of Wine from the special repository.  I also installed IE6 using the default winetricks.

The application which I want to run requires IE.  I mostly have it running now except the main functionality of this program is lacking.  It is supposed to log in to certain sites and query them for information.  Basically when I try that it always fails.  Strangely though IE6 is able to connect.  Also the application itself loads banners (it is ad supported) over the internet and also requires me to verify log in before starting.  So the internet is working.

Its just that for some reason it fails when logging in and grabbing data from the remotes sites (there are about 20).  To make matters even more puzzling there seems to be one (out of 20) sites where it DOES partially work. One thing which I possibly suspect is that that possibly javascript is broken in IE6...or something having to do with IE6.

Any ideas?  **Is there a better way to install IE6 which would work better (and still work with this app) besides winetricks?**



Also I might as well mention some issues with the app which are more cosmetic in case anyone knows.


- The menu system (File, etc) is a bit messed up.  Clicking on the menu item does not do anything beyond just the initial one to open the menu (like file).  I have to use keyboard shortcuts.  Double clicking does not work on the menu items either.

- There are some screen redraw issues.  A section of the bottom part of the app does not display and install shows the ubuntu desktop.

Thanks for any and all ideas!

---

### Post by paradigm2 on 2009-06-09
Hmmm.  In thinking I consider that this might have to do with the sites being secure (https).  Is anyone able to get IE6 under wine to work with https:// ?  Could you please verify this?

---

### Post by NightMKoder on 2009-06-09
You really shouldn't install IE6 under wine. It needs a whole bunch of pre-req's, etc.

What you need is wine-gecko. It's an implementation of IE using Firefox internals (weird eh?). Clean your wine prefix (ie, either delete it or make a new one) and launch 'wine iexplore'. It should ask you to install it.

---

### Post by paradigm2 on 2009-06-09
> **NightMKoder said:**
> You really shouldn't install IE6 under wine. It needs a whole bunch of pre-req's, etc.

What you need is wine-gecko. It's an implementation of IE using Firefox internals (weird eh?). Clean your wine prefix (ie, either delete it or make a new one) and launch 'wine iexplore'. It should ask you to install it.

Thanks I will give this a shot and simply delete ".wine" (it isn't workign well enough anyway).

I did find that about 4/20 sites are working now (but 2 are intermittent).  I played around and installed some extra stuff, also with trying win98, win2k, and winxp compatibility.  Still the same main issue.

I was able to fix the menu and the redraw issue by switching to XP and installing gdiplus from winetricks.

I will report back.

---

### Post by paradigm2 on 2009-06-09
> **NightMKoder said:**
> You really shouldn't install IE6 under wine. It needs a whole bunch of pre-req's, etc.

What you need is wine-gecko. It's an implementation of IE using Firefox internals (weird eh?). Clean your wine prefix (ie, either delete it or make a new one) and launch 'wine iexplore'. It should ask you to install it.

It looks as if it definitely MUST have ie6.  This program has a security function within it where it will try to load some banners over a https:// connection.  If it fails, no internet activity takes place at all within the program (rendering it useless).  This isn't specific just to Wine, it does this in Windows too.

One way or another it seems as if ie needs to be installed.

I might try ie 5.5 or ie4linux then.

---

### Post by NightMKoder on 2009-06-09
You shouldn't need IE. Wine comes with an implementation of wininet as well as other parts that can most definitely handle https. Paste a log here (without installing IE, but with gecko).

---

### Post by paradigm2 on 2009-06-09
Sure. Here are what seems to be some relevant entries (in order) from when I run it using the default wine browser:

```

fixme:wininet:INET_QueryOption INTERNET_OPTION_SECURITY_FLAGS: Stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_SECURITY_FLAGS; STUB

```

```

err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!

```

```

fixme:shdocvw:navigate_url Unsupported args (Flags 0x32deb8:3; TargetFrameName 0x32dec8:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32cc6c
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[1793b0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x148a78)->((null) 1 0x32d204 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x148a78)->((null) 25 2 0x32d218 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x148a78)->((null) 26 2 0x32d218 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:shdocvw:ClientSite_GetContainer (0x148a78)->(0x32d254)
fixme:shdocvw:ClOleCommandTarget_Exec (0x148a78)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32d328 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x148a78)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d3b8)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32de9c:3; TargetFrameName 0x32deac:8)

```

```

fixme:shdocvw:PersistStreamInit_InitNew (0x216878)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x216878)
fixme:shdocvw:navigate_url Unsupported args (Flags 0xd8bd9b0:3; TargetFrameName 0xd8bd9c0:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x216918)->((null) 1 0xd8bcce0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x216918)->((null) 25 2 0xd8bccf4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x216918)->((null) 26 2 0xd8bccf4 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 40000700
fixme:shdocvw:ClientSite_GetContainer (0x216918)->(0xd8bcd30)

```

```

fixme:shdocvw:ClOleCommandTarget_Exec (0x4553820)->({000214d1-0000-0000-c000-000000000046} 37 0 0xddfce04 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4553820)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0xddfce94)
fixme:shdocvw:ClOleCommandTarget_Exec (0x4553820)->((null) 29 2 0xddfe218 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x4553820)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x4553780)->(0x449a9b0)
fixme:shdocvw:ClientSite_GetContainer (0x4553820)->(0xddfe1cc)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x4553820)->(0xb7ea1051)

```

What is happening is that it should be popping up two banners and then also popping up a half page ad in a pop-up window (the application is ad supported), but it isn't doing that.  The application uses SSL in order to retreive the banners.  When the app is not able to get the banners for whatever reason, it doesn't work (it was this way in XP as well).

---

