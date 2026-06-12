---
title: "Just another &quot;Can't sync&quot; post"
date: 2010-06-14
forum: Ubuntu One (CLOSED)
---

### Post by PaulHuffman on 2010-06-14
I installed U. One a week and a half ago, but haven't seen it do much yet. Running 10.04.  When I first installed it, I set a directory to sync, but in My Storage I only got a partial list of subdirectories, and a "0 bytes used" indicator.  Stayed at 0 % ever since.

u1sdtool -s today reported is_connected: false. I went to Ubuntu One Preferences, hit connect, now u1sdtool -s reports:
Oops, an error ocurred:
Traceback (most recent call last):
Failure: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Now My storage doesn't even show any subdirectories.  Tried adding a small subdirectory to sync for a test, but haven't seen anything. 

What did I miss?

---

### Post by qianian on 2010-09-30
Did this ever resolve, Paul? I'm having a similar problem. I had to remove and reconnect my computer to U1 before it showed on the daemon but after two days, still 0%.

---

### Post by PaulHuffman on 2010-10-20
No, doesn't seem to work as advertised.

---

