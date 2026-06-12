---
title: "Periodic slowdown, is this normal?"
date: 2008-03-12
forum: The Cafe
---

### Post by Rhapsody on 2008-03-12
I'm not posting this in a support problem, because it's not really a problem as such. It's just something an application does, and I want to know if anyone else is getting it.

I'm in the middle of using my PC, browsing, listening to music, or maybe watching a video file, then everything slows to the point of almost stopping. Music skips, video stutters, even mouse movement and the clock applet stop working smoothly. What could be going on? Simple, [Akregator](http://akregator.kde.org/) is updating my feeds.

Admittedly, I have a lot of feeds (48, at my last count), but this isn't like my system slows down a bit. It damn nearly stops entirely, for as much as 30 seconds! This happens several times a day and is getting to be ridiculous. I've looked for options like lowering the priority, limiting the number of feeds it will try to update at one time, or even just lowering the update frequency, but there's nothing of the sort. It's either update periodically at some unknown interval, or not automatic updates at all.

So, does anyone else using Akregator get anything this severe? Does anyone have suggestions for another good aggregator that may consume less resources? I ask for help so I can make more actual use of my PC.

---

### Post by Radon on 2008-03-12
Hi!  I'm subscribed to more than a hundred feeds in Akregator, and I update them manually once a day.  I think your slowdowns are due to inadequate amount of RAM and is hitting the HDD's swap space too much.

You can disable automatic updating as follows: Settings > Configure Akreagtor > General  and unclick "Use interval fetching".  You can press Ctrl + L or the corresponding icon at the top to update manually.

To make a backup of your feeds go to /home/your_profile/.kde/share/apps and compress the akregator folder (tar reduces the file size by 3/4)

/Akregator is telling me I've got 46273 unread RSS feeds #-o :)

---

