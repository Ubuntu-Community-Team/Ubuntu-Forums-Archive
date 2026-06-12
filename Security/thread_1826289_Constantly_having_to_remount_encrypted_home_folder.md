---
title: "Constantly having to remount encrypted home folder"
date: 2011-08-16
forum: Security
---

### Post by AJerman on 2011-08-16
Hello all, been a while since I've been here. I'm having an issue with a fresh install of 11.04. Due to work requirements, I encrypted my home folder, which is fine, however, it seems to randomly lock itself down while I'm working, and it's getting really annoying.

Apps stop working, I can't open nautilus (something about not being able to create certain folders because home is locked), hell, even the terminal link on my desktop says failed to launch application (though the launcher on the top panel works). I just have to run ecryptfs-mount-private and enter my password to fix it, but it's doing this every 15 minutes or so.

Anyone have any idea what might cause it to relock itself so frequently? I would expect to not have to deal with mounting my private data, that should happen at login and be good until log out.

---

### Post by AJerman on 2011-08-24
Doesn't look like anyone has much info on this one. To add a little myself, it seems like whenever I use sudo to execute a root command, after it completes my home folder is locked again. Is this intended behavior, or is this something I can fix? I tend to run quite a few root commands and it's quite annoying to have to ecryptfs-mount-private after every one.

---

### Post by Dave_L on 2011-08-24
I found some similar reports:

[https://bugs.launchpad.net/ecryptfs/+bug/691237](https://bugs.launchpad.net/ecryptfs/+bug/691237)
[http://ubuntuforums.org/showthread.php?t=1783761](http://ubuntuforums.org/showthread.php?t=1783761)
[http://forums.gentoo.org/viewtopic-p-6735442.html#6735442](http://forums.gentoo.org/viewtopic-p-6735442.html#6735442)

The third link seems to contain a workaround.

I'm using ecryptfs on Ubuntu 10.04 and haven't encountered the issue.

My guess is that a problem reported in 10.04 (encrypted directory fails to get unmounted on logout) was "fixed" by unmounting a bit too agressively, resulting in the new issue.

---

### Post by AJerman on 2011-08-25
The second and third links don't seem to apply for me using Ubuntu because the files don't really match up. The line they commented out isn't in the file on Ubuntu 11.04.

Thanks for the link on launchpad though. When I originally wrote this topic I hadn't made the correlation with sudo yet, so I didn't find that before. I'll post on there and see if we can get some activity going.

---

