---
title: "Unity Web Player - anyone got it working in WINE?"
date: 2010-05-21
forum: Wine
---

### Post by emarkay on 2010-05-21
[http://unity3d.com/webplayer/](http://unity3d.com/webplayer/)

A weather site I use has a new Beta of "3D" NEXRAD, and I want to see if it's useful (as NWS Weather Spotter) or just a gimmick.  I don't see a Linux version listed and want to know if anyone has had any experience with getting this to work in Ubuntu (Karmic and Lucid) 

Thank you!

MRK

---

### Post by cogadh on 2010-05-21
About the only way I can see this possibly working would be if you install the Windows version of Firefox in Wine, then install the unity plug-in in that. Just installing the player in Wine without a Windows-based browser for it to work in would be useless.

---

### Post by tilixibr on 2010-08-13
Good suggestion. The only problem is that when i run the Unity installer via Wine (after instaling Windows Firefox version) I get an aborted installation and the following output:

```
Output folder: C:\users\fernandes\Local Settings\Application Data\Unity\WebPlayer
Extract: UnityBugReporter.exe
Extract: UnityWebPlayerUpdate.exe
Output folder: C:\users\fernandes\Local Settings\Application Data\Unity\WebPlayer\mono\2.x.x
Extract: mono-1-vc.dll
Extract: info.plist
Output folder: C:\users\fernandes\Local Settings\Application Data\Unity\WebPlayer\mono\2.x.x\Data\etc\mono\2.0
Extract: machine.config
Output folder: C:\users\fernandes\Local Settings\Application Data\Unity\WebPlayer\mono\2.x.x\Data\lib
Extract: mscorlib.dll
Extract: UnityDomainLoad.exe
Output folder: C:\users\fernandes\Local Settings\Application Data\Unity\WebPlayer\player\2.x.x
Extract: info.plist
Extract: webplayer_win.dll... 100%
Extract: wrap_oal.dll
Output folder: C:\users\fernandes\Local Settings\Application Data\Unity\WebPlayer\player\2.x.x\Data
Extract: unity default resources
Output folder: C:\users\fernandes\Local Settings\Application Data\Unity\WebPlayer\player\2.x.x\Data\lib
Extract: Boo.Lang.dll
Extract: UnityScript.Lang.dll
Extract: UnityEngine.dll
Output folder: C:\users\fernandes\Local Settings\Application Data\Unity\WebPlayer\loader
Extract: info.plist
Extract: npUnity3D32.dll
Extract: UnityWebPluginAX.ocx
Output folder: C:\users\fernandes\Local Settings\Application Data\Unity\WebPlayer\loader
```

From what I think, the last file failed do extract, am I right? How do I fix this?

---

### Post by Juasjero on 2010-11-17
How did you solve it?

---

### Post by emarkay on 2010-12-10
I gave up when I was told it's not possible as of now, but dang it, I didn't save the link or data...  SORRY!

---

### Post by madjr on 2010-12-11
if we're lucky google might get it ported to linux / chromeOS like in this video:

[http://www.youtube.com/watch?v=DKaJ6jEPXGE](http://www.youtube.com/watch?v=DKaJ6jEPXGE)

---

### Post by fanum on 2011-03-05
How did This get marked solved? It is not. There is some potential here:

Go VOTE!:

[http://feedback.unity3d.com/forums/15792-unity/suggestions/164961-platforms-linux-player-web-player-support](http://feedback.unity3d.com/forums/15792-unity/suggestions/164961-platforms-linux-player-web-player-support)

potential solution to get the win one working in chrome:

[http://code.google.com/p/nativeclient/](http://code.google.com/p/nativeclient/)

---

### Post by emarkay on 2011-06-05
I "solved" it because I was told it won't happen, but now, maybe, looks like someone has done it - partially...
[http://feedback.unity3d.com/forums/15792-unity/suggestions/164961-platforms-linux-player-web-player-support](http://feedback.unity3d.com/forums/15792-unity/suggestions/164961-platforms-linux-player-web-player-support)
(same link as above)

"unsolved" until it is working well.

---

### Post by William_Smith on 2011-11-15
I really hope they do make a version for Ubuntu. There is a game I have my eye on, anyone will to send me a message if something happens?

---

