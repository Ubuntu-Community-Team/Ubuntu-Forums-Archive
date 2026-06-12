---
title: "Spotify ALSA audio problem"
date: 2009-02-06
forum: Wine
---

### Post by SpinningAround on 2009-02-06
I got a problem with the audio in Spotify, I got sound when using ALSA problem is that sometime after some amount of time do the music playing stop completely, the song don't continue and I'm forced to restart the program to get it working again. I tried out OSS and it worked and didn't stop playing but when I use OSS can't I play from other audio sources. 

Output when running Spotify, I guess that the audio problem might have to do with the first line about the HDA ATI HDMI, unsure if it's relevant but my graphic card is a HD 4670
```

:~$ wine "C:\Program Files\Spotify\spotify.exe"
Warning: could not find DOS drive for current working directory '/home/', starting in the Windows directory.
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:shell:SHAppBarMessage msg=4, data={cb=36, hwnd=(nil), callback=7ee13ff4, edge=2076596987, rc=(4235920,3339772)-(17,0), lparam=7ed973a7}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=7ee13ff4, edge=0, rc=(4235920,3339772)-(17,0), lparam=7ed973a7}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=7ee13ff4, edge=1, rc=(4235920,3339772)-(17,0), lparam=7ed973a7}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=7ee13ff4, edge=2, rc=(4235920,3339772)-(17,0), lparam=7ed973a7}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=7ee13ff4, edge=3, rc=(4235920,3339772)-(17,0), lparam=7ed973a7}: stub
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:win:RegisterShellHookWindow (0x10024): stub
fixme:wininet:INET_QueryOptionHelper INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOptionHelper Unhandled dwOption 5
fixme:wininet:INET_QueryOptionHelper Unhandled dwOption 2
fixme:shell:SHAppBarMessage msg=4, data={cb=36, hwnd=(nil), callback=6020000, edge=65580, rc=(0,2147319808)-(2128544762,9547600), lparam=1002c}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=6020000, edge=0, rc=(0,2147319808)-(2128544762,9547600), lparam=1002c}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=6020000, edge=1, rc=(0,2147319808)-(2128544762,9547600), lparam=1002c}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=6020000, edge=2, rc=(0,2147319808)-(2128544762,9547600), lparam=1002c}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=6020000, edge=3, rc=(0,2147319808)-(2128544762,9547600), lparam=1002c}: stub
fixme:shell:SHAppBarMessage msg=4, data={cb=36, hwnd=(nil), callback=9, edge=5, rc=(-137591535,0)-(0,2120478964), lparam=7d4ed0c0}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=9, edge=0, rc=(-137591535,0)-(0,2120478964), lparam=7d4ed0c0}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=9, edge=1, rc=(-137591535,0)-(0,2120478964), lparam=7d4ed0c0}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=9, edge=2, rc=(-137591535,0)-(0,2120478964), lparam=7d4ed0c0}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=9, edge=3, rc=(-137591535,0)-(0,2120478964), lparam=7d4ed0c0}: stub
fixme:shell:SHAppBarMessage msg=4, data={cb=36, hwnd=(nil), callback=0, edge=0, rc=(65536,83)-(1328240,2076391215), lparam=8}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=0, edge=0, rc=(65536,83)-(1328240,2076391215), lparam=8}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=0, edge=1, rc=(65536,83)-(1328240,2076391215), lparam=8}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=0, edge=2, rc=(65536,83)-(1328240,2076391215), lparam=8}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=0, edge=3, rc=(65536,83)-(1328240,2076391215), lparam=8}: stub
fixme:shell:SHAppBarMessage msg=4, data={cb=36, hwnd=(nil), callback=7ed10ee0, edge=0, rc=(1324800,2076393473)-(0,1114112), lparam=2}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=7ed10ee0, edge=0, rc=(1324800,2076393473)-(0,1114112), lparam=2}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=7ed10ee0, edge=1, rc=(1324800,2076393473)-(0,1114112), lparam=2}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=7ed10ee0, edge=2, rc=(1324800,2076393473)-(0,1114112), lparam=2}: stub
fixme:shell:SHAppBarMessage msg=7, data={cb=36, hwnd=(nil), callback=7ed10ee0, edge=3, rc=(1324800,2076393473)-(0,1114112), lparam=2}: stub


```

---

### Post by Dizzle7677 on 2009-02-07
Audio is a pain as it is in L but this is what works for me to make it less so. 

Set 'Alsa" in Prefs->Sound
killall pulseaudio
Write a new key under HKCU/Software/Wine called "Alsa Driver" , new string "UseDirectHW" , value 'y'.

Look in the Winecfg -> Audio tab also for settings. Course it could just be ATI oddness since the video/audio card are the same (?!). Use the search Luke.

---

### Post by RaiCoss on 2009-02-07
> **Dizzle7677 said:**
> Audio is a pain as it is in L but this is what works for me to make it less so. 

Set 'Alsa" in Prefs->Sound
killall pulseaudio
Write a new key under HKCU/Software/Wine called "Alsa Driver" , new string "UseDirectHW" , value 'y'.

Look in the Winecfg -> Audio tab also for settings. Course it could just be ATI oddness since the video/audio card are the same (?!). Use the search Luke.

You may want to switch too OSS sound in the WINE configuration, it fixed every sound issue I ever had when using ALSA.

[[EDIT]]I just read your post properly, so ignore this advice. XD

---

### Post by SpinningAround on 2009-02-07
> **Dizzle7677 said:**
> Audio is a pain as it is in L but this is what works for me to make it less so. 

Set 'Alsa" in Prefs->Sound
killall pulseaudio
Write a new key under HKCU/Software/Wine called "Alsa Driver" , new string "UseDirectHW" , value 'y'.

Look in the Winecfg -> Audio tab also for settings. Course it could just be ATI oddness since the video/audio card are the same (?!). Use the search Luke.

I will try that if I keep having the problem, but I updated to the latest Wine using Launchpad and it looks like it fixed it.

---

### Post by HandeH on 2009-12-14
> **SpinningAround said:**
> I got a problem with the audio in Spotify, I got sound when using ALSA problem is that sometime after some amount of time do the music playing stop completely, the song don't continue and I'm forced to restart the program to get it working again. 


I had same kind of symptoms, although I could play Spotify only a couple of seconds (longer if I brought down volume from System>Settings>Sound>) with distorted sounds. My computer is Compal JFL92 laptop with Karmic Koala 9.10. 

Solution was for me: 
[LIST=1]
[*]At Wine config go to Sounds tab. 
[*]Remove selection (tick) from ALSA Driver and tick instead EsounD Driver. 
[*]Click OK or Apply. 
[*]Restart your spotify.
[/LIST]

---

### Post by maj1912 on 2010-01-02
Had a problem with Spotify under Karmic amd64 where the audio was stuttering badly.  

Switching to Esound driver as described above sorted the problem.  
Thanks.

---

### Post by nikKiiin on 2010-01-11
> **maj1912 said:**
> Had a problem with Spotify under Karmic amd64 where the audio was stuttering badly.  

Switching to Esound driver as described above sorted the problem.  
Thanks.
Ditto :D

---

### Post by Sputnik82 on 2010-01-13
Had the same problem in Karmic Koala with Alsa and selecting Esound solved it :D
Thanks!

---

### Post by qrwe on 2010-02-10
> **Sputnik82 said:**
> Had the same problem in Karmic Koala with Alsa and selecting Esound solved it :D
Thanks!

Same here, enabling Esound solved my problem. I recommend this solution!

---

### Post by c.zach on 2011-02-02
Esound is not always the solution (in my case its pretty laggy).

I had the same problem (sound stopped after some time) and setting hardware acceleration to "Emulation" with Alsa enabled helped.

---

