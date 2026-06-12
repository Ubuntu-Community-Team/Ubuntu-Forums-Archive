---
title: "Changing up homdir"
date: 2014-10-30
forum: System76 Support
---

### Post by Replicon on 2014-10-30
Hi guys,

I just setup my new Wild Dog, and everything is working great.

I got two drives in it (one for OS and apps, and one for home dir and data), but right now, the second drive is setup as just an extra drive, and /home also just lives on the main drive.

What is your recommended, least-intrusive way to change this up?

Option 1: Change mounts so the extra drive mounts as /home
Option 2: Create a home dir in extra drive, and update whatever sets up $HOME
Option 3: Keep everything as-is, and find a better way to use the drive hehe.
Option 4: Just move everything over, and symlink /home/username to (real home dir in other drive)
Option 5: usermod seems to be able to just do it on the command line...

Would any of these mess up any "special" setup done by the sys76 folks?


Thanks!

---

### Post by Replicon on 2014-10-30
I'm actually leaning towards option 1, looking at directions at:

[http://www.maketecheasier.com/move-home-folder-ubuntu/](http://www.maketecheasier.com/move-home-folder-ubuntu/)

What I don't get, however, is how come the extra drive is not showing up in fstab already? What's causing it to be mounted where it's mounted? Is it being treated as if it were just an external drive? Will copying homedir to it and attempting to mount it as /home in fstab break things?

---

