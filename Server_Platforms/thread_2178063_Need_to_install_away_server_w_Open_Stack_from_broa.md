---
title: "Need to install away server w/ Open Stack from broadband - but how?"
date: 2013-10-01
forum: Server Platforms
---

### Post by K7AAY on 2013-10-01
Here is what I believe to be an unusual question.

I've always installed Ubuntu desktop (many versions and flavors) with a decent internet connection, but now I find myself preparing for my first-ever server (13.04) installation, in a place without broadband. I therefore wish to prepare for installing everything from media, which I would download before I wander off to the Boonies. 

How can I download all the files I would need for a complete Open Stack install, onto movable media, before I leave the blue blanket of my broadband connection?

Once downloaded and a basic install performed, would I install additional packages needed by apt after revising /etc/apt/sources.lst to point to where the Big Pile o' Files be, or would I manually install each with dpkg, or, on the Gripping Hand, do it in a way I do not yet recognize?

Thank you kindly.

---

### Post by houstonbofh on 2013-10-01
Best thing is to set up a local mirror and bring it.  There are several paths to take, but they all lead the same place.  Eventually, you will have a USB hard drive with all the repos.

[https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror)
[https://help.ubuntu.com/community/Rsyncmirror](https://help.ubuntu.com/community/Rsyncmirror)
[http://ubuntuforums.org/showthread.php?t=1512787](http://ubuntuforums.org/showthread.php?t=1512787)

---

### Post by K7AAY on 2013-10-02
Thank you, Bob Oscar Francis Howard. Hook 'em, horns!

---

