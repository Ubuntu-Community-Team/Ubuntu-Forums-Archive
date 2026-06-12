---
title: "Odd &quot;cpu thrashing&quot;"
date: 2014-06-21
forum: Ubuntu Studio
---

### Post by uudruid74 on 2014-06-21
I have been experiencing a strange issue.   All X apps, including dbus, ibus, my applets, dock, etc, will all use as much CPU as they can.  It starts at random times.  There may or may not be a tendency to do it at higher CPU loads - happens when a program is doing heavy processing, but this could be my imagination.  Killing the gnome-settings-daemon so that no gtk themes are used except for default (which doesn't always display things correctly) seems to stop the bug from triggering.  Its very tough to get a screen-shot since system load sky-rockets and all apps stop responding (I can still drag the mouse from workspace and workspace and my cube rotates).

Using window managers other than compiz and killing cairo-dock doesn't fix the problem.

OK - have a picture of the top output (had to cheat to get this). The application using the most CPU will vary depending on which instant top grabs its snapshot.  All X apps are using all the CPU they can get.   System load goes over 7 on a quad-core machine (1.6Ghz, 8GB of RAM).   The hard drive isn't thrashing or anything.  This will last about 10-15 seconds, and then everything goes back to normal.   How often it hits seems to be random.

This is killing me.  Someone please help!

PS - The screen started to rotate as I grabbed the screenshot.  I didn't even realize it until after I uploaded it.   Its actually a saved version of the top output since I can't save a window while the problem is happening.  If you need a better screenshot let me know or any other details of the set-up.  You can still see all the bold line .. they are all trying to get CPU!

Fixed this.  If anyone else has any weird problems with performance issues, it appears that it could be related to how many fonts are installed.  All those publishing apps ended up loading 1300+ fonts which had my system slow to load things.  I'm not sure why this would periodically trigger a full CPU thrash of all already-loaded apps, but it was doing it.  With fewer fonts, it may be harder to notice.

If you are having latency and Xruns in little spurts, see how many fonts you've got installed!

---

