---
title: "apache ant run on startup?"
date: 2006-07-16
forum: Server Platforms
---

### Post by Linus Torvalds on 2006-07-16
How do make an apache ant program run at startup?
usually after I'm already running I cd to the location of the program like this: cd /usr/var/sslexplorer-0.2.4

Then I type "sudo ant run" without quotes to kick it off.
I want to make it run at bootup.

---

### Post by sas on 2006-07-16
You need to make a script with just the lines:
> #!/bin/bash
cd /usr/var/sslexplorer-0.2.4 && ant run

and call it /etc/init.d/antrun, then symlink the script to /etc/rc3.d/S99antrun by running "sudo ln -s /etc/init.d/antrun /etc/rc3.d/S99antrun"

---

### Post by MetalMusicAddict on 2006-07-16
I wouldnt think "Linus Torvalds" would have to ask such questions. :)

---

