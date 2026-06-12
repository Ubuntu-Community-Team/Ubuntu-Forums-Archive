---
title: "Low FPS in Modern Warfare 2 on Wine"
date: 2010-11-02
forum: Wine
---

### Post by korn101 on 2010-11-02
Hi,

I recently installed PlayOnLinux, with Wine.

I Installed steam no problem, and then went on to install Modern Warfare 2.

I can run Modern Warfare 2 fine, it's just a bit laggy. Pretty low FPS.

The Sound is fine.

Does anyone have any tips / ideas as to how I could get my FPS a little higher?

Thanks in Advance

---

### Post by Refalm on 2010-11-02
Disable In-Game Community.

Then, make a shortcut on your desktop with this:
```
rm -f /home/refalm/.wine/drive_c/Steam/GameOverlayRenderer.dll
```

Make sure you change my username to yours, and add "Program Files" if that's where you installed Steam.

Before you start CoD:MW2, just start the shortcut.

---

### Post by cogadh on 2010-11-02
I'm confused. How does making a shortcut that force deletes a DLL file unrelated to the game make the game work better? If you've already disabled the in-game community features, that DLL shouldn't even be used. Additionally, Steam should just automatically re-download it any time you launch it, so it should have no effect whatsoever.

---

### Post by Eternal_Light on 2010-11-02
I don't think wine can handle the high resource demands of cod mw2. I was getting hardly 65-70 fps on win7 with all options set at lowest and with the exact same hardware setup on wine the fps ranged from 50, when nothing happened on the screen, to 5, when i was trying to aim at an opponent, even on the simplest of maps. I think the game is just too heavy for you to try to play it on linux...

Try UrbanTerror instead and savour the long forgotten aroma of those 8bit-colored-box-shapes-everywhere games in it's best. Really fast paced action. It will help you get over mw2 in about a month or so :P Worked for me \\:D/

---

### Post by Refalm on 2010-11-03
> **cogadh said:**
> I'm confused. How does making a shortcut that force deletes a DLL file unrelated to the game make the game work better? If you've already disabled the in-game community features, that DLL shouldn't even be used. Additionally, Steam should just automatically re-download it any time you launch it, so it should have no effect whatsoever.
Even though the In-Game Community is "disabled", it's still loaded on the background. And I noticed it interfered with CoD:MW2 big time. Just try it, works great.

---

### Post by korn101 on 2010-11-03
Or I could just stick to playing Minecraft :guitar:

---

