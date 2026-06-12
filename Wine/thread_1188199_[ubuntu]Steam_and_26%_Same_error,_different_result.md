---
title: "[ubuntu]Steam and 26%: Same error, different results"
date: 2009-06-15
forum: Wine
---

### Post by Cadeyrn on 2009-06-15
I had the error where Steam crashes at 26% like everybody else, and mine was fixed with the ever-popular command:
```
nice -n 19 wine Steam.exe
```
But it still won't update. Around 36% it always jumps back to 0%, hangs there for a few minutes, and crashes like the 26% glitch. No one else seems to have this problem so it's been hard to find help.

It seems the only fix I haven't tried is ```
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```.

But I can't try it because there is no damn SteamTmp.exe. I've tried every directory inside of .wine, ran a Nautilus search, and searched myself, but WINE always tells me that file is not in that directory because it's not in any directory. I don't know where this SteamTmp.exe file came from or where to download it, and I don't know why other people have it because I've never heard about it till now. Even when I was a Windows user my copy of Steam had no "SteamTmp.exe".

EDIT: Hooray! For others missing SteamTmp.exe, just type in the same thing but substitute it with Steam.exe, that is, do this:
```
wine "C:\Program Files\Steam\Steam.exe" SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
Eventually the update window will close with the same Sharing error older versions of WINE got while installing Steam, but it will continue to update in the background, and when it's done, the login window shows up and Steam works again.

---

