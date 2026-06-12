---
title: "AutoFS - UID/GID dependent?"
date: 2013-04-02
forum: Server Platforms
---

### Post by Roasted on 2013-04-02
A buddy of mine was telling me how he prefers AutoFS to GVFS. I opted to give it a shot, but I'm not sure I understand how AutoFS actually works. I'm seeing some inconsistencies where it works in some situations but not others. I'm testing multiple user accounts which makes me wonder if AutoFS introduces an NFS style of usability where it needs to have identical UID and GID's from the server-to-client in order to successfully work. Am I correct in that understanding? Or did I do something else to cause these inconsistencies that I need to do some troubleshooting on?

Thanks!

---

### Post by Roasted on 2013-05-04
I revisited this issue after my buddy recommended that I put the GID and UID entries in the mount line. So now my /etc/auto.user.server file reads as such:

storage -fstype=cifs,rw,credentials=/etc/auto.jason.server.auth,soft,uid=1000,gid=1000 ://192.168.1.20/storage

Seems to work pretty nicely. Auto mounts on demand whenever needed and times out in 30 seconds of inactivity due to the --timeout=30 entry I have in auto.master. It's worked around all of my GVFS frustrations and issues (such as not being able to stream videos with VLC over GVFS properly as notated in this bug report I just [posted here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1176379"))

At any rate, things seem good to go thanks to AutoFS. :guitar:

---

