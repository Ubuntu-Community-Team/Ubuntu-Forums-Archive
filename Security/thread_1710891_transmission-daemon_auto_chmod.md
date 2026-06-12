---
title: "transmission-daemon auto chmod"
date: 2011-03-20
forum: Security
---

### Post by fela on 2011-03-20
I have transmission-daemon configured to download to a directory, TORRENTS, inside another directory, torrents (case sensitive of course ;)). TORRENTS is actually a symlink to a folder called torrents on another hard drive, but I don't think that's relevant.

The problem is that whenever the daemon is started, after a certain length of time I find that everything in the torrents folders (and the folders themselves) are chmodded 777 (world-writable) - obviously, a situation I would rather avoid.

The umask in transmission-daemon's settings.json file is on 23. I heard it uses decimal notation (as opposed to octal), so I converted 027(oct) [rwxr-x---] to 23(dec). Maybe something's wrong there?

Cheers, Fela

---

### Post by fela on 2011-03-20
Don't worry. As a lazy admin, I forgot I had a cron job setting the perms to 777 every 5 minutes...my bad! :D

---

