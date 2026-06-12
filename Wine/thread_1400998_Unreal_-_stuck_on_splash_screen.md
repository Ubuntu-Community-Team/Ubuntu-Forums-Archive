---
title: "Unreal - stuck on splash screen"
date: 2010-02-07
forum: Wine
---

### Post by LutraMan on 2010-02-07
I've installed unreal using wine, when I try to run it, it get stuck on the splash screen.

I've already tried to solve it for weeks, but now I have a new theory about what could get it fixed but I don't know how to execute it.

I've installed the game using an ISO image because I can't find the DVD. Recently, I've installed Starcraft Broodwar the same way but it didn't work until I placed the cd in the drive. I think wine couldn't identify the mounted image, and it was looking for a file there and got stuck (or it could find the mount, but had a problem extracting the file it needed). I think that whats happening with Unreal too, because I tried anything else I, and some help from the WineHQ forum could possibly think of.

Now I can't burn the ISO to a DVD because it's 6GB. Do you know of anyway I can vitalize an actual DVD drive (like daemon tools for windows?)

Until now I've used the following command to mount, but I guess it's not good enough:
```
sudo mount "/storage/Image Files/Games/Unreal.Tournament.3-AVENGEDd/avd-ut3.iso" /media/UT3 -o loop

```

I'm using Karmic. My Wine version is: 1.1.38

---

### Post by Soulcage on 2010-02-08
You could try this page [https://help.ubuntu.com/community/MountIso]("https://help.ubuntu.com/community/MountIso").
Make sure after you mount that you cd to the location then use wine setup.exe just incase. Sometimes if you don't then the installer won't work which could be your problem.

---

