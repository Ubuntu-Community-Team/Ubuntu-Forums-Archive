---
title: "DDO won't patch"
date: 2009-10-28
forum: Wine
---

### Post by BiynaYahu on 2009-10-28
I followed the instructions on the [page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17785") on WineHQ, and I have downloaded the new patchclient.dll.  I changed the options to point to that new file which I called lotropatcher.dll like the howto.  It still won't patch.

Output:
```
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element

fixme:advapi:SetEntriesInAclA 1 0x33f7dc (nil) 0x33f824
fixme:advapi:SetSecurityInfo stub
fixme:dpnhpast:DllRegisterServer :stub

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element

wine: Call from 0x7b843892 to unimplemented function msvcr71.dll._vscprintf, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
err:rundll32:WinMain Unable to load L"lotropatcher.dll"

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element

wine: Call from 0x7b843892 to unimplemented function msvcr71.dll._vscprintf, aborting

fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
err:rundll32:WinMain Unable to load L"lotropatcher.dll"

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element

wine: Call from 0x7b843892 to unimplemented function msvcr71.dll._vscprintf, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
err:rundll32:WinMain Unable to load L"lotropatcher.dll"

*** Finished ***
```

---

### Post by YokoZar on 2009-10-29
Try winetricks vcrun2003

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by BiynaYahu on 2009-10-29
Thank you for the reply, but I had already done that.  Thankfully though, this [post]("http://http://ubuntuforums.org/showthread.php?t=1280687&page=2") solved my issue.  I added the ppa, upgraded, and the patching worked.  Thank you to everyone who maintains all this amazing free to use software.

Mike Browell

---

