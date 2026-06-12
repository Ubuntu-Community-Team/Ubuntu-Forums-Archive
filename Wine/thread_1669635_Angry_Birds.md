---
title: "Angry Birds"
date: 2011-01-16
forum: Wine
---

### Post by stmiller on 2011-01-16
Angry Birds runs 100% perfect with wine on Ubuntu 10.10 for me. yay!

You will need to copy over the PC version (buy through intel store on Windows - argh), and then also download this dll and place it in the Angry Birds application directory (beside the exe).

msvcp90.dll

[http://www.dll-files.com/msvcp90.zip?0VLhPAdIlW](http://www.dll-files.com/msvcp90.zip?0VLhPAdIlW)

It just works with no winetricks or other hacks involved for me.

```
$ wine --version
wine-1.3.1


```

```
Angry Birds PC$ ls
AngryBirds.exe  AppUpWrapper.dll  config.lua  data  msvcp90.dll  msvcr100.dll
```

```
$ wine AngryBirds.exe
```

---

### Post by jakejw93 on 2011-01-17
[_[COLOR="Navy"]Angry Birds running in Linux[/COLOR]_]("http://www.youtube.com/watch?v=cFy7zfXq5R8")

Showing that angry birds can run in Linux!!!!! For me it ran straight away, and perfectly!

---

### Post by dankegel on 2011-01-18
I tried it.  It took some doing to find the .msi in 
c:\ProgramData\Intel.  Installed fine, into
c:/Program Files/Rovio/Angry Birds
(not Angry Birds PC), but didn't run.  When I start it, I get
the error dialog
The ADP runtime was unable to initialize 
as described at
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22450](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22450)

So, how come it worked for you and not me?

I have a sneaking suspicion that everyone running it on Linux
is running a cracked version.

---

### Post by pedro.nariyoshi on 2011-01-20
Maybe they're running a different version.

But I hear you Dan, I can't get it to work either... Same ADP problem..

---

### Post by Toshibawarrior on 2011-01-23
> **dankegel said:**
> 

So, how come it worked for you and not me?

I have a sneaking suspicion that everyone running it on Linux
is running a cracked version.

Your sneaking suspicion is correct. I also got the ADP runtime error and when I dug a little bit deeper I saw that Intel's AppUp software uses diabolical and proprietary DRM; which means that you can't run any AppUp apps on Wine because AppUp itself does not run under Wine. So to get Angry Birds running, the DRM must go, which at the same time means cracking the app...We're SOL on this one.

---

### Post by bboydp on 2011-01-29
Thank you for posting this, works like a charm and fun!

---

### Post by mitk0o0o0 on 2011-03-15
Thanks, worked. :)

But it overheated my computer alot after barely 10 mins of playing :O

---

