---
title: "Downloading World of Warcraft problems"
date: 2009-01-19
forum: Wine
---

### Post by msimmons on 2009-01-19
I'm following the guide [here]("https://help.ubuntu.com/community/WorldofWarcraft") to install WoW on my ubuntu 8.10 install, and I'm having issues with the downloader. (I'm using the last listed method, download the entire game)

I have the installer from blizzard (InstallWoW.exe for the current version of WoW) but when I run it (with wine InstallWoW.exe) I get an error "Failed to read information from the internet. Please close all applications and try again"

I've already followed the instructions for opening the necessary ports, and I'm currently not using my router, so I'm at a loss.

Nothing else is installed with wine.
OS version windows XP, pretty much all of winecfg is whatever is default.

Wine version 1.1.13

```
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:shdocvw:PersistStreamInit_Load (0x133a60)->(0x32ea74)
fixme:shdocvw:OleControl_FreezeEvents (0x133a60)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x133a60)->(0)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
fixme:shdocvw:WebBrowser_Stop (0x133a60)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x133a60)
fixme:shdocvw:OleObject_Close (0x133a60)->(1)
```

Any help is much appreciated

---

### Post by efjen on 2009-01-20
I'm having the same problem. I've used World of Warcraft on this very system before, and the downloader worked back then. This was sometime before christmas; either the downloader or Wine must have changed since then.

Wine version 1.1.13.

Any help would be greatly appreciated!

---

### Post by EnderEcho on 2009-01-20
Its kind of obvious and I hope I'm not being redundant, but reverting to an old WINE version might be best for the install. The game runs fine in 1.1.3. Since it just came out it may be a little while before this is resolved. So if you are in a rush to get it installed give that a shot and let us know if that worked!

---

### Post by msimmons on 2009-01-20
That's actually exactly what I was going to try (well, I was going to download it, and then install with the new version of wow), but I'm new to using linux as an OS.. so not entirely sure how to do that. I'll find out soon enough.

I'm running 64bit ubuntu, so I downloaded the binaries for 1.1.10 (still a bit uncomfortable with compiling my own, 1.1.3 does not exist for 8.10 intrepid... in wine archives anyway).

It's currently downloading and installing. Make sure you run winecfg first, naturally.

---

### Post by EnderEcho on 2009-01-20
I meant version 1.1.13. Sorry

---

### Post by msimmons on 2009-01-20
Ok, I downloaded and installed it, but now I'm having an issue with gameplay... well sort of
(I downloaded and installed with 1.1.10 for anyone who happens to google this)

I switched back to version 1.1.13 and it runs perfectly without any modifications. I started it up, it goes through the opening, I typed in the login, etc etc. play a character, set up my video settings how I'd like, and exit.

when I go back in, the settings have been completely reset to default.

Any ideas?


Edit:
Alrighty... I played with the WTF and Interface folders (deleted and replaced and restored etc) and after restoring the original one time it worked. /shrug
Not sure exactly what I did.

---

### Post by efjen on 2009-01-21
> **EnderEcho said:**
> Its kind of obvious and I hope I'm not being redundant, but reverting to an old WINE version might be best for the install. The game runs fine in 1.1.3. Since it just came out it may be a little while before this is resolved. So if you are in a rush to get it installed give that a shot and let us know if that worked!

Thank you. It was a bit stupid of me not to try an older version of Wine. I downgraded to 1.0.1 from the Ubuntu repos, and now it works. The only problem was that I could not click Agree on the WoW EULA, but I hacked my way past that by deleting EULA.htm. I deleted the whole ~/.wine folder after the downgrade.

---

### Post by roh8880 on 2009-06-02
I have a bit of a different problem. Up untill today, my WoW was working perfectly, then I login and I get the normal "Patch Needed click restart" then the downloader opens. But that is where it stops doing things. After about 5 minutes of not doing things, the green light turns yellow and says "tracker is not responding". 

I am totally lost on this one. I did allot of reading, i've searched the threads, am I just not seeing the answer?

---

