---
title: "Ubuntu security issues"
date: 2012-04-28
forum: Security
---

### Post by whiskers751 on 2012-04-28
I tried to use curlftpfs after installing it. It said I needed a mount point, so I created a folder and called it LiveCD because of what I was doing with it. So, I tried to mount it and got a permission denied error. I then deleted the folder, but couldn't, due to a large number of random, protected files! How did those get there? I have SSH and VNC enabled, my user is part of the 'src' group, and I am running Ubuntu 10.10
And I did all this under TTY1.
What do I do?

---

### Post by wacky_sung on 2012-04-28
[Ubuntu 10.10 (Maverick Meerkat) end-of-life reached on April 10, 2012]("http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/")

Time for you to update to latest version.

---

### Post by Dangertux on 2012-04-28
Turn off VNC for one thing, if it hasn't gotten you owned yet it will soon.

That being said curlftpfs mounts a remote filesystem. WHich is exactly what those files are, you don't have permission to delete them so you need to unmount the filesystem.

You in all likelyhood did put them there you just didn't realize it.

Hope this helps.

---

### Post by whiskers751 on 2012-04-28
Thanks a lot - just had a moment of brief panic! I will turn VNC off, as you said (I don't actually need it -SSH is fine) I guess, thread solved.

---

