---
title: "Ubuntu confessions"
date: 2007-04-17
forum: The Cafe
---

### Post by jfinkels on 2007-04-17
I made myself a script that runs "sudo aptitude update && sudo aptitude update" named "up" so that I would only have to type two letters.

I count down the months and days until the next official release date.

I spend more time on the forums than I spend on my homework.

Anyone else?

---

### Post by bwhite82 on 2007-04-17
I know what you mean, while Ubuntu as an OS is absolutely fantastic, what really shines through is the community that drives it. You simply cannot find a larger, friendlier community than Ubuntu's. You can log on and discuss politics in the Backyard then switch over to Absolute Beginners and help someone out. After that, you can login to IRC and happily chat away.

My confession is that I am constantly trying to drum-up support and a larger user-base for Ubuntu. I submit articles on Digg and chat up folks on forums of other distros to change over to Ubuntu. :D

---

### Post by 3rdalbum on 2007-04-17
> **jfinkels said:**
> I made myself a script that runs "sudo aptitude update && sudo aptitude update" named "up" so that I would only have to type two letters.

I admire your enthusiasm, but if you keep hitting the repositories like this, it will slow down the process of synchronising the mirrors and also make other people's software requests slower.

Rather than that, why not do:

```
sudo watch -n 900 -d "aptitude update"
```

That will automatically check every 15 minutes, and highlight any differences between the last time the command was run.

---

