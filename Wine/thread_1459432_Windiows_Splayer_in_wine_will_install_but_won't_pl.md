---
title: "Windiows Splayer in wine will install but won't play videos"
date: 2010-04-21
forum: Wine
---

### Post by oracle2b on 2010-04-21
[Splayer]("www.splayer.org/index.en.html") for windows is a good media player and I'd like to use it within Ubuntu. It'll install but when I run the application and the mouse is over the window it'll remain there. I tried to play a video and the application immediately quit. What can I do to make it work.

---

### Post by cogadh on 2010-04-21
Can't really help without a lot more information, like Wine version and its terminal output/error messages (for starters). However, considering the app doesn't even appear in Wine's database of tested applications, you might not have that much luck getting it to run at all.

On a side note, is there a reason that one of the many Linux native media players can't be used? Generally speaking, you will get far better results from one of them than you would from trying to "shoehorn" a Windows app with Wine.

---

### Post by oracle2b on 2010-04-22
Well smplayer won't let me get multiple instances with video. It'll open more than one window but it'll only play sound and no video. Vlc won't play undf files. I liked using Splayer in windows so I figured I'll try it now. Mplayer and movie player aren;t my cup of tea. I ran splayer and that's it there was no terminal commands that appeared,

---

### Post by cogadh on 2010-04-22
In order to get the terminal output, you need to run the app from the terminal:
```
wine "C:\Program Files\Path\To\Splayer.exe"
```
Obviously change that "Path\To\Splayer.exe" to the correct application path. All of Wine's error output should appear in the terminal; hopefully it will point at a cause and possible solution.

---

### Post by rvm4000 on 2010-04-22
> **oracle2b said:**
> Well smplayer won't let me get multiple instances with video. It'll open more than one window but it'll only play sound and no video.

That's probably because smplayer is using xv. Go to preferences -> general -> video and select another video output, and you'll have video in all windows.

---

### Post by oracle2b on 2010-04-23
jeff@IP-STB7:~/Downloads$ wine "/home/jeff/.wine/drive_c/Program Files/SPlayer/splayer.exe"
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:dwmapi:DwmIsCompositionEnabled 0x2c5e60

fixme:shell:InitNetworkAddressControl stub

fixme:keyboard:UnregisterHotKey (0x400e2,943): stub
fixme:keyboard:RegisterHotKey (0x400e2,943,0x00000002,C0): stub

Key not found.
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub

fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub

fixme:dc:CancelDC stub
fixme:dc:CancelDC stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~^[[fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub
fixme:gdi:GetColorAdjustment stub
fixme:gdi:SetColorAdjustment stub

---

### Post by cogadh on 2010-04-23
Key words in that string of "fixme" messages: stub and unimplemented. Basically, the "fixme" messages are developer notes about stuff they are still working on in Wine. Stubs are placeholders for future functionality, often times put in there so that apps that look for that function but don't depend on it will find something and still run. Unimplemented usually means that the function is part of a larger group of functions that have been implemented, but for some reason that particular one has not. Basically what it boils down to is Wine is not yet capable of running that particular app.

---

### Post by oracle2b on 2010-04-24
thanks for the explanation but I'll try rvm4000 advice.

> **rvm4000 said:**
> That's probably because smplayer is using xv. Go to preferences -> general -> video and select another video output, and you'll have video in all windows.

---

