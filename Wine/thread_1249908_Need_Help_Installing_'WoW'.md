---
title: "Need Help Installing 'WoW'"
date: 2009-08-25
forum: Wine
---

### Post by embiggened.badger on 2009-08-25
Good evening, folks. I need help installing one of my favorite games: 'World of Warcraft.' I installed and configured Wine with the express purpose of running this game.

I'd been following a [Tutorial]("https://help.ubuntu.com/community/WorldofWarcraft") located elsewhere within the vast Ubuntu knowledge base, using the first and most direct method of copying the original install CDs to a directory on the desktop and running the application through Wine. However, I hit a snag with one particular issue:

> *The installer may even hang for up to 5 minutes at 100% CPU, while appearing to be doing nothing. Simply wait and click next when possible.*I followed the instructions provided within that Tutorial to the letter, but once the install got underway, progress got as far as 'Sound.MPQ.' I sat and waited, as the instructions within the Tutorial said, but even after thirty to forty-five minutes, the installation process did not proceed beyond 'Sound.MPQ.' I checked System Monitor while this was running, and it listed 'Installer' as using at least 80% CPU power during the entire lull in the process ...

Was I wrong to halt the installation and try again? It seems awfully strange to me that the install process would hang on a single file for nearly an hour.

What am I doing wrong? Can anyone help me? 'WoW' is a big part of the reason I upgraded my video card earlier today ...

Let me know what additional information you need from me.

**Update:** I tried the direct download route, and the Downloader appears to have performed admirably for the first section of the installation process. At this point, however, I'm still hitting snags - namely, an error message saying **'HTML Rendering is Currently Disabled.'** I've installed IEs4Linux, which I read elsewhere was usually the root of HTML issues for Windows-based installers, but I'm still receiving this message. What am I doing wrong? What am I missing?

**Update:** Just FYI: I tried the Installer (copied from disc) through Wine again. It still appears to hang on 'Sound.MPQ.' Any idea what the issue could possibly be with this file?

---

### Post by pedro_orange on 2009-08-27
If you've already got it installed on Windows; copy the 'Program Files\World of Warcraft' folder to an external hard drive. 
Copy this to your .wine\drive_c\Program Files\ directory.
You can now run the WoW.exe file without needing to install anything. 
Crack open a terminal and do something like:

```
wine '~/.wine/drive_c/Program Files/World of Warcraft/WoW.exe' -opengl
```

---

