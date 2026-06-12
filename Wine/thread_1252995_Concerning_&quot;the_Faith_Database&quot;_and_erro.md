---
title: "Concerning &quot;the Faith Database&quot; and errors output in gnome-terminal"
date: 2009-08-29
forum: Wine
---

### Post by newagelink on 2009-08-29
I was gifted [The Faith Database]("http://shop.catholic.com/product.php?productid=440") (a Windows CD-ROM) for my birthday. It is apparently *not* mentioned in the [Wine Application Database]("http://appdb.winehq.org/").

I just installed Wine from Ubuntu 9.04's Add/Remove... repository. Then I ```
daniel@daniel-laptop:~$ wine /media/cdrom0/fdbsetup.exe
``` to install the program. Errors abound, and clicking "Cancel" rather than "Ignore" -- ignoring errors seems like a terrible idea -- the entire program closes. Copy/pasting output from the terminal: ```
fixme:reg:GetNativeSystemInfo (0x33fea0) using GetSystemInfo()
fixme:advapi:CheckTokenMembership ((nil) 0x1320c8 0x33fe18) stub!
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 43, in _contents_cb
    (contents, length, etag) = file.load_contents_finish(result)
glib.GError: Bad Request
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Program Files\\FDB\\unins000.exe") stub
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 43, in _contents_cb
    (contents, length, etag) = file.load_contents_finish(result)
glib.GError: Bad Request
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 43, in _contents_cb
    (contents, length, etag) = file.load_contents_finish(result)
glib.GError: Bad Request
fixme:shell:IPersistFile_fnGetCurFile (0x161820)
fixme:shell:IPersistFile_fnGetCurFile (0x1614f0)
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
daniel@daniel-laptop:~$ fixme:mixer:ALSA_MixerInit No master control found on Camera, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 4132 (SPI_GETDROPSHADOW)
err:ole:TLB_ReadTypeLib Loading of typelib L"oleacc.dll" failed with error 2
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x150c60, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x152238, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14b848, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14fb98, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14ffe0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1505b0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x150a28, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x154fb0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14f140, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x14f6e8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x155e48, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1543a0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x154950, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x154d38, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x155250, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x155c10, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x155128, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1581c8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x153fa0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x154490, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1591e8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x157610, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x157a58, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x157638, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15b598, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15b538, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15b598, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x159748, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x159b30, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15a060, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15a5b0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x156608, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x156aa0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x156f78, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x156e48, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15acf8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15b258, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15ce48, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15d420, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15d808, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15fe38, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 43, in _contents_cb
    (contents, length, etag) = file.load_contents_finish(result)
glib.GError: Bad Request
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1602d0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15cb20, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15c358, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15f168, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15e708, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15e708, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x160148, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15f438, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x15fa00, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x163038, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x160510, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1609e8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x164070, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x162410, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x162940, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x162f00, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1633a0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x162110, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1625d8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1663f0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1667b0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x163b88, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1640d8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x165718, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x165c00, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x164a40, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x164fa8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x168c00, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x165f78, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x166498, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x169b38, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x167f18, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1683d0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1688f0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x168888, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x167a48, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x169618, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x169778, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16a2f0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16a750, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16ba10, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16b658, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x167c30, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x168130, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16e0b8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16aeb0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16b308, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16cfc8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16d488, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16d500, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16d240, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x170438, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16ccf8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16d140, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16d600, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16f820, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16f8a8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16f620, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x172788, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16efb0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16f580, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x16f740, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x171b68, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1720e0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x172530, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x174b08, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x170fd8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1715a8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1739e8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x173ed8, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x173e60, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x173cd0, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33deef, 0x33dee8): stub
fixme:urlmon:ObtainUserAgentString (0, 0x176e58, 0x33dee8): stub
fixme:wininet:InternetLockRequestFile STUB
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 43, in _contents_cb
    (contents, length, etag) = file.load_contents_finish(result)
glib.GError: Bad Request
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 43, in _contents_cb
    (contents, length, etag) = file.load_contents_finish(result)
glib.GError: Bad Request
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33d93f, 0x33d938): stub
daniel@daniel-laptop:~$ Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 43, in _contents_cb
    (contents, length, etag) = file.load_contents_finish(result)
glib.GError: Bad Request
``` I checked System > Administration > Hardware Drivers and it said no proprietary drivers were in use. I don't know whether my video card is to blame as [the README thread]("http://ubuntuforums.org/showthread.php?t=885111") suggested, or what to do if it is.

Should I uninstall it and declare it a failure? I don't know what to do, but the program doesn't work.

---

### Post by hikaricore on 2009-08-30
The only thing I see are a cople of python errors.
The rest of the output are not errors but developer messages pertaining to various functions.

Not sure what to tell you tho, if it doesn't run it probably won't without a lot of messing around.

---

