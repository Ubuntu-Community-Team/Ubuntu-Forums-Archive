---
title: "Handbrake in Raring?"
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by bird1500 on 2013-03-23
Hi,
according to [this message]("https://lists.ubuntu.com/archives/raring-changes/2013-March/007932.html") handbrake is supposed to be somewhere in the repos, but apt-get install/search doesn't find it.
Anyone knows what's up?

I have all types of updates enabled, "raring-security", "raring-updates", "raring-proposed" and "raring-backports".

---

### Post by mc4man on 2013-03-23
The builds are on a dependency wait for a library, ( libavresample),  that currently doesn't exist in current libav (0.8.5
So as is it won't build until libav9 is available & while there was plenty of time to include libav9 in 13.04 (3 months+), it feels a little late now to do so.
 (- they could but then other sources would have to be re-built, no real clue as to intent here or why a build  was attempted in raring-proposed, doesn't anybody read first...

---

### Post by Gavin77 on 2013-03-23
The last time I used Handbrake from the repos it was heavily crippled, support for h264 and mp4 output were disabled.  The only full version was in the Handbrake Releases PPA.

---

### Post by coldraven on 2013-03-24
This will get you Handbrake
[http://ubuntuforums.org/showthread.php?t=2127803&p=12567215#post12567215](http://ubuntuforums.org/showthread.php?t=2127803&p=12567215#post12567215)

---

### Post by cariboo on 2013-03-24
> **coldraven said:**
> This will get you Handbrake
[http://ubuntuforums.org/showthread.php?t=2127803&p=12567215#post12567215](http://ubuntuforums.org/showthread.php?t=2127803&p=12567215#post12567215)

The instructions in that post are from someone who is trying to stick with the old GTK2 type interface, so the instructions may not work for you. The author of the software has two ppas one for the stable version: 

```
sudo apt-add-repository ppa:stebbins/handbrake-releases
```

and one for the latest version:

```
sudo aprt-add-repository ppa:stebbins/handbrake-snapshots
```

I've been using ver: 5358svn (x86_64), to re-rip my dvds, and haven't had any problems so far.

---

### Post by bird1500 on 2013-03-24
Thanks, the version from the ppa is better (though I had to rename "raring" to "quantal" for it to be detected, since there's no raring version) e.g. the sys tray works.
I found this app to be so easy to get started and so useful and qualitative that I wonder why it hasn't been included in the ubuntu repos before, while having piles of worthless apps in the repos.

---

### Post by stmiller on 2013-03-24
The ppa is maintained by the handbrake upstream developers. It is more or less the best way to go.

---

