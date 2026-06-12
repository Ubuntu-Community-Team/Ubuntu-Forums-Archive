---
title: "dell sever with ssh poblems"
date: 2008-11-09
forum: Server Platforms
---

### Post by bobyo134 on 2008-11-09
i have a dell sever that runs debian 4 and i have just reformated it, when i did so i changend the id tag so when i try to access ssh it says this "@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
f1:9c:dc:3a:59:07:ad:54:7c:56:bc:cc:95:48:f8:5c.
Please contact your system administrator.
Add correct host key in /home/bob/.ssh/known_hosts to get rid of this message.
Offending key in /home/bob/.ssh/known_hosts:1
RSA host key for 192.168.1.18 has changed and you have requested strict checking" my freind told me to completly install ssh again and i did but same problem so what do i do i need some help ppl thx.

---

### Post by chrisamiller on 2008-11-09
This line is what you need to be paying attention to:

Offending key in /home/bob/.ssh/known_hosts:1

Since the computer you're sshing to no longer matches what you had on file, SSH raises a warning.  If this happened normally, it could be indicative of someone else hijacking your connection so that you weren't sending your credentials to the place that you thought you were.

In this case, though, you know why the remote host's ID has changed - it's because you did a reformat/reinstall, etc.  What you'll need to do is open up your "/home/bob/ssh/known_hosts" file in your favorite text editor, and simply remove line 1.   Save the file, and when you ssh to your remote host this time, it'll ask you if you're sure you trust the computer on the other end.  Type yes, and you'll be back in business.

---

