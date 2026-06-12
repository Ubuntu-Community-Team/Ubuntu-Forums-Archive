---
title: "Ableton crashes when choosing wineasio"
date: 2012-02-03
forum: Ubuntu Studio
---

### Post by 0p7 0u7 on 2012-02-03
So I've tinkered with this enough to feel I'm almost there as far as getting this running the way I want.  I'm running ableton 8.2.2, wine 1.2.3, wineasio .90 and jack2.. All on an Hp AMD 64 dual core laptop with ati graphics and 3gbs of ram..  Wineasio registers, jack starts and runs, however when I try to choose the Wineasio driver in Ableton it crashes. I've tried enabling Alsa only in winecfg but then Wineasio doesn't appear as an option. When I choose Jack or both alsa and jack, and then I choose Wineasio in Ableton it just freezes and I have to force close it.  I loaded Ableton in the terminal and here is the output up until it crashes, I was hoping this might be something simple.. Thanks 

> [FONT=Courier New]a3n05m41@a3n05m41:~$ env WINEPREFIX="/home/a3n05m41/.wine" wine C:\\windows\\command\\start.exe /Unix /home/a3n05m41/.wine/dosdevices/c:/users/a3n05m41/Start\ Menu/Programs/Ableton/Live\ 8.2.2/Live\ 8.2.2.lnk
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
a3n05m41@a3n05m41:~$ fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f8fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33f8fc,0x00000000), stub!
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on USB 2.0 Video Capture Controlle, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on USB Midi, disabling mixer
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:dmusic:IDirectMusic8Impl_SetDirectSound (0x21e320, (nil), 0x10032): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5c0,0x00000000), stub!
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:ReplaceFileW Ignoring flags 1
fixme:file:ReplaceFileW Ignoring flags 1
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:win:FlashWindowEx 0x33f7c8
fixme:win:FlashWindowEx 0x33f848
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:ReplaceFileW Ignoring flags 1
fixme:file:ReplaceFileW Ignoring flags 1
fixme:file:ReplaceFileW Ignoring flags 1[/FONT]This last part is what pops up after I choose wineasio.

> 
[FONT=Courier New]fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
no message buffer overruns
no message buffer overruns
unknown option character l
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
`default' server already active
Failed to open server

[/FONT]

---

