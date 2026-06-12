---
title: "HOW-TO: Install WMP11 under Wine"
date: 2009-03-11
forum: Wine
---

### Post by falkTX on 2009-03-11
Hi guys,
Recently I found that is possible to install WMP11 (Windows Media Player) and run it. It crashes a lot, and the interface doesn't show properly (may be fixed with some winetricks, but I don't bother).
Anyway, I though I should share this, although I don't care a bit about WMP11.

To install WMP11, you'll need 'cabextract' and the WMP11 installer. Also make sure your wine version is set to XP.

1. Open a terminal and type:
```
cabextract "/location/to/WMP11/installer.exe" -d $HOME/WMP11
```
(Obviously, you'll have to write the real path/location to WMP11 file)

2. Change to the new created dir:
```
cd $HOME/WMP11
```

3. Install WMP11 codecs:
```
wine wmfdist11
```
(You'll have to press Ctrl+C (on terminal) after it finishes installing)

4. Install WMP11 codecs:
```
wine wmp11
```
(Also press Ctrl+C after it finishes)

5. Set Wine version to 2003 and run WMP11 (apps->Wine->Apps->WMP11)
It will pass the genuine check but it will crash. You'll have to kill the process (open the 'System Monitor' and kill setup_wm.exe)

6. Run WMP11 again and click continue.
Now WMP11 starts, although you can barely see it. To fix it click on 'File', press right and select 'Mask Mode'.

There you go. WMP11 is installed and running...
(Can we call it running?? :P LOL)

---

### Post by falkTX on 2009-03-11
An image to prove it

---

### Post by amp_man on 2009-04-16
Here's what my console says when I try to run it on jaunty x86_64:

```
amp@Mobulus:~/WMP11$ wine wmfdist11.exe 
fixme:clusapi:GetNodeClusterState ((null),0x32ec9c,0) stub!
```

screenshot attached.

---

### Post by Steve60938 on 2009-11-03
got this from another website and it worked for me even tho i had already installed wmp11 in wine

If you’ve already installed WM11 go to STEP 2.
 STEP 1: Go to the old windows media player (WM10), go to Tools–>Options and click on ‘Check for updates once a day.’ Press Apply and then OK.
 After a short time a window appears asking if you want to upgrade to a newer version, click OK. System will download WM11 and and install the Media Player 11. After installation restart your PC.


 STEP 2: Click on Start –> Search. Click ‘All files and folders’ then search for LegitLibM.dll. (it’s located in C:\Program Files\Windows Media Player folder.)
 After LegitLibM.dll is found, right click and rename it to legitlib.dll.




 STEP 3: Run WM11, click on validate, it may say ‘unable to validate’ (but that’s a fake message and WMP11 still works, so just click on OK). Then the program will go on to settings or configuration and after you do that the WMP 11 is ready to be used.

---

### Post by cascade9 on 2009-11-03
wow, somebody actually figured out how to run WMP in WINE? I really hope that was just an exercise, WMP was nasty enough under windows......

---

### Post by edin9 on 2009-11-03
What's the point?

---

### Post by Steve60938 on 2009-11-04
I have a whole lot of movies and tv shows that are a whole lot easier to look at in a media library with thumb nails than on the hd in folders, and as a new ubuntu user i cant for the life of me find the open source equivalent of wmp11. However after figuring all that out I wound up just using vmware with a shared folder.

---

### Post by Danefae on 2009-11-05
Hmm, I updating from 10 to 11. But it didn't go well for now. Having installed wmp10 through winetricks, the Options window wouldn't come up. In Help there is also a menu option to check for updates, but that didn't work either (unexpected error). I should probably try to install with the instructions for Media Player 11 in the AppDB.

However, nice to here that you got it working. Does playing WMA work? More so, how about WMA files with DRM? (If you have any of those.) It would be quite awesome to see that kind of functionality!

---

### Post by Godofgrunts on 2010-06-04
GUYS! I got it to work! I can also play DRM'd files!
[ATTACH]159314[/ATTACH]

Here's what I did. I followed the first post to install, I downloaded a "alternated" version of the legit dll (google is your friend).

After installing, set virutal desktop (mine is 800x600). Now, you can't really run WMP from the Applications menu, I had to pick a video, right click and choose WMP to play it. You still won't be able to see it. You have to go into fullscreen mode in order to see it.

:popcorn:

Wouldn't recommend this usually, but CBT Nuggets is an expensive CD and it has the MSS2 DRM built it which I couldn't get to play any way else.

Also, I do own a legal copy of Windows (came with my Dell :( ) so It's all good :guitar:

Also, nothing works. You can't rewind, pause, go forward etc.

---

