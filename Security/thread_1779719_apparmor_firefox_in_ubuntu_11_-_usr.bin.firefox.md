---
title: "apparmor firefox in ubuntu 11 - usr.bin.firefox"
date: 2011-06-10
forum: Security
---

### Post by toolmania1 on 2011-06-10
I followed this post ( most of it anyways ).

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

I do have usr.bin.firefox in apparmor.d.  Is this my Firefox profile.  In that post above, there was a little different path.  I am just guessing that it was because that was from an older Ubuntu version.  Is this correct?

---

### Post by toolmania1 on 2011-07-09
bump

---

### Post by Dave_L on 2011-07-09
You're probably correct.

This shows you which profiles are in use:

```
sudo service apparmor status
```

You can also try to make firefox do something that its profile disallows, and see if the action is blocked.  For example, create a subdirectory in /opt that's owned by your user, and then File >> Save Page As... into that subdirectory. The action should be blocked, and a "denied" message should appear in the log file(s).

---

