---
title: "Spotify: internal error 1"
date: 2009-10-08
forum: Wine
---

### Post by zoniq on 2009-10-08
I can install Spotify without a problem, but as soon as I try to run it I get **internal error 1**

If I run it manually from the shell I get the following debug output:
> wine spotify.exe
fixme:reg:GetNativeSystemInfo (0x74c4a3) using GetSystemInfo()
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:thread:NtSetInformationThread info class 17 not supported yet
fixme:imagehlp:CheckSumMappedFile (0xea0000, 2166780, 0x7966cc, 0x7966d0): stub
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x79cb55): Stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags


My current wine version is **wine-1.0.1**

---

### Post by asdfoo on 2009-10-08
> **zoniq said:**
> I can install Spotify without a problem, but as soon as I try to run it I get **internal error 1**

If I run it manually from the shell I get the following debug output:


My current wine version is **wine-1.0.1**

It might work if you use a version that is more recent... 1.0.1 was released about a year ago.

---

### Post by zoniq on 2009-10-09
Thanks. That helped. I just upgraded to **wine-1.1.30** via [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) and now Spotify runs without any problem so far.

---

### Post by KilianValkhof on 2009-10-27
I have this error with wine **version 1.1.32**. Any tips?

---

### Post by aske on 2010-10-25
Hello,

i have the same problem.

had the problem with version 1.1.42 (which i think is the same 1.2 version) and just now with 1.3.5.

yesterday one song played, but when it tried to play the second it would not play it.
i get the same error message in the terminal, the result is for the song (any song) never to be able to start. it seems as it is about to start, but stays at 0:00.

please advise, thanx.

---

