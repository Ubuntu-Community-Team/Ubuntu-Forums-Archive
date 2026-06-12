---
title: "Fixing WoW's backround downloader"
date: 2009-11-10
forum: Wine
---

### Post by Clydtsdk-Rivendare on 2009-11-10
For those who aren't aware of the situation, something happened at Blizzard that requires a small WoW patch -- however, this patch has no real name nor appears in any patch mirror sites I know about (ie. Wowwiki). Unless I can get my background downloader to work, I'm stuck.

When running wow.exe: Trying to log in brings up the "Patch Required" screen, then upon hitting "Restart" instead of bringing up the downloader, I go back to the login screen immediately with a "Failed to apply patch" error.

When running backgrounddownloader.exe: Appears to do nothing. After some time passes a "No data for the next patch is available" message appears.

When running backgrounddownloader.exe in the terminal:

```
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000

http error code = 404
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000

```And for reference read the following: 
[http://www.wow.com/2009/11/09/wow-launcher-and-downloader-causing-validation-errors/](http://www.wow.com/2009/11/09/wow-launcher-and-downloader-causing-validation-errors/)
The fixes mentioned in the article are all windows-specific and appear to be "We don't know what's going on, try this" type of stuff.

It would be REALLY AWESOME if I could get this nameless patch downloaded, either through a mirror I don't know about or by finally fixing that stupid downloader. I figured you guys would be the best to ask. Thanks a ton.

---

### Post by joeelmex on 2009-11-10
I had something funcky happen to mine, after the patch yesterday, the game would not load at all.  After testing i found out that the World of Warcraft directory where I have the game installed, was restricted to all users.  I tdid the chmod -R 777 path to the game.  Then tried wow.exe and the game loaded fine.  For grins I then tried the launcher again and it restricted access to the wow directory.  So the update from last night did some changes.  So thats what I did to play last night.

---

### Post by Clydtsdk-Rivendare on 2009-11-10
> **joeelmex said:**
> I had something funcky happen to mine, after the patch yesterday, the game would not load at all.  After testing i found out that the World of Warcraft directory where I have the game installed, was restricted to all users.  I tdid the chmod -R 777 path to the game.  Then tried wow.exe and the game loaded fine.  For grins I then tried the launcher again and it restricted access to the wow directory.  So the update from last night did some changes.  So thats what I did to play last night.

Did you actually get the patch or not? I'll look into this even though I haven't used the launcher except once to see if it would make wow work correctly after the bug occured.

---

### Post by joeelmex on 2009-11-10
Yeah I am pretty sure I did get the patch, but when I loaded WoW, it updated itself in the characther selection screen again and then closed.

---

### Post by Clydtsdk-Rivendare on 2009-11-12
> **joeelmex said:**
> Yeah I am pretty sure I did get the patch, but when I loaded WoW, it updated itself in the characther selection screen again and then closed.

See, that's my problem though, I can't get the patch. And apparently there's been a second... ugh.

---

### Post by titaniferous on 2009-11-12
I had exactly this problem on Jaunty and *seem* to have diagnosed it. For some reason WoW updates keep fiddling with folder permissions in ~/.wine/drive_c/Program_Files/World_of_Warcraft/. Repeated 'chmod 777' commands seem to solve it long enough to play, but it reverts the next time. Would love a more permanent fix...

---

### Post by Clydtsdk-Rivendare on 2009-11-14
> **titaniferous said:**
> I had exactly this problem on Jaunty and *seem* to have diagnosed it. For some reason WoW updates keep fiddling with folder permissions in ~/.wine/drive_c/Program_Files/World_of_Warcraft/. Repeated 'chmod 777' commands seem to solve it long enough to play, but it reverts the next time. Would love a more permanent fix...

Looked into this--it doesn't seem to be the issue.

---

