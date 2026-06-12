---
title: "Steam game hangs on load screen"
date: 2010-08-21
forum: Wine
---

### Post by phun-ky on 2010-08-21
I've been running Steam through Wine for ages now, and suddenly, after I tried to move the game window for Day of Defeat on startup (with alt button), none of the Steam games will load :( I get the background music and background image for the game, but no menu shows up. It's not even possible to select the game window once you alt+tab away from it..

I've tried reinstalling Steam/rebooting with no help

Here's the wine feedback from when I activate Day of defeat:

```

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32c924,0x00000000), stub!
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x10128
fixme:win:EnumDisplayDevicesW ((null),0,0x33f128,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise (0x1ca2f8)->(1 00000002 0x3d60090)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ca2f8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ca2f8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ca2f8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1cb168)->(1 00000002 0x3d610c0)
fixme:shdocvw:PersistStreamInit_InitNew (0x1cb168)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1cb168)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1cb168)->(ffffffff)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1d4878,0x1d47d8): stub
err:seh:setup_exception_record stack overflow 2716 bytes in thread 0022 eip 30161db8 esp 00240894 stack 0x240000-0x241000-0x340000
fixme:hnetcfg:fw_app_put_ProcessImageFileName 0x10076de8, L"c:\\programfiler\\steam\\steamapps\\phun-ky\\day of defeat\\hl.exe"
fixme:hnetcfg:fw_app_put_Name 0x10076de8, L"Day of Defeat"
fixme:hnetcfg:fw_apps_Add 0x10077de8, 0x10076de8
err:ntdll:RtlpWaitForCriticalSection section 0x14a7494 "?" wait timed out in thread 001f, blocked by 0020, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x14a7494 "?" wait timed out in thread 001f, blocked by 0020, retrying (60 sec)


```

I've also tried to reinstall Wine and Steam with no other result :(

EDIT:

Seems it actually is a Steam bug: [http://forums.steampowered.com/forums/showthread.php?t=1406135](http://forums.steampowered.com/forums/showthread.php?t=1406135)

---

### Post by ATMA3weapon on 2010-08-21
I was getting a similar error at the end in your log

```
err:ntdll:RtlpWaitForCriticalSection section 0x14a7494 "?" wait timed out in thread 001f, blocked by 0020, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x14a7494 "?" wait timed out in thread 001f, blocked by 0020, retrying (60 sec) 
```

---

### Post by harvodan on 2010-08-22
In my experience this happens because of the Steam community feature. The overlay actually seems to work now, and some games under wine don't like it at all. If the game fails to launch with that particular error, you need to go to the game properties and disable Steam Community ingame. Or you could do it globally under the steam settings for ingame features.

If it's a steam bug and it gets fixed, that's great, but this is how I got some games working in the meantime.

---

### Post by fatbuttlarry on 2010-08-23
> **harvodan said:**
> In my experience this happens because of the Steam community feature. The overlay actually seems to work now, and some games under wine don't like it at all. If the game fails to launch with that particular error, you need to go to the game properties and disable Steam Community ingame. Or you could do it globally under the steam settings for ingame features.

If it's a steam bug and it gets fixed, that's great, but this is how I got some games working in the meantime.

Thanks for the suggestions, but this doesn't fix it.  It's a new bug.  Any further advice is welcome.

Please cross-post here: [http://ubuntuforums.org/showthread.php?t=1556904](http://ubuntuforums.org/showthread.php?t=1556904)  and vote for bug here:

wine bugzilla:

[http://bugs.winehq.org/show_bug.cgi?id=24064](http://bugs.winehq.org/show_bug.cgi?id=24064)
[http://bugs.winehq.org/show_bug.cgi?id=24096](http://bugs.winehq.org/show_bug.cgi?id=24096)

-Tres

---

