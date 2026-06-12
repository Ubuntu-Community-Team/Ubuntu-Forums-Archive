---
title: "Blender (2.71) no longer starts."
date: 2016-03-04
forum: Ubuntu Studio
---

### Post by kraiye2 on 2016-03-04
Hi all,

I'm reasonably new to Ubuntu (running wily studio) and now after running the Software Updater for the first time Blender has stopped working.
I've tried launching it from the menu and double clicking a blender save file but nothing seems to happen
Typing blender in the terminal gives no result and no output - not even an error. The cursor goes to the next line but nothing happens.
ls -al in another terminal doesn't show any blender processes running.

I've uninstalled it and reinstalled it through the software centre with no luck.

Any ideas?

Cheers.

---

### Post by ajgreeny on 2016-03-04
The command ```
ls -al
``` will never show you the processes that are working, it simply lists all the files and folders in the folder where the terminal is opened, ie, your home by default.

You can see if blender is running by using command ```
ps aux | grep blender
``` which will show one or more lines depending on whether or not blender is running.  Here's my output from a similar command looking for firefox which I am using to access the forum so is obviously running.  The first line is for the firefox process itself, the second is not for firefox but for grep which is searching for firefox so don't be confused by that line when you see it
```
ajgreeny   11728  6.4  5.1 1574056 402908 ?      Sl   11:30   0:40 /usr/lib/firefox/firefox
ajgreeny   12954  0.0  0.0  18932   936 pts/0    S+   11:40   0:00 grep --color=auto firefox
```

---

### Post by kraiye2 on 2016-03-05
Oh yeah. That helps. Thanks :)
I've restarted a gradual move away from Windows and my brain doesn't seem to want to remember some of the basics I learnt 10 or so years ago!

---

### Post by Bucky Ball on 2016-03-05
Extremely odd. Something's gone wrong with the update as that should have upgraded your Blender to 2.74 (which is what I have on 15.10 month old install).

I installed 15.10 about a month ago, installed Blender, did an update and didn't see these problems so, though that might not seem to help much, it does give some clues perhaps.

Have you added any PPAs for Blender manually or did you have third-party repos ticked when you installed?

---

### Post by stiv2 on 2016-03-12
As a work-around, you can download a tarball from blender.org  (current is 2.76) and simply untar it in a location of your choice.   Go into the newly created directory (something like blender-2.76b-linux-glibc211-x86_64 )  and do  ./blender  to run it directly.  No need to install anything.

If you want to be clever, you can symlink the blender executable into your $HOME/bin directory.  Being a total Ubuntu Studio noob, I have no idea how to create file associations or launchers.

---

