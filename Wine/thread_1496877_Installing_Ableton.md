---
title: "Installing Ableton"
date: 2010-05-29
forum: Wine
---

### Post by Zerocool Djx on 2010-05-29
Hey,.. I need help installing Ableton in Wine....

[http://www.youtube.com/watch?v=5oJ-CSOmouc](http://www.youtube.com/watch?v=5oJ-CSOmouc)

Someone got it working in your tube,... when I attempt to install it it will install but I get a weird error, but it does install, but then when it's don't it doesn't run...

can someone help me?

---

### Post by cogadh on 2010-05-29
You have not provided enough information. Please see the [** Before asking for help with Wine << PLEASE READ BEFORE POSTING **]("http://ubuntuforums.org/showthread.php?t=885111")  sticky for details on what we need from you so you can help us help you.

---

### Post by Zerocool Djx on 2010-05-29
hey yea,. sorry about that,.. 

ok,.. I got wine, wine 1.2, wine-dev, wine-div 1.2, winetricks, wine 1.2-dbg...

ran it in terminal and this what I got:

'/home/vibe/.wine/dosdevices/c:/Program Files/Ableton/Live 8.0.5/Program/Live 8.0.5.exe' 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Ableton\\Live 8.0.5\\Program\\Live 8.0.5.exe") not found
err:module:import_dll Library mfc90.dll (which is needed by L"C:\\Program Files\\Ableton\\Live 8.0.5\\Program\\Live 8.0.5.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Ableton\\Live 8.0.5\\Program\\Live 8.0.5.exe" failed, status c0000135

So,.. I'm assuming I need to bring over some .dll files from windows side then?

As far as compatibility,.. I have both 7.0 and 8.1 versions of ableton.. but, I seen someone on youtube (posted above) got it to work.

---

### Post by cogadh on 2010-05-29
Use the [winetricks script]("http://wiki.winehq.org/winetricks") to install those missing DLL files and give it another shot. The "package" you need to install with winetricks is the "vcrun2008" one (MS Visual C++ 2008 libraries).

---

### Post by Zerocool Djx on 2010-05-29
> **cogadh said:**
> Use the [winetricks script]("http://wiki.winehq.org/winetricks") to install those missing DLL files and give it another shot. The "package" you need to install with winetricks is the "vcrun2008" one (MS Visual C++ 2008 libraries).

Awesome, I just installed wine the "winetricks script" from that link... will that automatically install the "vcrun2008"? or do I need to install that separately? and if so how?

thanks for the help! to make a long story short, I'm hearing impaired, and I DJ with this software like the movie "it's all gone Pete Tong" at the end..

---

### Post by Zerocool Djx on 2010-05-29
It's installing at the moment,... but I wanted to update that it did not throw an error this time during installation,... *~crosses fingers~*

---

### Post by Zerocool Djx on 2010-05-29
I am pleased to announce that it does in fact work! and with a latency of 25ms! NICE! 

HUGE help! thank you very much!

---

### Post by Zerocool Djx on 2010-05-30
Update:

:)

---

