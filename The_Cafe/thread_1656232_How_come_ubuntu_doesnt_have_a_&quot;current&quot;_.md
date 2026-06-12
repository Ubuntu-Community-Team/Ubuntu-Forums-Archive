---
title: "How come ubuntu doesnt have a &quot;current&quot; folder on the download server?"
date: 2010-12-30
forum: The Cafe
---

### Post by markp1989 on 2010-12-30
I was gonna add an entry to flexget to auto download the latest ubuntu as it is released , i tested it with Debian and it works.

Debian folder layout:
 [http://cdimage.debian.org/debian-cd/current/i386/bt-dvd](http://cdimage.debian.org/debian-cd/current/i386/bt-dvd)  so i can add the "current" folder, and it will download the newest torrent file when they are added. 

Ubuntu mirrors folder layout:
[http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)  so in order to have flexget auto download the torrent for the next version, i will need to know what its called, and add an entry for every ubuntu version in the flexget config.

does any one know of any ubuntu mirrors that just have a "current" folder which always has the latest release in it?

Thanks for reading, Mark

---

### Post by stmiller on 2010-12-30
Ubuntu only does that for the development release in progress:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by cariboo on 2010-12-30
I use zsync to update the daily live images during the testing cycle, it saves having to download the full iso every time I need one. For a  howto, have a look [here]("https://help.ubuntu.com/community/ZsyncCdImage").

Once an Ubuntu version is released, except for LTS point releases, the images aren't updated.

---

