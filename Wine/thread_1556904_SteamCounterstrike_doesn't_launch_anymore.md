---
title: "Steam/Counterstrike doesn't launch anymore"
date: 2010-08-20
forum: Wine
---

### Post by MaindotC on 2010-08-20
Steam will not launch after updating to the latest version of Steam.  I try to run "wine Steam.exe" from the Steam directory but there is no debugging output :(  I upgraded to wine 1.3 and that doesn't seem to affect anything.  Anyone else had this problem?  In #winehq a user stated he had 1.3 installed and didn't have any problems with Steam.

---

### Post by polraudio on 2010-08-20
Are you dualbooting with a Windows OS?

If so. Install steam on Windows then update everything fully. Once fully updated go into linux open steam from the windows partition and it should work. 

Worked for me except i have to run CSS on low graphics even with my drivers installed for graphics.

---

### Post by MaindotC on 2010-08-21
I'm not dual booting winblows nor would I bother doing that :(  Just strikes me as odd how these things just "happen".  Everything has been fine for like 5 straight years, and then all of a sudden a Steam update kills it, and I appear to be the only one.

---

### Post by ATMA3weapon on 2010-08-21
After the steam update yesterday, it broke CS for me. Steam starts just fine as usual. But when i start HL1 games it brings up the initial screen then turns into a zombie and closes out.

---

### Post by MaindotC on 2010-08-21
Exactly what is happening to me :(  I also tried wineboot -u but still no dice.

---

### Post by phun-ky on 2010-08-21
Could this be the same problem I have? [http://ubuntuforums.org/showthread.php?t=1558023](http://ubuntuforums.org/showthread.php?t=1558023)

---

### Post by MaindotC on 2010-08-21
I don't believe so as I'm not getting any output from launching it in a terminal.

---

### Post by Lubos on 2010-08-22
Same here on Ubuntu 9.10 and Wine 1.2 after Steam update.
This is all from console, steam start, than start counter strike 1.6 from steam, counter strike background image without menu (freezing) than terminate CS window and exit steam:
```
wine Steam.exe
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
CellID: Fetching server list from CSDS. . .
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 2, 0x33d334, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 3, 0x33d338, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 4, 0x33d33c, 4) stub
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 2, 0x33d804, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 3, 0x33d808, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 4, 0x33d80c, 4) stub
CellID: CSDS returned 161 servers.
CellID: Connecting to 208.111.182.251:27031. . .
CellID: Connect to 208.111.182.251:27031 took 127 MS
CellID: Nothing beat our old best time of 17 MS
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x4c21150, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x421c000)
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 2, 0x33d80c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 3, 0x33d810, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 4, 0x33d814, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 2, 0x33d2dc, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 3, 0x33d2e0, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 4, 0x33d2e4, 4) stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 2, 0x33d94c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 3, 0x33d950, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 4, 0x33d954, 4) stub
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x33cc6c,0x00000000), stub!
fixme:dwmapi:DwmSetWindowAttribute (0x300a6, 2, 0x33d554, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x300a6, 3, 0x33d558, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x300a6, 4, 0x33d55c, 4) stub
err:ole:RevokeDragDrop invalid hwnd (nil)
fixme:advapi:RegisterTraceGuidsW (0x37e4f30, 0x3e3b720, {3dada31d-19ef-4dc1-b345-037927193422}, 1, 0x3e13b24, (null), (null), 0x3e3b738,)
err:ole:RevokeDragDrop invalid hwnd 0x1011a
fixme:win:EnumDisplayDevicesW ((null),0,0x33f128,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise (0x1ad688)->(1 00000002 0x10a1950)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ad688)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ad688)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ad688)->(ffffffff)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1cfb38,0x1cfa98): stub
err:ntdll:RtlpWaitForCriticalSection section 0x14a74c4 "?" wait timed out in thread 001e, blocked by 001f, retrying (60 sec)
fixme:hnetcfg:fw_app_put_ProcessImageFileName 0x2372c828, L"c:\\program files\\steam\\steamapps\\mysteamnick_sk\\counter-strike\\hl.exe"
fixme:hnetcfg:fw_app_put_Name 0x2372c828, L"Counter-Strike"
fixme:hnetcfg:fw_apps_Add 0x1ddf80, 0x2372c828
err:seh:setup_exception_record stack overflow 2716 bytes in thread 0046 eip 30161db8 esp 00240894 stack 0x240000-0x241000-0x340000
err:ntdll:RtlpWaitForCriticalSection section 0x14a74c4 "?" wait timed out in thread 001e, blocked by 001f, retrying (60 sec)
err:ole:RevokeDragDrop invalid hwnd (nil)
fixme:advapi:UnregisterTraceGuids 0: stub
Shutting down. . .
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

This is maybe related to this error:
[http://appdb.winehq.org/commentview.php?iAppId=1163&iVersionId=19444&iThreadId=62334](http://appdb.winehq.org/commentview.php?iAppId=1163&iVersionId=19444&iThreadId=62334)

[http://forum.winehq.org/viewtopic.php?p=48363](http://forum.winehq.org/viewtopic.php?p=48363)

---

### Post by Technophobia on 2010-08-22
I'm also having this problem with HL1 based games. The best we can do is submit a bug to the Wine team or submit garbage rated tests to HL1 appdb page [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2049](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2049).

---

### Post by hudy5 on 2010-08-23
So can anybody report them this bug ?

Sory for my bad english.

---

### Post by Lubos on 2010-08-23
Already roperted to wine bugzilla (not by me):

[http://bugs.winehq.org/show_bug.cgi?id=24064](http://bugs.winehq.org/show_bug.cgi?id=24064)
[http://bugs.winehq.org/show_bug.cgi?id=24096](http://bugs.winehq.org/show_bug.cgi?id=24096)

---

### Post by fatbuttlarry on 2010-08-23
> **Lubos said:**
> Already roperted to wine bugzilla (not by me):

[http://bugs.winehq.org/show_bug.cgi?id=24064](http://bugs.winehq.org/show_bug.cgi?id=24064)
[http://bugs.winehq.org/show_bug.cgi?id=24096](http://bugs.winehq.org/show_bug.cgi?id=24096)

+1 for this.  I voted for both bugs.

-Tres

---

### Post by MaindotC on 2010-08-23
> **Lubos said:**
> Already roperted to wine bugzilla (not by me):

[http://bugs.winehq.org/show_bug.cgi?id=24064](http://bugs.winehq.org/show_bug.cgi?id=24064)
[http://bugs.winehq.org/show_bug.cgi?id=24096](http://bugs.winehq.org/show_bug.cgi?id=24096)

+1 more for each bug. I didn't know if there was a voting system so I just put in a snippet reply that I'm having the same issue.  I hope it helps bring attention to the problem.

---

### Post by Lubos on 2010-08-26
Here is quick workaround (Xubuntu 9.10, Wine 1.3.1 from ppa and Counter Strike 1.6):
[http://bugs.winehq.org/show_bug.cgi?id=24064](http://bugs.winehq.org/show_bug.cgi?id=24064)

start steam, then rename GameOverlayRenderer.dll to something
else, then start games.
If GameOverlayRenderer.dll is enabled, games freezes with previously mentioned
exception.
After quit Steam, rename .dll back

---

### Post by MaindotC on 2010-09-04
Lubos that does work and will satisfy my CS needs until a fix is discovered.  Thanks!

---

### Post by Lubos on 2010-09-10
Hi,

after last Steam update, you dont need rename GameOverlayRenderer.dll to play Counter Strike 1.6

---

### Post by MaindotC on 2010-09-10
Well I couldn't even run Steam to get the update unless I renamed the dll.  What I ended up doing, and I know this isn't really solving the problem but it works now, is I uninstalled Steam/CS, removed the associative folders, then reinstalled Steam.  Now, however, I cannot start Counterstrike from the wine menu.  I have to start Steam, and then choose CS from the wine menu. It's really not that big of a problem so I just roll with it.  I can go back to wasting away hours of my life playing CS so that's all that's important :D

---

