---
title: "Wine 1.3.17/Lucid 64bit/No Sound"
date: 2011-04-17
forum: Wine
---

### Post by pqwoerituytrueiwoq on 2011-04-17
From lscpi
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
```If I enable audio or go to the audio tab in wine config rhythmbox goes mute and will not un-mute till it is restarted so I disabled it
i installed the [FONT=Courier New]alsa-oss[/FONT] package but it still is not working

also tried this
```
$ winetricks mfc42
Executing w_do_call mfc42
Executing load_mfc42
Executing mkdir -p /home/chad/.cache/winetricks/vcrun6
Downloading http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe to /home/chad/.cache/winetricks/vcrun6
--2011-04-17 18:15:46--  http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe
Resolving download.microsoft.com... 65.54.81.204, 65.54.81.208
Connecting to download.microsoft.com|65.54.81.204|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1833232 (1.7M) [application/octet-stream]
Saving to: `vc6redistsetup_enu.exe'

100%[======================================>] 1,833,232   49.1K/s   in 65s     

2011-04-17 18:16:52 (27.7 KB/s) - `vc6redistsetup_enu.exe' saved [1833232/1833232]

Executing wine /home/chad/.cache/winetricks/vcrun6/vc6redistsetup_enu.exe /T:C:\windows\Temp\_mfc42 /c
Executing cabextract -q /home/chad/.cache/winetricks/vcrun6/vcredist.exe -d /home/chad/.wine/dosdevices/c:/windows/system32 -F mfc42*.dll
/home/chad/.cache/winetricks/vcrun6/vcredist.exe: library not compiled to support large files.
```

---

### Post by cogadh on 2011-04-19
That's not a Wine problem, that's most likely a limitation of your sound hardware and ALSA (assuming you had Wine and Rythbox set to use ALSA). Unless your sound hardware is a full hardware sound card, ALSA is limited to only processing one audio stream at a time, so you can either have Rythmbox or Wine using it, but not both. I think you can configure Rythmbox to not use ALSA by default, which may correct the problem.

---

### Post by pqwoerituytrueiwoq on 2011-04-19
can wine be configured to use something else, and if so how?
guess my laptop has a full hardware sound card then
edit sound test fails in wine config on all settings in it

---

### Post by cogadh on 2011-04-19
You can try setting Wine to use the OSS driver and using the "padsp" command to run Wine with PulseAudio's OSS wrapper, it sometimes solves the issue. Usage:
```
padsp wine executable.exe
```

---

