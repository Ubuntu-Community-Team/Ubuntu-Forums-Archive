---
title: "Restoring notify-osd notifications."
date: 2010-08-09
forum: Ubuntu One (CLOSED)
---

### Post by gvoima on 2010-08-09
I very much like ubuntu one and the fact that Lucid got rid of the notification area icon. And that they added emblems to recognize current synchronization process, this is great if you happen to use nautilus at the moment.

But, I miss the notify-osd notifications "syncing", "syncing complete" etc.
They were are a kind of "you have new items in synced folder" -reminder for me, as me and my friends share a common folder to sync items.

Is there a way to restore these osd notifications? From e.g. gconf-editor or others like?

---

### Post by duanedesign on 2010-08-13
This is a python script that gives you notifications when the syncdaemon changes Status. It reports what you see when you run the command u1sdtool -s. Not exactly what you are wanting but it is a start. With a little work you could have something very close to the old notifications. 

If anyone does hack on it please post your work. :)

[Here is the script]("http://people.ubuntu.com/~duanedesign/U1/notifySync.py")

---

### Post by gvoima on 2010-08-14
Thanks, this helps. :)


[edit]
Actually there's no more need for this and I can manage without any notifications. So I'll mark this as solved, though there was no solution.
[/edit]

---

